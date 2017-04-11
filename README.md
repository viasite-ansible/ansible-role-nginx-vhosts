# Ansible Role: Nginx vhosts
[![Build Status](https://travis-ci.org/viasite-ansible/ansible-role-nginx-vhosts.svg?branch=master)](https://travis-ci.org/viasite-ansible/ansible-role-nginx-vhosts)


## Purpose

I am using this role as part of [viasite-ansible.site](https://github.com/viasite-ansible/ansible-role-site)
for speedup site provision.

This is stripped version of [jdauphant.nginx](https://github.com/jdauphant/ansible-role-nginx).
You must provision jdauphant.nginx to host before using this role. 

On my machine provision of one site decreased from 48 seconds (with `--skip-tags package`) to 7 seconds.


## Features
- add sites
- remove sites

Other features implemented in full jdauphant.nginx role.


## Usage
See [jdauphant's docs](https://github.com/jdauphant/ansible-role-nginx).


## Example Playbook

```yaml
- hosts: all
  roles:
    - viasite-ansible.nginx-vhosts
  vars:
    nginx_sites:
      foo:
        template: "site.conf.j2"
      bar:
        - listen 8080
        - server_name localhost
        - root "/tmp/site1"
        - location / { try_files $uri $uri/ /index.html; }
        - location /images/ { try_files $uri $uri/ /index.html; }
    nginx_remove_sites:
      - baz
```

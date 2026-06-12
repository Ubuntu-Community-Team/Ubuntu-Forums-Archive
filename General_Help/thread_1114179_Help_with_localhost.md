---
title: "Help with localhost"
date: 2009-04-02
forum: General Help
---

### Post by mdgrech on 2009-04-02
I have LAMP setup, right now I have to access my files thru var/www and dealing with permissions is a pain.  

I would like to create a dir in my hold folder called public_html where the docs are synced with the contents of var/www and I have no permissions issues

---

### Post by DGortze380 on 2009-04-02
> **mdgrech said:**
> I have LAMP setup, right now I have to access my files thru var/www and dealing with permissions is a pain.  

I would like to create a dir in my hold folder called public_html where the docs are synced with the contents of var/www and I have no permissions issues

You could do this with a little script, here's some pseudo code to start you off.

#!/bin/bash
# Run as Root

# Sync /var/www with /home/<username>/public_html
rsync -ax -delete /var/www /home/<username>/public_html

# Change permissions
chmod -r 777 /home/<username>/public_html

---

### Post by mdgrech on 2009-04-02
Alright found the answer here under virtual hosts:  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

This solution is sweet cause you can easily access and everything right from your home dir

I'll throw out some keywords for others:

Can't access localhost
Can't edit var/www
symlink var/www to home

---


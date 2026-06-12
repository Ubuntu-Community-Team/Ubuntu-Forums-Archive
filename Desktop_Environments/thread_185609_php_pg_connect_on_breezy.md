---
title: "php pg_connect on breezy"
date: 2006-06-01
forum: Desktop Environments
---

### Post by taniwhaiti on 2006-06-01
i have apache1.3, php4 and postgresql 8.0 on a development machine, running ubuntu breezy

i can't get pg_connect() working

i have installed php4-pgsql from apt-get
i've restarted apache.

calls to pg_connect result in:
Fatal error: Call to undefined function: pg_connect() in /var/www/includes/database.pgsql.inc on line 24

so, what do i need to add to provide pg_connect in php4 on breezy?

---

### Post by chriscando on 2006-06-01
Maybe just make sure that you have postgres started
sudo /etc/init.d/postgresql-8.0

---


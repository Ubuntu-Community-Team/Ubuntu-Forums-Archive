---
title: "Problems install MySQL 5 on Hardy"
date: 2009-01-09
forum: General Help
---

### Post by pan69 on 2009-01-09
Hi when I run the following command to install MySQL 5 on my Hardy server:

```
sudo apt-get install mysql-server mysql-client libmysqlclient15-dev
```

I get the following error during installation (after the root password dialogs):

```

Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libmysqlclient15off (5.0.51a-3ubuntu5.4) ...

Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.4) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up zlib1g-dev (1:1.2.3.3.dfsg-7ubuntu1) ...
Setting up libmysqlclient15-dev (5.0.51a-3ubuntu5.4) ...

Setting up mysql-client (5.0.51a-3ubuntu5.4) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help very much appreciated.

- Luke

---


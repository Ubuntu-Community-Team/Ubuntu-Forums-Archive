---
title: "MYSQL problems"
date: 2007-08-01
forum: Desktop Environments
---

### Post by Puck7 on 2007-08-01
Hi everyone!
I have looked at the other threads and nothing seems to be the same as my problem.

Here is the deal. Whenever i try to update or install smth from Synaptic Package Manager i get this error :

>  * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does anyone have a suggestion about how can this be fixed ?

---


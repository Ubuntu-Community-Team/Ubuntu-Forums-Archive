---
title: "Insecure directory in $ENV{PATH} while running with -T switch"
date: 2006-06-09
forum: Desktop Environments
---

### Post by element on 2006-06-09
I just noticed this when trying to remove and reinstall PostgreSQL. Any ideas how to resolve this?
Thanks!

```

XXXXXX@XXXXXX:~$ sudo apt-get remove postgresql-8.1
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  postgresql-8.1
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 12.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110432 files and directories currently installed.)
Removing postgresql-8.1 ...
 * Stopping PostgreSQL 8.1 database server  * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 342.
Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 350.
(does not shutdown gracefully, now stopping immediately)
                                                                                                       [fail]
invoke-rc.d: initscript postgresql-8.1, action "stop" failed.
dpkg: error processing postgresql-8.1 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting PostgreSQL 8.1 database server  * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 52.
                                                                                                       [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Anus+ on 2007-11-13
Hi element!

The problem is rather old but i think I have the solution to this problem and maybe this will help somebody having the same issue with postgres - because I had it a few days ago. Ok, here we go:

At first kill all postgresql processes remaining (e.g. by using the *kill* command. Now follow these instructions:

```

# sudo rm /var/lib/postgresql/8.2/main/postmaster.pid
# sudo chown postgres:postgres /etc/postgresql/8.2/main/environment
# sudo chmod u+rw,g+rw /etc/postgresql/8.2/main/environment

```

I think the trick is to remove the *postmaster.pid* file. Now uninstall all postgresql packages using *aptitude* and afterwards purge all the configuration files and manually delete the postgres directories in */etc/*, */var/lib/* and */usr/share/* and all it's contents.

Now execute the following two commands to update the package sources...
```

# sudo aptitude update
# sudo aptitude upgrade

```

The next step will be to re-install postgres and its dependencies using *aptitude*.

Afterwards postgresql should start up as usual and everything's fine. The problem is if you try to shutdown postgres using the *init.d*-script, it won't succeed. I haven't found a solution, yet. Beside of killing the postgresql processes manually...


Regards, Anus+

---


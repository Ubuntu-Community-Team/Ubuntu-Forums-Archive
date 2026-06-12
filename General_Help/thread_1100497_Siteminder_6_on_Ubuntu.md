---
title: "Siteminder 6 on Ubuntu"
date: 2009-03-19
forum: General Help
---

### Post by csdozier on 2009-03-19
Officially Siteminder is only supported via Suse/Redhat. I am trying to get it to work on Ubuntu. It is installed, but I can not get it to load with apache, I get the following error:


root@xxxxx:/etc/apache2# /etc/init.d/apache2 restart
 * Restarting web server apache2
/etc/apache2/envvars: 9: NETE_WA_ROOT: not found
/etc/apache2/envvars: 10: NETE_WA_PATH: not found
/etc/apache2/envvars: 9: NETE_WA_ROOT: not found
/etc/apache2/envvars: 10: NETE_WA_PATH: not found
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Cannot load /root/netegrity/webagent/bin/libmod_sm20.so into server: libsmerrlog.so: cannot open shared object file: No such file or directory
   ...fail!

More info:
-------------
root@testwiki:/etc/apache2# more envvars 
# envvars - default environment variables for apache2ctl

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid
NETE_WA_ROOT = /root/netegrity/webagent
NETE_WA_PATH = /root/netegrity/webagent/bin
PATH=/root/netegrity/webagent/bin:$PATH

root@testwiki:/etc/apache2# more httpd.conf
LoadModule sm_module "/root/netegrity/webagent/bin/libmod_sm20.so"
SmInitFile "/etc/apache2/WebAgent.conf"


Alias /siteminderagent/pwcgi/ "/root/netegrity/webagent/pw/>"
<Directory "/export/webagent/pw/">
Options Indexes MultiViews ExecCGI
AllowOverride None
Order allow,deny
Allow from all
</Directory>

root@testwiki:/etc/apache2# 


Anybody familiar with siteminder gotten this to work or know what I am doing wrong. The config wizard didnt totally complete so I think that is part of the problem.

---

### Post by csdozier on 2009-03-19
I added LD_LIBRARY_PATH=/root/netegrity/webagent/bin too, still same error

---

### Post by csdozier on 2009-03-19
Ok I have made it past that error, now a new error:

root@xxxx:~/netegrity/webagent/bin# /etc/init.d/apache2 restart
 * Restarting web server apache2
/etc/apache2/envvars: 9: NETE_WA_ROOT: not found
/etc/apache2/envvars: 10: NETE_WA_PATH: not found
/etc/apache2/envvars: 9: NETE_WA_ROOT: not found
/etc/apache2/envvars: 10: NETE_WA_PATH: not found
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Cannot load /root/netegrity/webagent/bin/libmod_sm20.so into server: /root/netegrity/webagent/bin/libmod_sm20.so: undefined symbol: __dynamic_cast_2
   ...fail!

---

### Post by rathnid on 2009-05-01
Was wondering what steps you took that brought you to the new error level? I'm dealing with the exact same problem.

---

### Post by jpalko on 2009-06-30
> **csdozier said:**
> Ok I have made it past that error, now a new error:

root@xxxx:~/netegrity/webagent/bin# /etc/init.d/apache2 restart
 * Restarting web server apache2
/etc/apache2/envvars: 9: NETE_WA_ROOT: not found
/etc/apache2/envvars: 10: NETE_WA_PATH: not found
/etc/apache2/envvars: 9: NETE_WA_ROOT: not found
/etc/apache2/envvars: 10: NETE_WA_PATH: not found
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Cannot load /root/netegrity/webagent/bin/libmod_sm20.so into server: /root/netegrity/webagent/bin/libmod_sm20.so: undefined symbol: __dynamic_cast_2
   ...fail!

I think you're trying to use the wrong module version, try the libmod_sm22.so.

But what did you do to get rid of the earlier problem? Can't seem to figure that out myself now. :) 

Or actually I do have one solution, but I was wondering if I could do this without making a ld.so.conf.d file for siteminder.

---


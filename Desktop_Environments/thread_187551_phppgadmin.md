---
title: "phppgadmin"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jewishj on 2006-06-03
I have been trying to get this to work for hours and something is evading me here.  I just need to setup postgresql for access with local php scripts (such as phppgadmin) but when I load phppgadmin by going to I get to the login prompt and nothing will work.  Every login is failed.  I have tried the login for root on this machine, the login for my user, the login postgres with no password, the login postgres with the password i gave it using the commands from the wiki (if you search for postgre in the wiki.. it will be the only result), and basically tried every combination i could think of.  I've tried modifying pg_hda.conf as described on this forum and I think I understand it pretty well, but I am pretty new to linux (and any former experience I had was a long time ago) so i've run out of ideas at this point.

I installed apache2, php5, mysql5, and postgre-sql 8.1 using synaptic.  apache, php, and mysql are working perfectly.  I can access pgsql just fine from the terminal and php-pgsql is fine too because I'm not getting any connection errors from phppgadmin (I hope this assumption is reasonable).

Following is my pg_hda.conf file:
```

# PostgreSQL Client Authentication Configuration File
# ===================================================
#
# Refer to the PostgreSQL Administrator's Guide, chapter "Client
# Authentication" for a complete description.  A short synopsis
# follows.
#
# This file controls: which hosts are allowed to connect, how clients
# are authenticated, which PostgreSQL user names they can use, which
# databases they can access.  Records take one of these forms:
#
# local      DATABASE  USER  METHOD  [OPTION]
# host       DATABASE  USER  CIDR-ADDRESS  METHOD  [OPTION]
# hostssl    DATABASE  USER  CIDR-ADDRESS  METHOD  [OPTION]
# hostnossl  DATABASE  USER  CIDR-ADDRESS  METHOD  [OPTION]
#
# (The uppercase items must be replaced by actual values.)
#
# The first field is the connection type: "local" is a Unix-domain socket,
# "host" is either a plain or SSL-encrypted TCP/IP socket, "hostssl" is an
# SSL-encrypted TCP/IP socket, and "hostnossl" is a plain TCP/IP socket.
#
# DATABASE can be "all", "sameuser", "samerole", a database name, or
# a comma-separated list thereof.
#
# USER can be "all", a user name, a group name prefixed with "+", or
# a comma-separated list thereof.  In both the DATABASE and USER fields
# you can also write a file name prefixed with "@" to include names from
# a separate file.
#
# CIDR-ADDRESS specifies the set of hosts the record matches.
# It is made up of an IP address and a CIDR mask that is an integer
# (between 0 and 32 (IPv4) or 128 (IPv6) inclusive) that specifies
# the number of significant bits in the mask.  Alternatively, you can write
# an IP address and netmask in separate columns to specify the set of hosts.
#
# METHOD can be "trust", "reject", "md5", "crypt", "password",
# "krb5", "ident", or "pam".  Note that "password" sends passwords
# in clear text; "md5" is preferred since it sends encrypted passwords.
#
# OPTION is the ident map or the name of the PAM service, depending on METHOD.
#
# Database and user names containing spaces, commas, quotes and other special
# characters must be quoted. Quoting one of the keywords "all", "sameuser" or
# "samerole" makes the name lose its special character, and just match a
# database or username with that name.
#
# This file is read on server startup and when the postmaster receives
# a SIGHUP signal.  If you edit the file on a running system, you have
# to SIGHUP the postmaster for the changes to take effect.  You can use
# "pg_ctl reload" to do that.

# Put your actual configuration here
# ----------------------------------
#
# If you want to allow non-local connections, you need to add more
# "host" records. In that case you will also need to make PostgreSQL listen
# on a non-local interface via the listen_addresses configuration parameter,
# or via the -i or -h command line switches.
#




# DO NOT DISABLE!
# If you change this first entry you will need to make sure that the
# database
# super user can access the database using some other method.
# Noninteractive
# access to all databases is required during automatic maintenance
# (autovacuum, daily cronjob, replication, and similar tasks).
#
# Database administrative login by UNIX sockets
local   all         postgres                          ident sameuser

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local	all	postgres				ident sameuser
local	all	all	password
#local   all         all                               ident sameuser
# IPv4 local connections:
#host    all         all         127.0.0.1/32          md5
# IPv6 local connections:
#host    all         all         ::1/128               md5

```

Thanks in advance for any help

---

### Post by adamkane on 2006-06-07
There aren't many postgresql users in the forums. Please keep us updated, if you have any successes or have any other information to share.

---

### Post by techstop on 2006-06-11
Can you try adding this line to your conf file?

```
local all all trust
```

Make this the ONLY uncommented line in your file.

I have set up postgres on another distribution (ClarkConnect) and this is all I had to do. Remember, each time you change the pg_hba.conf file, you need to restart the pgsql service (I do this on CC with webmin). See how you go.

---


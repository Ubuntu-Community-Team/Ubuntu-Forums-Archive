---
title: "apt-get, bugzilla3, mysql-server-5.1, mysql-server-5.0 installation issues"
date: 2009-06-13
forum: General Help
---

### Post by tonyf12 on 2009-06-13
I'm trying to install bugzilla3. I previously had mysql-server-5.1 installed, and it gave the following error:

```

tony@tony-laptop:~/Desktop/bugzilla-3.2.3$ sudo apt-get install -f
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libqt4-dbus libqtcore4 libphonon4 libqt4-xml libmysqlclient16 libqtgui4
  bsd-mailx mailx libqt4-script
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0B/23.6MB of archives.
After this operation, 79.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 128655 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I went onto the irc channel and asked for help where I was told to downgrade mysql to 5.0 and then install bugzilla.

So I went to do this. However when I ```
sudo apt-get remove mysql-server-5.1
```the bugzilla installation configuration begins, and goes until it stops again complaining about the 5.1 -> 5.0 downgrade.

So I went and asked again on the irc and I was told to
```

sudo apt-get clean
sudo apt-get update

```which I did.

It was still happening however so I removed the bugzilla3 package and tried to remove mysql then. And apparently it wasn't there. (I checked mysql-server, mysql-server-5.1 and mysql-server-5.0).

So I went to install bugzilla3 again, and it got as far as last time and complained about mysql-server-5.1 -> 5.0 downgrade. And now apt-get reported it was there, but it won't remove it as it starts the bugzilla install.

How do I fix this?

---

### Post by phillw on 2009-07-15
[SIZE=2]Hi...

I'm fairly okay with MySQL, but not with bugzilla ... however .....

This may be of assistance, failing that, they may be better placed to help you ?

[http://lpsolit.wordpress.com/2009/02/24/do-not-use-mysql-5131-or-newer-with-bugzilla-32-322/](http://lpsolit.wordpress.com/2009/02/24/do-not-use-mysql-5131-or-newer-with-bugzilla-32-322/)

Hope it is of help

Regards,

Phill.[/SIZE]

---


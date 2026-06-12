---
title: "amanda.conf not included with amanda-server or amanda-common ?"
date: 2009-03-25
forum: General Help
---

### Post by musashixXX on 2009-03-25
I've encountered an odd issue here. I've installed amanda-server via apt-get and after the install, the configuration file (amanda.conf) is nowhere to be found. AFAIK it's supposed to be in /etc/amanda/ but it isn't, and using 'locate' after running updatedb doesn't find it either.

Any help would be most appreciated!

---

### Post by wililupy on 2009-04-17
Unfortunatly, the brilliance that packaged this didn't include it. You have to write one manually. 
That is why I decided to just use the Version of Amanda from amanda.zmanda.com. It comes with a program called amserverconfig that writes all the configuration files for you and creates the directories you need to get it up and running. 

You will have to remove those packages before installing the newer version, and you will either have to delete the directories, or change the permissions on them, unless you download the source code for amanda and run ./configure --with-user backup --with-group backup that way it will use the backup user that is included with Ubuntu instead of creating the amandabackup user and the group disk.

If you do decide to go with the second option, where it creates the user and group for you, make sure you delete all the amanda directories before installing, /etc/amanda, /var/lib/amanda, /var/amanda, /tmp/amanda /var/log/amanda. Also, after the account is created, unlock the account by removing the :1: from /etc/shadow for the amandabackup user and setting a password for the user by typing passwd amandabackup. 

Then, to write your configurations, just type man amserverconfig to get the flags you need, and then run them. Man pages are you friend with amanda, and once you get everything setup, you will be very pleased with it. It just takes pulling your hair out for a few days and doing some trial and error.

Let me know if you have any questions.

---

### Post by cocoa117 on 2010-02-05
it's in /usr/share/doc/amanda-common/examples/amanda.conf.gz

---


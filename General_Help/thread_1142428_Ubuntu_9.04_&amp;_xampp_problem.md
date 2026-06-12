---
title: "Ubuntu 9.04 &amp; xampp problem"
date: 2009-04-29
forum: General Help
---

### Post by UbuGr on 2009-04-29
Hello,
I try to start xampp on ubuntu 9.04 and I have a problem to start the mysql server.
when try status(/opt/lamp/lamp status) show me that mysql is not running.
When try the phpmyadmin page I get the error message.

> #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured) 

and the file *.err in /opt/lamp/var/mysql directory

has always the following record

> 090429 12:32:32  mysqld started
090429 12:32:32 [Warning] option 'max_join_size': unsigned value 18446744073709551615 adjusted to 4294967295
090429 12:32:32 [Warning] option 'max_join_size': unsigned value 18446744073709551615 adjusted to 4294967295
090429 12:32:33  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name /opt/lampp/var/mysql/ib_logfile0
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
090429 12:32:33  mysqld ended



Can anyone help me?
thank you.

---

### Post by Bindsa on 2009-04-29
Maybe it's an permission problem, try using sudo before you start Lampp.

Hope this helped you.

--
B!ndsa

---

### Post by UbuGr on 2009-04-29
> **Bindsa said:**
> Maybe it's an permission problem, try using sudo before you start Lampp.

Hope this helped you.

--
B!ndsa
thank you for your time but
No, of cource I use sudo.
What could be happen??I have a new clear installation of ubuntu 9.04 and also new xampp files.With previous 8.10,8.04.. all was -too simple- ok!

---

### Post by davidbenson on 2009-05-09
I'm guessing that you first unpacked the archive in your home folder as yourself (not root) and then copied the lampp folder to /opt...  If so then the owner & permissions on /opt/lampp/var/mysql (and all the other files) will be incorrect...  The easiest way to fix this is to wipe out the /opt/lampp folder and put it back fresh - the correct way...

To remove:

   sudo rm -Rf /opt/lampp

To reinstall:

download the xampp package (unless you still have it)
open a shell (terminal)
navigate to the tar.gz file and...

   sudo tar -zxvf xampp-linux-1.7.1.tar.gz -C /opt

Then you should be able to start it up with:

   sudo /opt/lampp/lampp start


To make life easier for myself, I always create symlinks to lampp, mysql and mysqldump in my /bin directory...  Kinda hackish but whatever...  It's just my dev box...  :)

   sudo ln -s /opt/lampp /bin/lampp
   sudo ln -s /opt/lampp/bin/mysql /bin/mysql
   sudo ln -s /opt/lampp/bin/mysqldump /bin/mysqldump


(tested on Ubuntu 9.04)

Good luck!

---

### Post by mafaz13 on 2009-05-10
Okay I have installed and started LAMPP (XAMPP for Linux)

But when I try phpMyAdmin I get:

"[B]#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured) 

[/B]**Connection for controluser as defined in your configuration failed."**

Also get this when I start

[B]Starting XAMPP for Linux 1.7.1...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Another MySQL daemon is already running.
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.[/B]

Note: I have done the tar for LAMPP a couple of times already each time deleting and starting afresh

Can Anyone help please tanks

---

### Post by UbuGr on 2009-05-10
**davidbenson** thank you very much!!!
I solve my problem with your answer. I wonder how I had not thought of this, as the first time in earlier version of ubuntu I installed it with terminal.

**mafaz13**

"XAMPP: Another MySQL daemon is already running."

 maybe you have an other mysql instance running.

Try the command 

```

 ps -A | grep mysql

```

to see if a mysql process is running.

---

### Post by davidbenson on 2009-05-10
@UbuGr - glad it worked out for you...  :)

@Mafaz13 - UbuGr is correct...  you probably installed MySQL and ProFTP from the repos when you installed (or later with apt-get)...  If that is the case then the "installed" copies are causing a conflict with the Xampp copies...  You wouldn't normally install two copies of MySQL or Apache (although you can) so if you're gonna go with Xampp then it may be best to remove any installed copies of Apache and MySQL...  Hopefully this is a dev machine and not a production server...  Try stopping MySQL and Apache and then starting Xampp and let me know how it works out:

Stop MySQL:
sudo /etc/init.d/mysql stop

Stop Apache:
sudo /etc/init.d/apache2 stop

Stop ProFTPd:
sudo /etc/init.d/proftpd stop

Start Xampp:
sudo /opt/lampp/lampp start


If that solves your problem then you should be able to use apt to uninstall Apache, MySQL and ProFTP...  Alternatively, you can choose to just disable them from starting...

---

### Post by gleble on 2009-06-30
I have the same problem, upgraded to 9.04 (1)and I cannot get into phpmyadmin through Xampp. Xammp status says mysql is not running. I have another 9.04 upgrade(2) on the same disk and mysql works ((2) won't play radio which is why I want to use (1). Has anybody solved this yet? Thanks in anticipation.

---


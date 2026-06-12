---
title: "Setting up localhost?"
date: 2008-08-12
forum: Desktop Environments
---

### Post by deep_blue on 2008-08-12
It has only been 2 hours since I've been playing with Ubuntu and I'm already in love....

I want to setup a localhost so that websites that I'm designing with CMS (drupal) can be accessed locally. I'm using Ubuntu 8.04 through CD. Is there a way that I can install drupal locally?

Earlier I was using XAMPP in windows xp for configuring localhost.

Since I'm new to Ubuntu and this forum, I'm really expecting some love from you guys.:KS

---

### Post by Stemp on 2008-08-12
[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP#To%20install%20the%20default%20LAMP%20stack%20in%20Ubuntu%207.04%20(Feisty%20Fawn)%20Ubuntu%207.10%20(Gutsy%20Gibbon)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron)")

---

### Post by deep_blue on 2008-08-12
I tried installing lamp by this command "sudo tasksel install lamp-server" as provided in the link but it didn't get installed. I tried to install php5 still no use.

I'm running Ubuntu from "CD". Can I also install/use localhost form CD itself?

---

### Post by Stemp on 2008-08-12
```
sudo apt-get install apache2 apache2-doc mysql-server php5 libapache2-mod-php5 php5-mysql phpmyadmin
```

That should be enough.

---

### Post by deep_blue on 2008-08-12
Thank you for the command. I used that command and everything went fine until I was asked to provide password for mysql. And then, there was a list of "servers" to select from so I selected "apache2" and after that I got some errors so I used the above command again.

I'm not used to linux or ubuntu, so couldn't figure out what made this error to appear. Is there a way to correct it.

This is the error that I got after using the command for the second time.

```

ubuntu@ubuntu:~$ sudo apt-get install apache2 apache2-doc mysql-server php5 libapache2-mod-php5 php5-mysql phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
apache2-doc is already the newest version.
mysql-server is already the newest version.
php5 is already the newest version.
libapache2-mod-php5 is already the newest version.
php5-mysql is already the newest version.
phpmyadmin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 113 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                     /usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
                                                                                                                      [ OK ]
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
Reloading AppArmor profiles : done.
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
 * Starting MySQL database server mysqld                                                                                     /usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
                                                                                                                      [fail]
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
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 

```

But when I typed "http://localhost" in the browser it worked, as a page appeared saying "It works!". Is this fine as there was an error when installing as stated above. And where is www/public_html/htdocs folder and mysql/phpadmin located?

---

### Post by Stemp on 2008-08-12
Your errors seems to be a bug in live cd related to this one : [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/131976](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/131976)

But it should be fixed :(

> But when I typed "http://localhost" in the browser it worked, as a page appeared saying "It works!"

When you're looking at localhost, it doesn't use mysql (the database).
That just mean Apache (the http server) is ok.

> And where is www/public_html/htdocs folder and mysql/phpadmin located? 

for phpmyadmin it should be [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) but as mysql is not configured properly I don't know if it was installed.

for public_html you need the usedir module.
```
sudo a2enmod userdir
sudo /etc/init.d/apache2 reload
```

There will be a public_html directory in your home.
To acces it : [http://localhost/~yourusername/](http://localhost/~yourusername/)

---

### Post by deep_blue on 2008-08-12
I restarted my pc (live cd) so everything was again from the start. So when I applied the command
```
sudo apt-get install apache2 apache2-doc mysql-server php5 libapache2-mod-php5 php5-mysql phpmyadmin
``` it says "Couldn't find package phpmyadmin"

Is this also a bug?

---

### Post by Stemp on 2008-08-12
> it says "Couldn't find package phpmyadmin"

Is this also a bug? 

Nope, you have to :
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20the%20Universe%20and%20Multiverse%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20the%20Universe%20and%20Multiverse%20Repositories)

---

### Post by john test on 2008-08-12
I'm confused
1  why don't you go ahead and install ubuntu and set up the uids and pws?
2 Sincy you know xampp why are you not using xampp for Linux?

---

### Post by deep_blue on 2008-08-13
> **Stemp said:**
> Nope, you have to :
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20the%20Universe%20and%20Multiverse%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20the%20Universe%20and%20Multiverse%20Repositories)

Thanks again. But the link doesn't point on how to install phpadmin package. Or I'm missing something.

I've one doubt with Ubuntu. Can I install Ubuntu in USB flash drive and access it in a computer where there is no Floppy drive, CD/DVD Rom, Hard disk and other internal/external storage medias.

If so:
1. Then what should be the minimum space (GB) requirement for USB flash drive.
2. Can Ubuntu (which is running from USB flash drive) detects "another" flash drive if it is added.
3. Will it also detect printer and other hardware. (I mean will it work similarly to an uninterpretable operating system.)
4. Since I work on designing websites in windows xp where I use Photoshop, Dreamweaver and WS_FTP client, can you recommend some good replacement for these in Ubuntu?

@ john test: Currently in my pc windows xp is installed, so I don't want to have 2 operating system getting installed in one single harddrive. That is why I'm currently testing all the things from the CD Live. After I find that Ubuntu can fulfill my needs I'll jump to XAMPP linux as you said, which will be kooool. And meanwhile also wanted to test the Ubuntu inbuilt local host........

---

### Post by Stemp on 2008-08-13
The link point to the way to add the universe/multiverse repositories.
After doing it, reload your apt list and install phpmyadmin.
In a command line :
```
sudo apt-get update
sudo apt-get install phpmyadmin
```

A persistent install on a USB will be a good idea IMHO as it could work like a real installation of Ubuntu.
You'll need a 1GB USB key or bigger.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

NB: Using XAMPP in Linux is a bad idea because you cannot control and update the softwares in it.

---

### Post by deep_blue on 2008-08-19
I installed persistent ubuntu 8.04 in 4gb pendrive through live cd, where it took 2.1 gb space (i was not expecting that it will occupy this much of space).

I then enabled the universe and multiverse and installed localhost using

```
sudo apt-get install apache2 apache2-doc mysql-server php5 libapache2-mod-php5 php5-mysql phpmyadmin
``` Installation went without problem and I can access [http://localhost/](http://localhost/) in firefox browser.

but when i got to /var/www it doesn't allow me to change, rename or save files and folders. Though I have login with my main login id and password that I created while installing ubuntu but it says you don't have permission to access /var/www. And when i try to go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) it says 404 not found. I know phpmyadmin + mysql has been properly installed.

I think if I'm missing something or if something is left in the above code to execute.

---

### Post by cdtech on 2008-08-19
could be a owner/group issue. ls -la the /var/www directory and see if thats the case. You may need to add yourself to the group or give /var/www another owner as I did (webadmin).

---

### Post by deep_blue on 2008-08-19
> **cdtech said:**
> ls -la the /var/www directory and see if thats the case.

I'm new to linux and ubuntu. Can you give me a link on how can I do -la kinda stuffs?

---

### Post by deep_blue on 2008-08-20
I logged in ubuntu with the user and pass id that I created while installing it but I think I don't have root access since I can't read/write some of the folders and files? How can I login to the root?

---

### Post by Stemp on 2008-08-20
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mikjp on 2008-08-20
Read some documentation. 

Try man sudo in the terminal

mikko

---

### Post by deep_blue on 2008-08-28
Thank you for all your support. LAMP is now running fine.

Does anyone know how to enable "clean urls" in drupal 5.x?

---

### Post by Stemp on 2008-08-28
It should be :

Load the rewrite module in Apache

```
sudo a2enmod rewrite
```

Edit your Apache configuration file /etc/apache2/apache2.conf

Add theses lines at the end :

```
<Directory /var/www/your_drupal_directory>
    AllowOverride all
</Directory>

```

Restart Apache :

```
sudo /etc/init.d/apache2 reload
```

---

### Post by deep_blue on 2008-08-28
Thanks STEMP for your great help.

I followed this thread [http://ubuntuforums.org/showthread.php?t=845164](http://ubuntuforums.org/showthread.php?t=845164) and got the job done.

skipping microsoft........kicking unbuntu

---

### Post by deep_blue on 2008-08-28
Is it possible to also install cPanel?

---

### Post by deep_blue on 2008-09-04
Is it possible to also install cPanel and Java (JDK/JRE) under LAMP?

---


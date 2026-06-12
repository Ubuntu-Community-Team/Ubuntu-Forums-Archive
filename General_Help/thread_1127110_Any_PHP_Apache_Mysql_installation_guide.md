---
title: "Any PHP Apache Mysql installation guide"
date: 2009-04-16
forum: General Help
---

### Post by runnner on 2009-04-16
As a newbie, I need some guidance on installation of PHP Apache Mysql on Ubuntu, Who could give me some useful info? Thanks!

---

### Post by mb_webguy on 2009-04-16
Installing is easy.  Just open System->Administration->Synaptic Package Manager.  Go to Edit->Mark Packages By Task.  Click the box next to "LAMP server", and click OK.  Now click the Apply button.  

You just installed Apache, PHP, and MySQL.

I'd suggest installing the MySQL GUI tools (the mysql-admin and mysql-query-browser packages) while you're in Synaptic.

The default Apache web directory is the /var/www directory.  This is where you would put all of your html and php files.  You may want to change the ownership or permissions so you don't have to have superuser permissions to write to it (e.g. "sudo chmod +w /var/www").

---

### Post by _Purple_ on 2009-04-16
You can check [this link](http://www.howtoforge.com/ubuntu_lamp_for_newbies) for LAMP installation.:)

---

### Post by runnner on 2009-04-16
> **_Purple_ said:**
> You can check [this link](http://www.howtoforge.com/ubuntu_lamp_for_newbies) for LAMP installation.:)
This link is useful. Thank you all for help!

I log onto the ubuntu remotely using putty, what I get is a terminal windows. 

It looks like I must first upload the PHP Apache Mysql onto the hard disk, then following the steps in [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies). Is what I say right or not?

---

### Post by runnner on 2009-04-16
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo apt-get install mysql-server

The above 3 commands don't specify the paths where PHP Apache Mysql locate, how do the commands know where are they?



I downloaded httpd-2.2.11.tar.gz from apache.org and want to install it, does "sudo apt-get install apache2" work?

I downloaded PHP 5.2.9 (tar.gz) from php.net and want to install it, does "sudo apt-get install php5 libapache2-mod-php5" work? 

Thanks for help!

---

### Post by _Purple_ on 2009-04-16
> **runnner said:**
> sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo apt-get install mysql-server

The above 3 commands don't specify the paths where PHP Apache Mysql locate, how do the commands know where are they?



I downloaded httpd-2.2.11.tar.gz from apache.org and want to install it, does "sudo apt-get install apache2" work?

I downloaded PHP 5.2.9 (tar.gz) from php.net and want to install it, does "sudo apt-get install php5 libapache2-mod-php5" work? 

Thanks for help!

Apt-get is the Debian package management system and Ubuntu is a Debian based distribution. The commands mentioned above search the database for the package, download and install them. You do not have to download the ta.gz files manually. Moreover, apt-get installs the dependencies of the package as well. For more details on apt-get, please [click here](http://wiki.linuxhelp.net/index.php/Apt-get_Guide).

You can also install packages by going to System > Administration > Synaptic Package Manager. Then select the package name from the list and install. To check the details of the installed packages in Synaptic Package Manager, right click on the package name and go to properties.

Programs are usually installed in /usr/bin, /usr/local/bin and usr/sbin. Please check [this post](http://ubuntuforums.org/showpost.php?p=567454&postcount=2) for details.

> **runnner said:**
> This link is useful. Thank you all for help!

I log onto the ubuntu remotely using putty, what I get is a terminal windows. 

It looks like I must first upload the PHP Apache Mysql onto the hard disk, then following the steps in [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies). Is what I say right or not?

Do you mean you want to install it on a remote PC using putty?

---

### Post by mcduck on 2009-04-16
You said that you are using remote terminal connection to that machine. In that case using Synaptic is out of the question. Still, running following command has the same effect as using the "Mark Packages by Task" in Synaptic:

```
sudo tasksel install lamp-server
```

This will download, install & configure Apache, PHP and MySQL and all dependencies for you.

In addition I recommend getting PHPMyAdmin for easy database management through web browser:
```
sudo apt-get install phpmyadmin
```

Downloading stuff manually from internet isn't really the way things are usually done in Linux, even less in Debian-based distributions which have a lot better ways of handling software installation. At least as long as you have Internet connection..

---

### Post by runnner on 2009-04-16
> **_Purple_ said:**
> 
Do you mean you want to install it on a remote PC using putty?

What I meant was first FTP uploading the PHP Apache Mysql onto the hard disk of the linux server, then following the steps in [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies). 

After reading your replies, I know I needn't do FTP uploading,   just "sudo apt-get install " will work. Thank you for help!

---

### Post by runnner on 2009-04-17
> 
From [http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)
you need to setup your sources.list file which is located in /etc/apt/sources.list . This file contains the information that apt looks for when attempting to install a package.


IF I will install a new package which is not in the /etc/apt/sources.list, should I first add the new package info such as its download url into the sources.list manually? Then I call "apt-get install very_new_package"

---

### Post by mcduck on 2009-04-17
> **runnner said:**
> IF I will install a new package which is not in the /etc/apt/sources.list, should I first add the new package info such as its download url into the sources.list manually? Then I call "apt-get install very_new_package"

If the package is in some 3rd party repository, you may add that repository to the sources.lst file (sources.lst doesn't list packages, it lists software servers designed to provide packages and package information for Ubuntu's package manager). You definitely can't add stuff that you download from normal WWW sites there, even normal URL syntax won't work.

If you download things by hand apt-get won't help you. It only manages installed packages and software that's available in repositories.

When you download .deb packages from the net you use "dpkg" to install them. As in "sudo dpkg -i yourpackage.deb". After installed, Ubuntu's package management will be aware of this package and it can be removed with apt-get or nay other package management tool.

---

### Post by runnner on 2009-04-20
Thank you for your replies!

I prefer to use apt-get install.
After run sudo apt-get install AMP_NAME , where do apache2, php and mysql  locate? Thanks!

---

### Post by _Purple_ on 2009-04-20
You can use the following command to find the location of package
```
dpkg -L <packagename>
```

---

### Post by nruner on 2009-04-30
use locate to find where they are.

---


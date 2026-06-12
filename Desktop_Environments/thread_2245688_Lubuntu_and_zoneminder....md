---
title: "Lubuntu and zoneminder..."
date: 2014-09-25
forum: Desktop Environments
---

### Post by krr2 on 2014-09-25
Hello everybody....

I'm a noob (sort of...) but I intend to use an old core solo mac mini with Lubuntu to deal two or three foscam H264 webcam....

ZoneMinder seems to be the app to use.

I followed several tutorial but none of them are for lubuntu, they are for Ubuntu... I thought it would be the same instructions... but it does not...

For now, I'm trying in a VMWare machine in my mac pro... with this tutorial (and others): [http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.26.5_the_easy_way](http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.26.5_the_easy_way)

is there any change that should be done in this tutorial if it was for Lubuntu ?

thanks for help

---

### Post by ajgreeny on 2014-09-25
I will not comment on the sense of installing zoneminder as I know nothing about it, but the procedure shown to install it in the link you show seems absolutely fine whatever *ubuntu family OS you are using.

Have you tried this yet or have you still to take the action?

Just remember that the **sudo su** command gives you a root terminal and whilst that is open you will need to be aware that it is possible, with a typo or similar, to do untold damage to your system, as there will be no "Are you sure?" questions if you do something silly and inadvertently remove something with a command.

---

### Post by krr2 on 2014-09-25
> **ajgreeny said:**
> I will not comment on the sense of installing zoneminder as I know nothing about it, but the procedure shown to install it in the link you show seems absolutely fine whatever *ubuntu family OS you are using.

Have you tried this yet or have you still to take the action?

Just remember that the **sudo su** command gives you a root terminal and whilst that is open you will need to be aware that it is possible, with a typo or similar, to do untold damage to your system, as there will be no "Are you sure?" questions if you do something silly and inadvertently remove something with a command.


Of course, I tried... not on the mac mini (it's my mother's) but on a Lubuntu freshly installed in a VMWare machine... I followed all instruction, zoneminder seems to be installed, apache is installed for sure (Iv'e checked with 127.0.0.1).... but when I try to reach 127.0.0.1/zm/ .... I have a 404 ...

I know I got be prudent with sudo su, even if I'm not familiar with terminal and code ... that's why I decided to "test" the stuff in a virtual machine...

---

### Post by alsanti on 2014-11-21
I installed it but all I get is this error  "Unable determine arp path, status is '127' and 255" and this is with 1.28 and the latest verion of Lubuntu.  I looked every where for a fis to no avail?

---

### Post by alsanti on 2014-11-21
So I worked on this a bit more and actually got it to work in lubuntu 14,10.  I did the following, removed the install as follows.
sudo apt-get remove --purge zoneminder
sudo apt-get remove --purge mysql-server mysql-client mysql-common
sudo rm -rf /var/lib/mysql
sudo apt-get remove --purge apache2*
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo rm -r /var/www/*
sudo rm -r /etc/apache2/*
sudo rmdir /var/www
sudo rmdir /etc/apache2
sudo rm -r /opt/zm
sudo rm /etc/apache2/conf.d/zoneminder.conf
sudo dpkg --configure -a

reboot hardware


I first installed apache2, ffmpeg, Mysql (latest version) and 
Install Cambozola


cd /usr/src && wget [http://www.andywilcock.com/code/cambozola/cambozola-latest.tar.gz](http://www.andywilcock.com/code/cambozola/cambozola-latest.tar.gz)

tar -xzvf cambozola-latest.tar.gz

replace 935 with cambozola version downloaded 
 cp cambozola-0.935/dist/cambozola.jar /usr/share/zoneminder 

Create two symbolic links 
 ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf ( the conf.d gave me some issues, I ran the latter first then this one an it was accepted)
ln -s /etc/zm/apache.conf /etc/apache2/conf-enabled/zoneminder.conf
CGI is not enabled in Ubuntu 14.04 by default. Enable it this way:  
 a2enmod cgi
Create a new user 
 adduser www-data video
Restart Apache 
 /etc/init.d/apache2 force-reload 
or 
  service apache2 restart

After all this then I installed Zm 1.28 and then ran the following Msql from the terminal: locate mysql, thi seem to run all the files, not sure what it did but it seemed to do the trick.
im using this USB camera Microsoft® LifeCam Cinema(TM) (usb-0000:00:1d.7-5):

Seems to be working now. After all this, now I have to teach myself how to actually use ZM.

---


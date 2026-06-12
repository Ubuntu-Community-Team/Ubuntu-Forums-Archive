---
title: "Gallery2 update disaster ?"
date: 2010-07-20
forum: Desktop Environments
---

### Post by dargaud on 2010-07-20
Hello all,
today I went along with the regular updates and apparently all my gallery2 data (tens of thousands of organized images) has been nuked:
```
$ sudo aptitude full-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils gallery2 icedtea-6-jre-cacao icedtea6-plugin language-pack-en 
  language-pack-en-base language-pack-fr language-pack-fr-base language-pack-gnome-en language-pack-gnome-en-base 
  language-pack-gnome-fr language-pack-gnome-fr-base language-pack-gnome-it language-pack-gnome-it-base 
  language-pack-it language-pack-it-base language-pack-kde-en language-pack-kde-en-base language-pack-kde-fr 
  language-pack-kde-fr-base language-pack-kde-it language-pack-kde-it-base mapserver-bin openjdk-6-jdk openjdk-6-jre 
  openjdk-6-jre-headless openjdk-6-jre-lib php5-mapscript python-mapscript 
31 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/104MB of archives. After unpacking 2,679kB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 358148 files and directories currently installed.)
...
Preparing to replace gallery2 2.3-1ubuntu3 (using .../gallery2_2.3-1ubuntu3.1_all.deb) ...
Unpacking replacement gallery2 ...
...
Setting up gallery2 (2.3-1ubuntu3.1) ...
ln: creating symbolic link `/usr/share/gallery2/lib/smarty': No such file or directory
dpkg: error processing gallery2 (--configure):
 subprocess installed post-installation script returned error exit status 1
...
Errors were encountered while processing:
 gallery2
localepurge: Disk space freed in /usr/share/locale: 2960 KiB
localepurge: Disk space freed in /usr/share/man: 256 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 3216 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gallery2 (2.3-1ubuntu3.1) ...
ln: creating symbolic link `/usr/share/gallery2/lib/smarty': No such file or directory
dpkg: error processing gallery2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gallery2
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 updates [-31].

```
```
$ ll /etc/apache2/conf.d/gallery2*
lrwxrwxrwx 1 root root  25 2009-02-03 01:00 /etc/apache2/conf.d/gallery2 -> /etc/gallery2/apache.conf
-rw-r--r-- 1 root root 415 2010-06-13 19:34 /etc/apache2/conf.d/gallery2~

$ ll /etc/gallery2/
total 16
drwxr-xr-x   2 root     root  4096 2010-07-20 16:54 ./
drwxr-xr-x 202 root     root 12288 2010-07-20 16:54 ../
-rw-r-----   1 www-data root     0 2010-07-20 16:54 config.php

$ cat /etc/apache2/conf.d/gallery2~ # Previous version
Alias /Gallery /usr/share/gallery2

<Directory /usr/share/gallery2>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
  php_value memory_limit 64M
  php_value error_reporting E_ALL & ~E_NOTICE & ~E_DEPRECATED
</Directory>

# some people prefer a simple URL like http://gallery2.example.com
#<VirtualHost 1.2.3.4>
#  DocumentRoot /usr/share/gallery2
#  ServerName gallery2.example.com
#</VirtualHost>

$ find /usr/share/gallery2/ -ls
14270469    4 drwxr-xr-x   3 root     root         4096 Jul 20 16:48 /usr/share/gallery2/
14270479    4 drwxr-xr-x   2 root     root         4096 Jul 20 16:49 /usr/share/gallery2/lib
14271303    0 lrwxrwxrwx   1 root     root           20 Jul 20 16:49 /usr/share/gallery2/lib/adodb -> /usr/share/php/adodb
14271302    0 lrwxrwxrwx   1 root     root           21 Jul 20 16:48 /usr/share/gallery2/lib/smarty -> /usr/share/php/smarty

```

Now where the heck have my images gone ?!?

---

### Post by dargaud on 2010-07-30
I got a [partial solution here]("http://gallery.menalto.com/node/97041"), but the real solution would be for ubuntu to stop bundling Gallery2 if they don't know how to maintain the configuration from one version to another...

---


---
title: "Help with broken package."
date: 2009-01-29
forum: General Help
---

### Post by RedWagon on 2009-01-29
The ice storm killed power at work and our server was not properly shut down.  I just went to update and got a bunch of errors.  I ran apt-get install -f to try and fix it but got this:

lakeview@Server:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apache2-utils
The following NEW packages will be installed:
  apache2-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
44 not fully installed or removed.
Need to get 0B/346kB of archives.
After unpacking 545kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 142546 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.2.4-3ubuntu0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/htpasswd', which is also in package thttpd-util
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lakeview@Server:~$

---

### Post by icheyne on 2009-01-29
```
sudo aptitude reinstall apache2-utils
```

---

### Post by RedWagon on 2009-02-27
Still isn't working...
```
lakeview@Server:~$ sudo aptitude reinstall apache2-utils
[sudo] password for lakeview:
Sorry, try again.
[sudo] password for lakeview:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
apache2-utils is not currently installed, so it will not be reinstalled.
The following packages are BROKEN:
  apache2.2-common 
The following partially installed packages will be configured:
  apache2 apache2-mpm-prefork ffmpeg libapache2-mod-php5 libapr1 
  libaprutil1 libarchive-tar-perl libarchive-zip-perl libavcodec1d 
  libavformat1d libavutil1d libcompress-raw-zlib-perl libcompress-zlib-perl 
  libconvert-binhex-perl libdate-manip-perl libdbd-mysql-perl libdbi-perl 
  libdc1394-13 libdevice-serialport-perl libgsm1 libid3tag0 libimlib2 
  libio-compress-base-perl libio-compress-zlib-perl libio-stringy-perl 
  libio-zlib-perl libmailtools-perl libmime-lite-perl libmime-perl 
  libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 libswscale1d 
  libtimedate-perl libungif4g mysql-client-5.0 mysql-server 
  mysql-server-5.0 php5 php5-common php5-mysql zoneminder 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  apache2.2-common: Depends: apache2-utils but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
apache2-utils [2.2.4-3ubuntu0.1 (gutsy-updates, gutsy-security)]

Score is 41

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  apache2-utils 
The following NEW packages will be installed:
  apache2-utils 
The following partially installed packages will be configured:
  apache2 apache2-mpm-prefork apache2.2-common ffmpeg libapache2-mod-php5 
  libapr1 libaprutil1 libarchive-tar-perl libarchive-zip-perl libavcodec1d 
  libavformat1d libavutil1d libcompress-raw-zlib-perl libcompress-zlib-perl 
  libconvert-binhex-perl libdate-manip-perl libdbd-mysql-perl libdbi-perl 
  libdc1394-13 libdevice-serialport-perl libgsm1 libid3tag0 libimlib2 
  libio-compress-base-perl libio-compress-zlib-perl libio-stringy-perl 
  libio-zlib-perl libmailtools-perl libmime-lite-perl libmime-perl 
  libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 libswscale1d 
  libtimedate-perl libungif4g mysql-client-5.0 mysql-server 
  mysql-server-5.0 php5 php5-common php5-mysql zoneminder 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/346kB of archives. After unpacking 545kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 142546 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.2.4-3ubuntu0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/htpasswd', which is also in package thttpd-util
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libio-stringy-perl (2.110-2) ...

Setting up libpq5 (8.2.11-0ubuntu0.7.10) ...

Setting up libconvert-binhex-perl (1.119+pristine-1) ...
Setting up libio-compress-base-perl (2.005-1) ...
Setting up libtimedate-perl (1.1600-7) ...
Setting up libmysqlclient15off (5.0.45-1ubuntu3.4) ...

Setting up libungif4g (4.1.4-5) ...

Setting up libgsm1 (1.0.10-13build1) ...

Setting up libcompress-raw-zlib-perl (2.005-1) ...
Setting up libmailtools-perl (1.74-1) ...
Setting up libmime-perl (5.420-1) ...
Setting up libdevice-serialport-perl (1.002-1) ...

Setting up libdate-manip-perl (5.44-5) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up php5-common (5.2.3-1ubuntu6.4) ...
Setting up libdc1394-13 (1.1.0-3ubuntu3) ...

dpkg: dependency problems prevent configuration of apache2.2-common:
 apache2.2-common depends on apache2-utils; however:
  Package apache2-utils is not installed.
dpkg: error processing apache2.2-common (--configure):
 dependency problems - leaving unconfigured
Setting up libmime-lite-perl (3.01-8) ...
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
Setting up libplrpc-perl (0.2017-1.1) ...
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.2.3-1ubuntu6.4) | php5-cgi (>= 5.2.3-1ubuntu6.4); however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Setting up libavutil1d (3:0.cvs20070307-5ubuntu4.1) ...

dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on phpapi-20060613+lfs; however:
  Package phpapi-20060613+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20060613+lfs is not configured yet.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
Setting up libapr1 (1.2.7-8.2ubuntu1) ...

Setting up libid3tag0 (0.15.1b-10) ...

Setting up libdbi-perl (1.57-1) ...
Setting up libio-compress-zlib-perl (2.005-1) ...
dpkg: dependency problems prevent configuration of zoneminder:
 zoneminder depends on libapache2-mod-php5 | libapache2-mod-php4; however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php4 is not installed.
 zoneminder depends on php5 | php4; however:
  Package php5 is not configured yet.
  Package php4 is not installed.
 zoneminder depends on php5-mysql | php4-mysql; however:
  Package php5-mysql is not configured yet.
  Package php4-mysql is not installed.
dpkg: error processing zoneminder (--configure):
 dependency problems - leaving unconfigured
Setting up libswscale1d (3:0.cvs20070307-5ubuntu4.1) ...

Setting up libdbd-mysql-perl (4.004-2) ...
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.4-3ubuntu0.1); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
Setting up libaprutil1 (1.2.7+dfsg-2build1) ...

Setting up libcompress-zlib-perl (2.005-1ubuntu0.2) ...
Setting up libimlib2 (1.3.0.0debian1-4ubuntu0.1) ...

dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (>= 2.2.4-3ubuntu0.1) | apache2-mpm-prefork (>= 2.2.4-3ubuntu0.1) | apache2-mpm-event (>= 2.2.4-3ubuntu0.1); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
Setting up libavcodec1d (3:0.cvs20070307-5ubuntu4.1) ...

Setting up mysql-client-5.0 (5.0.45-1ubuntu3.4) ...

Setting up libavformat1d (3:0.cvs20070307-5ubuntu4.1) ...

Setting up libio-zlib-perl (1.04-1) ...
Setting up ffmpeg (3:0.cvs20070307-5ubuntu4.1) ...
Setting up libarchive-zip-perl (1.18-1) ...
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.4) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
chown: cannot access `/var/run/mysqld': No such file or directory
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up mysql-server (5.0.45-1ubuntu3.4) ...
Setting up libarchive-tar-perl (1.31-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 apache2.2-common
 libapache2-mod-php5
 php5
 php5-mysql
 zoneminder
 apache2-mpm-prefork
 apache2
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
lakeview@Server:~$ sudo aptitude reinstall apache2-utils
[sudo] password for lakeview:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
apache2-utils is not currently installed, so it will not be reinstalled.
The following packages are BROKEN:
  apache2.2-common 
The following partially installed packages will be configured:
  apache2 apache2-mpm-prefork libapache2-mod-php5 php5 php5-mysql 
  zoneminder 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  apache2.2-common: Depends: apache2-utils but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
apache2-utils [2.2.4-3ubuntu0.1 (gutsy-updates, gutsy-security)]

Score is 41

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  apache2-utils 
The following NEW packages will be installed:
  apache2-utils 
The following partially installed packages will be configured:
  apache2 apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5 
  php5-mysql zoneminder 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/346kB of archives. After unpacking 545kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 142546 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.2.4-3ubuntu0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/htpasswd', which is also in package thttpd-util
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of apache2.2-common:
 apache2.2-common depends on apache2-utils; however:
  Package apache2-utils is not installed.
dpkg: error processing apache2.2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.2.3-1ubuntu6.4) | php5-cgi (>= 5.2.3-1ubuntu6.4); however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on phpapi-20060613+lfs; however:
  Package phpapi-20060613+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20060613+lfs is not configured yet.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zoneminder:
 zoneminder depends on libapache2-mod-php5 | libapache2-mod-php4; however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php4 is not installed.
 zoneminder depends on php5 | php4; however:
  Package php5 is not configured yet.
  Package php4 is not installed.
 zoneminder depends on php5-mysql | php4-mysql; however:
  Package php5-mysql is not configured yet.
  Package php4-mysql is not installed.
dpkg: error processing zoneminder (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.4-3ubuntu0.1); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (>= 2.2.4-3ubuntu0.1) | apache2-mpm-prefork (>= 2.2.4-3ubuntu0.1) | apache2-mpm-event (>= 2.2.4-3ubuntu0.1); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2.2-common
 libapache2-mod-php5
 php5
 php5-mysql
 zoneminder
 apache2-mpm-prefork
 apache2
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
lakeview@Server:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [189B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://us.archive.ubuntu.com gutsy-updates Release.gpg [189B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]             
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                   
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US       
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US     
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US     
Get:4 http://security.ubuntu.com gutsy-security Release [58.5kB]     
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release                              
Get:5 http://us.archive.ubuntu.com gutsy-updates Release [58.5kB]        
Hit http://archive.ubuntu.com gutsy/main Packages                            
Hit http://archive.ubuntu.com gutsy/universe Packages      
Hit http://archive.ubuntu.com gutsy/restricted Packages    
Hit http://archive.ubuntu.com gutsy/multiverse Packages                        
Hit http://archive.ubuntu.com gutsy/universe Sources                           
Hit http://archive.ubuntu.com gutsy/main Sources                               
Hit http://archive.ubuntu.com gutsy/multiverse Sources                         
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Get:6 http://us.archive.ubuntu.com gutsy-updates/main Packages [305kB]         
Get:7 http://security.ubuntu.com gutsy-security/main Packages [140kB]
Get:8 http://security.ubuntu.com gutsy-security/restricted Packages [5736B] 
Get:9 http://security.ubuntu.com gutsy-security/universe Packages [98.5kB]     
Get:10 http://us.archive.ubuntu.com gutsy-updates/restricted Packages [6059B]  
Get:11 http://us.archive.ubuntu.com gutsy-updates/universe Packages [121kB]    
Get:12 http://security.ubuntu.com gutsy-security/multiverse Packages [8279B]   
Get:13 http://security.ubuntu.com gutsy-security/main Sources [27.9kB]         
Get:14 http://security.ubuntu.com gutsy-security/restricted Sources [935B]     
Get:15 http://security.ubuntu.com gutsy-security/universe Sources [14.2kB]     
Get:16 http://security.ubuntu.com gutsy-security/multiverse Sources [1340B]    
Get:17 http://us.archive.ubuntu.com gutsy-updates/multiverse Packages [13.1kB] 
Get:18 http://us.archive.ubuntu.com gutsy-updates/main Sources [82.7kB]
Get:19 http://us.archive.ubuntu.com gutsy-updates/restricted Sources [935B]
Get:20 http://us.archive.ubuntu.com gutsy-updates/universe Sources [20.2kB]
Get:21 http://us.archive.ubuntu.com gutsy-updates/multiverse Sources [2456B]
Fetched 965kB in 3s (277kB/s)                           
Reading package lists... Done
lakeview@Server:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apache2-utils
The following NEW packages will be installed:
  apache2-utils
0 upgraded, 1 newly installed, 0 to remove and 53 not upgraded.
7 not fully installed or removed.
Need to get 0B/346kB of archives.
After unpacking 545kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 142546 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.2.4-3ubuntu0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/htpasswd', which is also in package thttpd-util
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-utils_2.2.4-3ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lakeview@Server:~$ 

```

---


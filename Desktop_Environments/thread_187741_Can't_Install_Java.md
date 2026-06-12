---
title: "Can't Install Java"
date: 2006-06-03
forum: Desktop Environments
---

### Post by david_e on 2006-06-03
When I try to install BlackDown Java I see this:

```
davide@acer-ferrari:~/temp$ sudo apt-get install j2re1.4
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  j2re1.4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/22.5MB of archives.
After unpacking 60.3MB of additional disk space will be used.
Preconfiguring packages ...
j2re1.4 failed to preconfigure, with exit status 10
(Reading database ... 90051 files and directories currently installed.)
Unpacking j2re1.4 (from .../j2re1.4_1.4.2.02-1ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/j2re1.4_1.4.2.02-1ubuntu3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/j2re1.4_1.4.2.02-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I had a similar problem with Sun Java:

```

davide@acer-ferrari:~/temp$ sudo apt-get install sun-java5-jre
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  sun-java5-bin
Suggested packages:
  sun-java5-plugin ia32-sun-java5-plugin sun-java5-fonts
The following NEW packages will be installed:
  sun-java5-bin sun-java5-jre
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.5MB of archives.
After unpacking 83.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com dapper/multiverse sun-java5-bin 1.5.0-06-1 [22.1MB]
Get:2 http://archive.ubuntu.com dapper/multiverse sun-java5-jre 1.5.0-06-1 [7341kB]
Fetched 29.5MB in 1m3s (464kB/s)
Preconfiguring packages ...
(Reading database ... 90051 files and directories currently installed.)
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
But I was able to install it following this guide:

[https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e](https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e)

*** EDIT ***
I have already tried to check if there are broken dependecies: 
```
davide@acer-ferrari:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree... Done
```

---

### Post by Titus A Duxass on 2006-06-03
Try using Automatix and just select the required package.

---

### Post by irv on 2006-06-03
See the end of thread [http://www.ubuntuforums.org/showthread.php?t=187670]("http://www.ubuntuforums.org/showthread.php?t=187670")

---

### Post by david_e on 2006-06-03
I experienced this issue when trying to install azureus from adept. I manged to install it using the tar.bz2 pack and installing Sun Jre  manually and I have already tested it downloading Xubuntu 6.06 ISO, so I don't want to use automatix to reinstall it...

I just don't understand why I am not able to install Java from the repositories... I was thinking if this is a bug of some kind...

I have forgotten to say that I am using Kubuntu 6.06 RC....

---

### Post by brownrl on 2006-06-03
Had good luck this way:

1. Download the sun  jre 1.5.0_07 whatever from sun

2. un tar gz it

3. sudo cp the whole thing to /usr/java/

4. replace the following sim links:

sudo ln -fs /usr/java/jrexxx/bin/java /usr/bin/java
sudo ln -fs /usr/java/jrexxx/bin/java_vm /usr/bin/java_vm
sudo ln -fs /usr/java/jrexxx/bin/javaws /usr/bin/javaws #not sure if needed

5. The firefox plugin:

sudo ln -fs /usr/java/jre1.5.0_07/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so

You then are using the latest java. Unfortunately once the next version comes you have to do the process again.

Lastely, Java is the dumbest stupidest thing to hit the computing world. Make sure that you complain as much as possible to who/what ever is forcing you to use it.

R

---

### Post by david_e on 2006-06-03
Thank you for the reply. 

Sorry but, due to my poor English, there is a misunderstand: I was able to install Sun Java before I started this thread. 

My problem is I wish to install Blackdown Java for testing reasons, but I don't know how as the only way I know is by repositories. 

I just said I had a similar problem with Sun that I was able to solve only by fakeroot as irv on the thread he pointed...

I wonder if it is a problem of repo's or there is some broken dependecies in my system....

---


---
title: "cupsys update will not install"
date: 2008-12-12
forum: Desktop Environments
---

### Post by tiggsy on 2008-12-12
3 days in a row it has failed, with the following error

E: /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.2_i386.deb: subprocess new pre-removal script returned error exit status 102

How do i get it to work?

I couldn't copy the terminal output, so i'm attaching what I got from a screenshot

---

### Post by tiggsy on 2008-12-17
Bump. This is preventing me from installing stuff on Synaptic

---

### Post by tiggsy on 2008-12-19
every single update is now failing, including adobeAIR

I need to get this working. help!!!

---

### Post by tiggsy on 2009-01-22
I managed to get round this, by running the Recovery mode and cleaning it up. Then whenever it came up on the updates, I would untick it.

Unfortunately, it has become a "security" matter, and I can't untick it. But it's stopping all other updates. I really need a way to get this to work.

Here's the latest terminal output:

```
Preconfiguring packages ...
(Reading database ... 174432 files and directories currently installed.)
Preparing to replace cupsys 1.3.7-1ubuntu3.1 (using .../cupsys_1.3.7-1ubuntu3.3_i386.deb) ...
Ignoring nonregistered document `cupsys'
invoke-rc.d: not a symlink: /etc/rc2.d/S19cupsys
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: not a symlink: /etc/rc2.d/S19cupsys
dpkg: error processing /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
update-rc.d: warning: /etc/rc2.d/S19cupsys is not a symbolic link
invoke-rc.d: not a symlink: /etc/rc2.d/S19cupsys
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was actually trying to do something completely unrelated, but this comes up all the time whenever I try to do anything in the way of installing, removing, etc.

---

### Post by XanTrax on 2009-01-22
This is going to sound stupid...but,

I was having a similar problem where nothing would be able to install because of something corrupting and almost every package wanting to be configured.  Everyone had said to remove the pkg (dpkg -r <pkg_name>) but it would not work for me...all I did was "sudo apt-get remove <pkg>" where <pkg> was the corrupted packages.  Some of them wanted to take out ubuntu-desktop, so, I let it.  Then, when it was done I ran "sudo apt-get install ubuntu-desktop" and it reinstalled all the correct packages.

My error was

```

A package failed to install.  Trying to recover:
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.

```

And it listed packages that had problems installing...so I removed each of those packages.  What you can do is:

```

sudo dpkg -r cupsys
sudo aptitude reinstall

```

Give that a try.

---

### Post by tiggsy on 2009-01-22
> **XanTrax said:**
> What you can do is:

```

sudo dpkg -r cupsys
sudo aptitude reinstall

```

Give that a try.

Thanks. But when I tried it, I got: 

```
dpkg: error processing cupsys (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 cupsys

```

which was what I was getting some weeks? back when I fixed it by going into recover and doing something or other... Anyway, I have the thread that gave me that tagged: [http://ubuntuforums.org/showthread.php?t=933492](http://ubuntuforums.org/showthread.php?t=933492)

I guess I will try doing that, then removing cupsys as you suggest and reinstalling it... In the morning. :D

---

### Post by XanTrax on 2009-01-22
> **tiggsy said:**
> Thanks. But when I tried it, I got: 

```
dpkg: error processing cupsys (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 cupsys

```

which was what I was getting some weeks? back when I fixed it by going into recover and doing something or other... Anyway, I have the thread that gave me that tagged: [http://ubuntuforums.org/showthread.php?t=933492](http://ubuntuforums.org/showthread.php?t=933492)

I guess I will try doing that, then removing cupsys as you suggest and reinstalling it... In the morning. :D

You could also try this:

NOTE: Remember, all commands below are to be executed one at a time

```

cd /var/cache/apt/archives
find * | grep -i cupsys

```

You should see

```

cupsys_1.3.7-1ubuntu3.3_i386.deb

```

Appear on the screen.  Then, issue:

```

sudo mv cupsys_1.3.7-1ubuntu3.3_i386.deb cupsys_1.3.7-1ubuntu3.3_i386.deb_old
sudo apt-get purge cupsys
sudo apt-get install --reinstall cupsys

```

The purge may not work.

---

### Post by tiggsy on 2009-01-23
OK. I rebooted, selected fix broken packages, and then did the normal reboot.

I tried your list of commands here, and all seemed to go well until I got to this one:

> sudo apt-get install --reinstall cupsys

where I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libnet-daemon-perl libxine1-misc-plugins libxcb-xv0 libdbi-perl
  libmp4v2-0 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libfftw3-3
  libxine1-bin libplrpc-perl libxine1-ffmpeg libxcb-shape0 libtunepimp5
  libifp4 libxine1-plugins libxcb-shm0 libnjb5 libofa0 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up cupsys (1.3.7-1ubuntu3.3) ...
Reloading AppArmor profiles : done.
update-rc.d: warning: /etc/rc2.d/S19cupsys is not a symbolic link
invoke-rc.d: not a symlink: /etc/rc2.d/S19cupsys
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So it seems that the package for cupsys is broken on the repository!?? And its been that way for some time. I need my printer. I also need to be able to install other packages, but it looks as if this is going to go the same way as both times before...

How do I get a non-broken package?

---

### Post by XanTrax on 2009-01-23
Rather then me typing everything to you, please try this persons suggestion:

[http://ubuntuforums.org/showpost.php?p=1408484&postcount=3](http://ubuntuforums.org/showpost.php?p=1408484&postcount=3)

and please post the output.

---

### Post by tiggsy on 2009-01-23
This is what I did, following the post you pointed me to:

```
cd /etc/rc2.d/
ls -al
```

S19cupsys showed up with no symlink specified

```
sudo rm S19cupsys
sudo apt-get remove -f cupsys
```

got me: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libnet-daemon-perl libxine1-misc-plugins libxcb-xv0 libdbi-perl
  libmp4v2-0 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libfftw3-3
  libxine1-bin libplrpc-perl libxine1-ffmpeg libxcb-shape0 libtunepimp5
  libifp4 libxine1-plugins libxcb-shm0 libnjb5 libofa0 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  cupsys
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 174441 files and directories currently installed.)
Removing cupsys ...
 * Stopping Common Unix Printing System: cupsd                           [ OK ]
```

then 

```
sudo apt-get -f install
```

gave me 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libnet-daemon-perl libxine1-misc-plugins libxcb-xv0 libdbi-perl
  libmp4v2-0 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libfftw3-3
  libxine1-bin libplrpc-perl libxine1-ffmpeg libxcb-shape0 libtunepimp5
  libifp4 libxine1-plugins libxcb-shm0 libnjb5 libofa0 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
sudo apt-get install cupsys
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libnet-daemon-perl libxine1-misc-plugins libxcb-xv0 libdbi-perl
  libmp4v2-0 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libfftw3-3
  libxine1-bin libplrpc-perl libxine1-ffmpeg libxcb-shape0 libtunepimp5
  libifp4 libxine1-plugins libxcb-shm0 libnjb5 libofa0 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  cups-pdf cupsys-driver-gutenprint foomatic-filters-ppds hplip xpdf-korean
  xpdf-japanese xpdf-chinese-traditional xpdf-chinese-simplified
Recommended packages:
  avahi-utils
The following NEW packages will be installed
  cupsys
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1863kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy-updates/main cupsys 1.3.7-1ubuntu3.3 [1863kB]
Fetched 1863kB in 7s (252kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package cupsys.
(Reading database ... 172891 files and directories currently installed.)
Unpacking cupsys (from .../cupsys_1.3.7-1ubuntu3.3_i386.deb) ...
Setting up cupsys (1.3.7-1ubuntu3.3) ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd                           [ OK ] 
```

finally

```
sudo ln -s ../init.d/cupsys s19cupsys
ls -al
```

showed s19cupsys -> ../init.d/cupsys in the list.

So, it looks like it worked... If not, I'll keep you posted.

And THANKS!!

PS. Can't find the "thank you" button - where'd it go?

---

### Post by XanTrax on 2009-01-23
> **tiggsy said:**
> This is what I did, following the post you pointed me to:

```
cd /etc/rc2.d/
ls -al
```

S19cupsys showed up with no symlink specified

```
sudo rm S19cupsys
sudo apt-get remove -f cupsys
```

got me: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libnet-daemon-perl libxine1-misc-plugins libxcb-xv0 libdbi-perl
  libmp4v2-0 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libfftw3-3
  libxine1-bin libplrpc-perl libxine1-ffmpeg libxcb-shape0 libtunepimp5
  libifp4 libxine1-plugins libxcb-shm0 libnjb5 libofa0 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  cupsys
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 174441 files and directories currently installed.)
Removing cupsys ...
 * Stopping Common Unix Printing System: cupsd                           [ OK ]
```

then 

```
sudo apt-get -f install
```

gave me 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libnet-daemon-perl libxine1-misc-plugins libxcb-xv0 libdbi-perl
  libmp4v2-0 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libfftw3-3
  libxine1-bin libplrpc-perl libxine1-ffmpeg libxcb-shape0 libtunepimp5
  libifp4 libxine1-plugins libxcb-shm0 libnjb5 libofa0 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
sudo apt-get install cupsys
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libnet-daemon-perl libxine1-misc-plugins libxcb-xv0 libdbi-perl
  libmp4v2-0 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libfftw3-3
  libxine1-bin libplrpc-perl libxine1-ffmpeg libxcb-shape0 libtunepimp5
  libifp4 libxine1-plugins libxcb-shm0 libnjb5 libofa0 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  cups-pdf cupsys-driver-gutenprint foomatic-filters-ppds hplip xpdf-korean
  xpdf-japanese xpdf-chinese-traditional xpdf-chinese-simplified
Recommended packages:
  avahi-utils
The following NEW packages will be installed
  cupsys
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1863kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy-updates/main cupsys 1.3.7-1ubuntu3.3 [1863kB]
Fetched 1863kB in 7s (252kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package cupsys.
(Reading database ... 172891 files and directories currently installed.)
Unpacking cupsys (from .../cupsys_1.3.7-1ubuntu3.3_i386.deb) ...
Setting up cupsys (1.3.7-1ubuntu3.3) ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd                           [ OK ] 
```

finally

```
sudo ln -s ../init.d/cupsys s19cupsys
ls -al
```

showed s19cupsys -> ../init.d/cupsys in the list.

So, it looks like it worked... If not, I'll keep you posted.

And THANKS!!

PS. Can't find the "thank you" button - where'd it go?

Good question :p.  Either way, its of no real concern to me.  By the way, I found that post because I googled "exit status 102 dpkg" as it was shown in the error messages here

```

 subprocess post-installation script returned error exit status 102

```

Just for future reference ;).  I probably should have googled that from the start :p.

---


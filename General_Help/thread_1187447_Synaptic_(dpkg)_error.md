---
title: "Synaptic (dpkg) error"
date: 2009-06-14
forum: General Help
---

### Post by Eredeath on 2009-06-14
I am getting an error when trying to use synaptic or the update manager. I'm getting a popup screen that says:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So following the instructions I  run 'sudo dpkg --configure -a' and get this:
```

Setting up libc6 (2.9-4ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Aborted
dpkg: subprocess post-installation script returned error exit status 134
```
Clearly this didn't help anything.
Any ideas?

---

### Post by skyjacker on 2009-06-14
> **Eredeath said:**
> I am getting an error when trying to use synaptic or the update manager. I'm getting a popup screen that says:



So following the instructions I  run 'sudo dpkg --configure -a' and get this:
```

Setting up libc6 (2.9-4ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Aborted
dpkg: subprocess post-installation script returned error exit status 134
```
Clearly this didn't help anything.
Any ideas?I had a similar problem (but not the exact same one), and I finally removed synaptic```
sudo apt-get remove synaptic
```. Then re-install it ```
sudo apt-get install synaptic
```

---

### Post by Eredeath on 2009-06-14
it must be a problem with dpkg, apt-get isn't working. I get the same error as when i try to start synaptic. 

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

---

### Post by fooman on 2009-06-14
open a terminal (applications > accessories > terminal) and type or copy/paste the following into it:

```
sudo dpkg --configure -a
```then press enter,  followed by your password when prompted.

then run these:

```
sudo apt-get update
``````
sudo apt-get upgrade
```EDIT:  oops,  sorry...forgot one more:

```
 sudo apt-get -f install
```hope that helps.

---

### Post by Eredeath on 2009-06-14
As i said earlier, apt-get doesn't work... 
this is what i get when i do as you ask (see attachment)

---

### Post by camper365 on 2009-06-14
Can you make the image a little bigger, I can't read that (and if I get a magnifying glass, all I see are the red blue and green dots of the monitor:p).

It looks like apt-get got interrupted while it was working with libc6. I think at this point the best you can do is reinstall. I know that when I was trying to upgrade to karmic, I got a lot of problems with libc6 and libstdc++. Good luck.

btw, this is my 200th post :).

---

### Post by Eredeath on 2009-06-14
> **camper365 said:**
> Can you make the image a little bigger, I can't read that (and if I get a magnifying glass, all I see are the red blue and green dots of the monitor:p).

It looks like apt-get got interrupted while it was working with libc6. I think at this point the best you can do is reinstall. I know that when I was trying to upgrade to karmic, I got a lot of problems with libc6 and libstdc++. Good luck.

btw, this is my 200th post :).

congrats on the 200th post :)

do you know how i can uninstall any of this without using dpkg? that's where i'm getting hung up.

---

### Post by camper365 on 2009-06-15
libstdc++6 is /usr/lib/libstc++.so.6 and libc6 is /lib/libc.so.6

I am running Karmic right now, so I can't post my files, but if you boot from a livecd and mount your root directory, you can copy the one from the livecd and put that on your hard drive and it should work. I have not actually tried that yet though. I just reinstalled.

You don't want to uninstall, you want to reinstall, if you don't have a libc6 installed your computer will probably not work at all.

---

### Post by juangf7 on 2009-06-16
I have a problem when installing new programmes:

E: Sub-process /usr/bin/dpkg returned an error code (1)

the whole report is:

eading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following partially installed packages will be configured:
  apturl evince evolution evolution-common evolution-documentation-en evolution-plugins gnome-about gnome-app-install 
  gnome-applets-data gnome-desktop-data gnome-system-tools synaptic ubuntu-docs update-manager 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up gnome-applets-data (2.26.1-0ubuntu1) ...
Segmentation fault
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ubuntu-docs (9.04.10) ...
Segmentation fault
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 139
Setting up synaptic (0.62.5ubuntu3) ...
Segmentation fault
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
Setting up evince (2.26.1-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Segmentation fault
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.26.1-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.26.1-0ubuntu2); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.26.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-desktop-data (1:2.26.1-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                             Segmentation fault
dpkg: error processing gnome-desktop-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-about:
 gnome-about depends on gnome-desktop-data (= 1:2.26.1-0ubuntu2); however:
  Package gnome-desktop-data is not configured yet.
dpkg: error processing gnome-about (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
Setting up evolution-documentation-en (2.26.1-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                             Segmentation fault
dpkg: error processing evolution-documentation-en (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-tools (2.22.2-0ubuntu4) ...
No apport report written because MaxReports is reached already
                                                              Segmentation fault
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 gnome-applets-data

How I sort it out this problem?

---

### Post by Soul-Sing on 2009-06-16
Is it possible to start synaptic package manager? Filter on broken ( evolution) packages.
otherwise ```
sudo apt-get -f install
```
direct after the error via the terminal.

---

### Post by juangf7 on 2009-06-16
I doesn't work

I wrote in terminal:

usuario1@usuario1-laptop:~$ sudo apt-get -f install

but:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-applets-data (2.26.1-0ubuntu1) ...
Segmentation fault
dpkg: error processing gnome-applets-data (--configure):

Etc...

No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 gnome-applets-data
 ubuntu-docs
 synaptic
 gnome-app-install
 apturl
 evince
 evolution-common
 evolution
 evolution-plugins
 gnome-desktop-data
 gnome-about
 update-manager
 evolution-documentation-en
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't know how to solve this problem :(

---

### Post by Soul-Sing on 2009-06-16
Could you take look at your harddisk: system: systemmonitor.
It seems like a full harddisk.....
or:  ```
sudo fdisk -l
```

---

### Post by juangf7 on 2009-06-16
usuario1@usuario1-laptop:~$ sudo fdisk -l
[sudo] password for usuario1: 

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ae59edc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         851     6835626    5  Extended
/dev/sda2             852         981     1044225   82  Linux swap / Solaris
/dev/sda5               1         851     6835594+  83  Linux
usuario1@usuario1-laptop:~$ 

Thanks Leoquant!

---

### Post by Soul-Sing on 2009-06-16
And to be sure: place a picture here: system: systemmonitor: "disks¨.

---

### Post by juangf7 on 2009-06-16
[http://www.facebook.com/album.php?aid=118404&id=617418627&l=e44e816ccc](http://www.facebook.com/album.php?aid=118404&id=617418627&l=e44e816ccc)

---

### Post by Soul-Sing on 2009-06-16
sorry, my fault: a picture of the file system....
to be 100% sure. So again systemmonitor: file system.
But i'am almost sure it is a full harddisk.

---

### Post by juangf7 on 2009-06-16
the second pic is about the filesystem, the hard disk is not full (only 42%)

---

### Post by Soul-Sing on 2009-06-16
Thx. Maybe someone should take a look at this problem.

---

### Post by camper365 on 2009-06-18
It looks like it is seg faulting after processing every package. I ma not sure exactly how aptitude works, but I think it calls dpkg to install or remove, etc. every package.
It looks like your dpkg is broken. What you can probably do is download the source code to dpkg and compile it, then use aptitude again.
Instructions for compiling will be in the INSTALL file of the tarball. When you download it, open it with the archive manager and extract it.

---


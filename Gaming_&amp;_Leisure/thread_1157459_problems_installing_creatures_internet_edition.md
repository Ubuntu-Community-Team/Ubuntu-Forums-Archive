---
title: "problems installing creatures internet edition"
date: 2009-05-12
forum: Gaming &amp; Leisure
---

### Post by bunkum on 2009-05-12
[LEFT]Hello,
I'm new to Ubuntu and have installed Version 8.10 (ibex) on my very old Laptop. I wanted to install creatures internet edition but it failed and I don't know what to do now. This is for troubleshooting:

[CENTER]**1st I downloaded the package "dockingstation.run"**

**2nd I activated it with sh dockingstation.run**
_It failed for the first time saying:_
[/CENTER]


Verifying archive integrity... All good.
Uncompressing Creatures: Docking Station............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
./dstation-install: line 83: type: creatures3: not found

Docking Station InstallBlast
----------------------------

Installing off filesystem /tmp/selfgz9613/.

Checking for updates...

Current linux_x86_glibc21 build: linux_x86_glibc21_64
Latest linux_x86_glibc21 build: linux_x86_glibc21_64
Nothing to update for linux_x86_glibc21

Making 'dockingstation' executable link...

Current global build:
Latest global build: dsbuild 195
Updating to latest version
Updating global data to latest version

Getting files from dsbuild 195/global/ to /usr/local/games/dockingstation
Converting images to local format                                               
./imageconvert: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

[/LEFT]
[CENTER]**3rd I had to set a password for root (as it is not set by default) to change to SU**

**4th I installed it again using sh dockingstation.run**

**_5th it failed again and said:_**
[/CENTER]

Verifying archive integrity... All good.
Uncompressing Creatures: Docking Station.
./dstation-install: line 83: type: creatures3: not found

Docking Station InstallBlast
----------------------------

Installing off filesystem /tmp/selfgz9613/.

Checking for updates...

Current linux_x86_glibc21 build: linux_x86_glibc21_64
Latest linux_x86_glibc21 build: linux_x86_glibc21_64
Nothing to update for linux_x86_glibc21

Making 'dockingstation' executable link...

Current global build:
Latest global build: dsbuild 195
Updating to latest version
Updating global data to latest version

Getting files from dsbuild 195/global/ to /usr/local/games/dockingstation
Converting images to local format                                               
./imageconvert: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Amof on 2009-05-12
```
./imageconvert: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory 
```


Fairly sure that means you are missing a library. 

This should fix it. 

```
sudo apt-get install libgtk1.2
```

---

### Post by bunkum on 2009-05-13
I did what you recommended but this message
[I]
Updating linux_x86_glibc21 to latest version

Getting files from ports/linux_x86_glibc21_64/ to /usr/local/games/dockingstation
Finished linux_x86_glibc21 update                                                 
Relaunching new version of script
trap: 119: SIGINT: bad trap[/I]

still aborts the installation.

---

### Post by bunkum on 2009-05-13
Sorry I just saw that I didn't quote the first error correctly. It is definitely the one I posted just now.

---

### Post by thedaemon on 2009-05-31
I have the same problem bunkum. :(

---

### Post by Ziphilt on 2009-06-01
> **bunkum said:**
> I did what you recommended but this message
[I]
Updating linux_x86_glibc21 to latest version

Getting files from ports/linux_x86_glibc21_64/ to /usr/local/games/dockingstation
Finished linux_x86_glibc21 update                                                 
Relaunching new version of script
trap: 119: SIGINT: bad trap[/I]

still aborts the installation.

Hopefully this webpage will help you:
[http://creatures.wikia.com/wiki/Linux_Docking_Station_Instructions](http://creatures.wikia.com/wiki/Linux_Docking_Station_Instructions)

That page also tells you about how you need libgtk1.2, but you already know that.

---

### Post by calvimm on 2009-06-27
hey
i am having problems installing as well. i followed the instructions on the linux docking station wiki but i keep getting this message:

Installing off filesystem /home/calvimmm/dockingstation_195_64/.

Checking for updates...

Current linux_x86_glibc21 build: linux_x86_glibc21_64
Latest linux_x86_glibc21 build: linux_x86_glibc21_64
Nothing to update for linux_x86_glibc21

Making 'dockingstation' executable link...

Current global build:
Latest global build: dsbuild 195
Updating to latest version
Updating global data to latest version

Getting files from dsbuild 195/global/ to /usr/local/games/dockingstation
Converting images to local format                                               
Finished global update

Rerunning to check for network updates
trap: 119: SIGINT: bad trap


help!

---

### Post by ncweber on 2009-09-13
This still isn't working.  Has anyone been able to solve this?  I've been able to open an su terminal and navigate to the install file [ /usr/local/games/dockingstation/dstation-install] and run it in the su terminal.  Everything seems to run fine, but then there doesn't seem to be any way to start the program.  It says to type "dockingstation nocheck".  Type it where?  People need to be more specific when giving instructions.

---


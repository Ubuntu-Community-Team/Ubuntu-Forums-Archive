---
title: "How to remove apps from Show Applications which don't show as &quot;installed&quot;"
date: 2024-11-14
forum: Desktop Environments
---

### Post by dpan622 on 2024-11-14
USER:  very much a novice

RE: Prepping to create an ISO image (once I figure out how)

Version:  Ubuntu 20.04

I've removed from the system apps I know I'll never use via Show Applications, details, and uninstalling these.
WHY?  I assume it frees up storage space, system resources, and will make the ISO system image I'd like to create smaller.
There are three items listed in "Show Applications" which examining "details" show as "not installed", however they still run when clicked!

Q: How and where do I find and remove these pesky apps dug in like ticks?
I've toyed with "which" and "whereis" and simply haven't found a guide detailed enough for a novice to follow.

GOAL:    - REMOVE listed apps from Show Applications which are not installed; uninstalling if necessary
        - Sudoku
        - Mahjonng
        - Mines

---

### Post by Dennis N on 2024-11-14
Run in terminal:
```
sudo apt remove gnome-mahjongg gnome-sudoku gnome-mines
```
That should do it.

---

### Post by grahammechanical on 2024-11-14
> Version:  Ubuntu 20.04

Support for Ubuntu 20.04 ends April 2025. Ubuntu 24.04 is Long Term Support (LTS) and it does not include any games. The installer gives us two Options. 

1) Essentials - Web browser and system utilities. That is all. Not even a software centre application.
2) Extended Selection - an offline friendly selection of office tools, utilities and web browser. And no games.

The Ubuntu 24.04 ISO image is 6.2 GB. ISO images have been getting larger over the last 4 years. And Ubuntu does not have a mini ISO any more.

Regards

---

### Post by dpan622 on 2024-11-16
> **Dennis N said:**
> Run in terminal:
```
sudo apt remove gnome-mahjongg gnome-sudoku gnome-mines
```
That should do it.

Thank you Dennis N, those apps are [B]no longer listed in Show Applications!
[/B]Amazing the simple solutions that experience nets you...

**FOLLOW-UP Q**: Are the programs gone from the system, or only their access point or symlink in the Show Applications?
With "$ sudo apt autoremove" I suspect so... confirmation of my suspicion would just be grand.

Here is what that operation netted (for those that follow and wish to see the results before trying the same):

[user@computer-name]:~$ sudo apt remove gnome-mahjongg gnome-sudoku gnome-mines
[sudo] password for [user]: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnome-games-support-1-3 libgnome-games-support-common libqqwing2v5
**Use 'sudo apt autoremove' to remove them.**
The following packages will be REMOVED:
  gnome-mahjongg gnome-mines gnome-sudoku
0 upgraded, 0 newly installed, 3 to remove and 3 not upgraded.
After this operation, 5,186 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 177393 files and directories currently installed.)
Removing gnome-mahjongg (1:3.36.1-1) ...
Removing gnome-mines (1:3.36.0-1) ...
Removing gnome-sudoku (1:3.36.0-1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.6-1~ubuntu20.04.7) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
[user@computer-name]:~$ **sudo apt autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libgnome-games-support-1-3 libgnome-games-support-common libqqwing2v5
0 upgraded, 0 newly installed, 3 to remove and 3 not upgraded.
After this operation, 215 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 176279 files and directories currently installed.)
Removing libgnome-games-support-1-3:amd64 (1.6.1-1) ...
Removing libgnome-games-support-common (1.6.1-1) ...
Removing libqqwing2v5:amd64 (1.3.4-1.1build1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.16) ...
[user@computer-name]:~$

---

### Post by dpan622 on 2024-11-16
Thanks for the suggestion grahammechanical.

I tried a dual boot system last go-round with Ubuntu and Windows and ended up not being able to access my Ubuntu boot drive; a problem I neither had the experience nor time to address in 2021.  At this turn, thoroughly disgusted with Windows, I've dumped it altogether and am running Ubuntu/Linux exclusively.  (What joy it is to be able to say that; never going back.)

That said... when I installed this time round, I first tried the latest update 24.04 with the minimum install; it proved problematic for my limited knowledge of running and managing a Linux system.  With all the battles I've fought getting this install running as it is, I can't even remember what those issues were.  I've had less issues running the 20.04 version... but still having issues.

By comparison, Windows was taking several minutes to boot and let me into my computer interface, as well as constantly running items in the background calling upon system resources.  Ubuntu/Linux boots in a matter of seconds by comparison.  It takes me longer to type in my password than it takes Ubuntu to boot.  Using "Mission Center" to monitor the system, I'm very pleased with how light the OS is running and using system resources.  I'm amazed... ten-year old hardware running like brand new.

Presently, I'm fighting the printer driver install war... Its not going well.  ;-D

---

### Post by Holger_Gehrke on 2024-11-16
> **dpan622 said:**
> Thank you Dennis N, those apps are [B]no longer listed in Show Applications!
[/B]Amazing the simple solutions that experience nets you...

**FOLLOW-UP Q**: Are the programs gone from the system, or only their access point or symlink in the Show Applications?
With "$ sudo apt autoremove" I suspect so... confirmation of my suspicion would just be grand.


'apt' and the Debian package system it administers are very granular. So you removed the games but they depended on other packages. Installed packages can have two states - manually installed or automatically installed because other packages need them. 'apt autoremove' removes packages that were automatically installed because other packages needed them which aren't needed anymore.

If your final goal is to create a new image without any programs you don't want / need, then you're going about it somewhat wrong. Creating an image is a rather involved process and you can't make an image of your current running system. You need a running system inside of which you build a new system which you will then create the image from. I haven't done it myself since it only makes sense to do so if you have to install a lot of systems and want to have a set of packages in the images that are right for the machines you are installing on - the typical scenario for this would be deployment of Ubuntu Desktops at a company. A tutorial which seems to describe it quite well can be found at [https://mvallim.github.io/live-custom-ubuntu-from-scratch/](https://mvallim.github.io/live-custom-ubuntu-from-scratch/)

Holger

---


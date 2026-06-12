---
title: "Desktop Restoration"
date: 2017-05-05
forum: Desktop Environments
---

### Post by rolfUser on 2017-05-05
I turned on my computer recently (Ubuntu 16.04) and noticed the Ubuntu emblem appear larger than normal, twice as large. When the desktop loaded up, the icons on the unity launcher were much larger than normal. Windows that open up always take up the whole screen and I find it very difficult to navigate this way.

I learned previously that input:
```
sudo xrandr -q
``` provides the name of your monitor. In my case, it is VGA-0.

This time, the output was:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm         640*480                73.00*

```

Under System Settings>Displays, I cannot get the unity icon size to adjust because that option is too far below in the window to even be viewed.
If this happens, how can I restore the desktop?

---

### Post by ajgreeny on 2017-05-05
As you are using 16.04 I wonder if you have been bitten by the problem of an update to 16.04 giving you **linux-image-4.4.0-77-generic** but not also installing the **linux-image-extra** and **linux-headers** packages of that same version that it should have done.

This caused a big problem for many users who lost wifi, but in some cases users also lost their proprietary graphics drivers.  

Let's see the output of ```
dpkg -l linux* | grep 4.4.0-77
``` in terminal to see if this is your situation.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

If it is, a second update using terminal commands ```
sudo apt-get update
sudo apt-get dist-upgrade
``` should now add those missing packages and put things right for you.

---

### Post by Autodave on 2017-05-06
And don't forget that it might not be an OS problem at all.  Assuming that you are using a VGA cable, make sure it is tight on both ends. If tight and you have access to another cable, try that, too.

---

### Post by rolfUser on 2017-05-08
I am using a VGA cable. It's connected to my Insignia HDTV. I can watch TV and use my computer on this thing. Now that I'm back, I will have the output ready for you shortly. Thank you.

---

### Post by rolfUser on 2017-05-08
> **ajgreeny said:**
> As you are using 16.04 I wonder if you have been bitten by the problem of an update to 16.04 giving you **linux-image-4.4.0-77-generic** but not also installing the **linux-image-extra** and **linux-headers** packages of that same version that it should have done.

This caused a big problem for many users who lost wifi, but in some cases users also lost their proprietary graphics drivers.  

Let's see the output of ```
dpkg -l linux* | grep 4.4.0-77
``` in terminal to see if this is your situation.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

If it is, a second update using terminal commands ```
sudo apt-get update
sudo apt-get dist-upgrade
``` should now add those missing packages and put things right for you.


input:
```
dpkg -l linux* | grep 4.4.0-77
```

output:
```
ii  linux-headers-4.4.0-77             4.4.0-77.98              all          Header files related to Linuxkernel version 4.4.0ii  linux-headers-4.4.0-77-generic     4.4.0-77.98              amd64        Linux kernel headers forversion 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-77-generic       4.4.0-77.98              amd64        Linux kernel image for version4.4.0 on 64 bit x86 SMP
```

As for upgrading the distro to 16.10, that looks like I will need a internet connection. That will not work. My PC is dual-booted with Ubuntu 16.04 and Windows 10. Internet works fine on Windows, but no internet at all since this problem started on Ubuntu.

---

### Post by ajgreeny on 2017-05-09
Try booting to the previous kernel from grub which may give you back your wifi, then run the upgrade/update commands again.

You appear to be missing the linux-image-extra-4.4.0-77-generic which is one of the missing required packages needed for some wifi drivers.

PS:
The command ```
sudo apt-get dist-upgrade
``` does not move you from 16.04 to 16.10 but simply makes sure that new kernel versions are installed when they are available, so don't imagine it will do anything you don't want.

---

### Post by rolfUser on 2017-05-09
> **ajgreeny said:**
> Try booting to the previous kernel from grub which may give you back your wifi, then run the upgrade/update commands again.

You appear to be missing the linux-image-extra-4.4.0-77-generic which is one of the missing required packages needed for some wifi drivers.

PS:
The command ```
sudo apt-get dist-upgrade
``` does not move you from 16.04 to 16.10 but simply makes sure that new kernel versions are installed when they are available, so don't imagine it will do anything you don't want.

Okay.Before I move forward...
What you mean by "previous kernel" is that I should download (from Windows 10) and install (transfer the ISO from my USB drive) Ubuntu 15.10? 
Before 16.04, I was using 14.04. 
If there is a tutorial for what you suggest, please share.

---

### Post by litlesam on 2017-05-09
> **rolfUser said:**
> Okay.Before I move forward...
What you mean by "previous kernel" is that I should download (from Windows 10) and install (transfer the ISO from my USB drive) Ubuntu 15.10? 
Before 16.04, I was using 14.04. 
If there is a tutorial for what you suggest, please share.

I believe the person asked you to select advance options on boot up from your Grub menu and select the previous kernel that worked before you started having problems.

---

### Post by ajgreeny on 2017-05-10
> **rolfUser said:**
> Okay.Before I move forward...
What you mean by "previous kernel" is that I should download (from Windows 10) and install (transfer the ISO from my USB drive) Ubuntu 15.10? 
Before 16.04, I was using 14.04. 
If there is a tutorial for what you suggest, please share.
At the grub menu (you may need hold **shift** at power-on if you do not usually see the menu) go to Advanced and from that use one of the other kernels that are usually shown there; you may have an entry for 4.4.0-75, or maybe some other version, and boot to that.

If the GUI and wifi work fine with that kernel try updating again with those two commands.

---

### Post by rolfUser on 2017-05-10
From the grub menu on startup, I went into advanced options and selected **4.4.0-75-generic**. Sure enough, the system booted up like nothing had happened. The two arrows on the top right of the screen indicated a steady signal and sure enough, Internet was working.
input:
```
sudo apt-get update
```
output:
```
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11:Resource temporarily unavailable)

E: Unable to lock directory /var/lib/apt/lists/
```
Pretty odd to me, this output. So I chose to report here first before the next line of code you suggested.

---

### Post by Bashing-om on 2017-05-10
rolfUser; Hello;

As I pass by :)
> 
E: Could not get lock /var/lib/apt/lists/lock - open (11:Resource temporarily unavailable)

generally, another instance of the package manager is running . Say like "unattended-upgrades" running in the background.

Try the terminal upgrade again at this time and advise.

[INDENT][INDENT]it is all a process
[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-11
> **Bashing-om said:**
> rolfUser; Hello;

As I pass by :)

generally, another instance of the package manager is running . Say like "unattended-upgrades" running in the background.

Try the terminal upgrade again at this time and advise.[INDENT][INDENT]it is all a process
[/INDENT]
[/INDENT]

I think you were right. I tried again from **4.4.0-75-generic**:
input:
```
sudo apt-get update
```
output:
```
Hit:1 http://download.virtualbox.org/virtualbox/debian xenial InReleaseHit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease    
Hit:6 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial InRelease         
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Hit:8 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease 
Hit:9 http://ppa.launchpad.net/ozmartian/apps/ubuntu xenial InRelease          
Hit:10 http://ppa.launchpad.net/videolan/master-daily/ubuntu xenial InRelease
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [530 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.6 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [45.7 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [515 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [298 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [193 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [461 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [447 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [8,932 B]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [7,724 B]
Get:25 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:26 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Fetched 3,291 kB in 8s (368 kB/s)                                              
Reading package lists... Done
```

---

### Post by Bashing-om on 2017-05-11
rolfUser; Ho Kay !

And part 2 of ajgreeny's instruction :
```

sudo apt-get dist-upgrade

```
does that install the missing kernel packages ?

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]could be not so yes ....
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-11
Take 2:
input:
```
sudo apt-get update
```
output:
```
Hit:1 http://download.virtualbox.org/virtualbox/debian xenial InReleaseHit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease    
Hit:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease    
Hit:7 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial InRelease
Hit:8 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/ozmartian/apps/ubuntu xenial InRelease
Hit:10 http://ppa.launchpad.net/videolan/master-daily/ubuntu xenial InRelease
Reading package lists... Done
```
input:
```
sudo apt-get dist-upgrade
```
output:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libopenshot-audio5 linux-image-extra-4.4.0-77-generic
The following packages will be upgraded:
  activity-log-manager activity-log-manager-control-center
  chromium-codecs-ffmpeg-extra firefox firefox-locale-en flashplugin-installer
  fonts-opensymbol gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0
  libfreetype6 libfreetype6:i386 libjavascriptcoregtk-4.0-18 libopenshot11
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk2 libreoffice-impress libreoffice-math libreoffice-pdfimport
  libreoffice-style-elementary libreoffice-style-galaxy
  libreoffice-style-tango libreoffice-writer librtmp1 libwebkit2gtk-4.0-37
  libwebkit2gtk-4.0-37-gtk2 libxnvctrl0 linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev login logrotate nvidia-settings
  openjdk-8-jre openjdk-8-jre-headless openshot-qt openssh-client passwd
  python3-openshot python3-uno rtmpdump ssh-askpass-gnome unattended-upgrades
  uno-libs3 ure vidcutter zlib1g zlib1g:i386 zlib1g-dev
55 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 281 MB of archives.
After this operation, 96.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 login amd64 1:4.2-3.1ubuntu5.2 [305 kB]
Get:2 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 uno-libs3 amd64 5.3.3~rc2-0ubuntu0.16.04.1~lo0 [883 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 chromium-codecs-ffmpeg-extra amd64 58.0.3029.96-0ubuntu0.16.04.1279 [999 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 zlib1g-dev amd64 1:1.2.8.dfsg-2ubuntu4.1 [168 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4.1 [52.1 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 zlib1g amd64 1:1.2.8.dfsg-2ubuntu4.1 [51.2 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libfreetype6 i386 2.6.1-0.1ubuntu2.3 [330 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libfreetype6 amd64 2.6.1-0.1ubuntu2.3 [316 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 openjdk-8-jre amd64 8u131-b11-0ubuntu1.16.04.2 [69.3 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 openjdk-8-jre-headless amd64 8u131-b11-0ubuntu1.16.04.2 [27.0 MB]
Get:11 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 ure amd64 5.3.3~rc2-0ubuntu0.16.04.1~lo0 [1,746 kB]
Get:12 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-calc amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [6,820 kB]
Get:13 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-impress amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [931 kB]
Get:14 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-draw amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [3,320 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 passwd amd64 1:4.2-3.1ubuntu5.2 [780 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 logrotate amd64 3.8.7-2ubuntu2.16.04.1 [37.8 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 librtmp1 amd64 2.4+20151223.gitfa8646d-1ubuntu0.1 [54.4 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 openssh-client amd64 1:7.2p2-4ubuntu2.2 [587 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 activity-log-manager amd64 0.9.7-0ubuntu23.16.04.1 [101 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 activity-log-manager-control-center all 0.9.7-0ubuntu23.16.04.1 [1,696 B]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox amd64 53.0.2+build1-0ubuntu0.16.04.2 [46.4 MB]
Get:22 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-gnome amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [59.5 kB]
Get:23 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-gtk2 amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [205 kB]
Get:24 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-style-tango all 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [1,299 kB]
Get:25 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-style-elementary all 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [1,449 kB]
Get:26 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-style-galaxy all 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [1,561 kB]
Get:27 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-common all 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [22.6 MB]
Get:28 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox-locale-en amd64 53.0.2+build1-0ubuntu0.16.04.2 [665 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 flashplugin-installer amd64 25.0.0.171ubuntu0.16.04.1 [6,846 B]
Get:30 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwebkit2gtk-4.0-37-gtk2 amd64 2.16.1-0ubuntu0.16.04.2 [8,637 kB]
Get:31 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-pdfimport amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [183 kB]
Get:32 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 python3-uno amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [196 kB]
Get:33 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-base-core amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [715 kB]
Get:34 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-math amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [388 kB]
Get:35 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-avmedia-backend-gstreamer amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [24.0 kB]
Get:36 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-writer amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [8,227 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwebkit2gtk-4.0-37 amd64 2.16.1-0ubuntu0.16.04.2 [10.6 MB]
Get:38 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libjavascriptcoregtk-4.0-18 amd64 2.16.1-0ubuntu0.16.04.2 [3,949 kB]
Get:39 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-core amd64 1:5.3.3~rc2-0ubuntu0.16.04.1~lo0 [34.1 MB]
Get:40 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gir1.2-webkit2-4.0 amd64 2.16.1-0ubuntu0.16.04.2 [67.4 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gir1.2-javascriptcoregtk-4.0 amd64 2.16.1-0ubuntu0.16.04.2 [21.7 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-77-generic amd64 4.4.0-77.98 [35.9 MB]
Get:43 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.77.83 [1,786 B]
Get:44 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.77.83 [2,306 B]
Get:45 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.77.83 [2,278 B]
Get:46 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-77.98 [836 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 ssh-askpass-gnome amd64 1:7.2p2-4ubuntu2.2 [14.2 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unattended-upgrades all 0.90ubuntu0.5 [32.7 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 rtmpdump amd64 2.4+20151223.gitfa8646d-1ubuntu0.1 [41.6 kB]
Get:50 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 fonts-opensymbol all 2:102.10+LibO5.3.3~rc2-0ubuntu0.16.04.1~lo0 [278 kB]
Get:51 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial/main amd64 libopenshot-audio5 amd64 0.1.4+0+50+111+201705110801~ubuntu16.04.1 [1,464 kB]
Get:52 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial/main amd64 libopenshot11 amd64 0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1 [286 kB]
Get:53 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 libxnvctrl0 amd64 381.22-0ubuntu0~gpu16.04.1 [17.7 kB]
Get:54 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 nvidia-settings amd64 381.22-0ubuntu0~gpu16.04.1 [885 kB]
Get:55 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial/main amd64 python3-openshot amd64 0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1 [300 kB]
Get:56 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial/main amd64 openshot-qt all 2.3.2+0+798+110+201705110701~ubuntu16.04.1 [53.2 MB]
Get:57 http://ppa.launchpad.net/ozmartian/apps/ubuntu xenial/main amd64 vidcutter all 3.2.0~201705111415~ubuntu16.04.1 [1,826 kB]
Fetched 281 MB in 15min 7s (310 kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 724272 files and directories currently installed.)
Preparing to unpack .../login_1%3a4.2-3.1ubuntu5.2_amd64.deb ...
Unpacking login (1:4.2-3.1ubuntu5.2) over (1:4.2-3.1ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up login (1:4.2-3.1ubuntu5.2) ...
(Reading database ... 724272 files and directories currently installed.)
Preparing to unpack .../chromium-codecs-ffmpeg-extra_58.0.3029.96-0ubuntu0.16.04.1279_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (58.0.3029.96-0ubuntu0.16.04.1279) over (58.0.3029.81-0ubuntu0.16.04.1277) ...
Preparing to unpack .../uno-libs3_5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking uno-libs3 (5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../ure_5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking ure (5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../zlib1g-dev_1%3a1.2.8.dfsg-2ubuntu4.1_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.8.dfsg-2ubuntu4.1) over (1:1.2.8.dfsg-2ubuntu4) ...
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4.1_amd64.deb ...
De-configuring zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Unpacking zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4.1) over (1:1.2.8.dfsg-2ubuntu4) ...
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4.1_i386.deb ...
Unpacking zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4.1) over (1:1.2.8.dfsg-2ubuntu4) ...
Preparing to unpack .../libreoffice-calc_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-calc (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-impress_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-impress (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-draw_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-draw (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-gnome_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-gnome (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-gtk2_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-gtk2 (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-style-tango_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_all.deb ...
Unpacking libreoffice-style-tango (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-style-elementary_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_all.deb ...
Unpacking libreoffice-style-elementary (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-style-galaxy_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_all.deb ...
Unpacking libreoffice-style-galaxy (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-common_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_all.deb ...
Unpacking libreoffice-common (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-pdfimport_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-pdfimport (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../python3-uno_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking python3-uno (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-base-core_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-base-core (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-math_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-math (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-avmedia-backend-gstreamer_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-avmedia-backend-gstreamer (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-writer_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-writer (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libreoffice-core_1%3a5.3.3~rc2-0ubuntu0.16.04.1~lo0_amd64.deb ...
Unpacking libreoffice-core (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (1:5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../fonts-opensymbol_2%3a102.10+LibO5.3.3~rc2-0ubuntu0.16.04.1~lo0_all.deb ...
Unpacking fonts-opensymbol (2:102.10+LibO5.3.3~rc2-0ubuntu0.16.04.1~lo0) over (2:102.10+LibO5.3.2~rc2-0ubuntu1~xenial0) ...
Preparing to unpack .../libfreetype6_2.6.1-0.1ubuntu2.3_amd64.deb ...
De-configuring libfreetype6:i386 (2.6.1-0.1ubuntu2.2) ...
Unpacking libfreetype6:amd64 (2.6.1-0.1ubuntu2.3) over (2.6.1-0.1ubuntu2.2) ...
Preparing to unpack .../libfreetype6_2.6.1-0.1ubuntu2.3_i386.deb ...
Unpacking libfreetype6:i386 (2.6.1-0.1ubuntu2.3) over (2.6.1-0.1ubuntu2.2) ...
Preparing to unpack .../openjdk-8-jre_8u131-b11-0ubuntu1.16.04.2_amd64.deb ...
Unpacking openjdk-8-jre:amd64 (8u131-b11-0ubuntu1.16.04.2) over (8u121-b13-0ubuntu1.16.04.2) ...
Preparing to unpack .../openjdk-8-jre-headless_8u131-b11-0ubuntu1.16.04.2_amd64.deb ...
Unpacking openjdk-8-jre-headless:amd64 (8u131-b11-0ubuntu1.16.04.2) over (8u121-b13-0ubuntu1.16.04.2) ...
Preparing to unpack .../passwd_1%3a4.2-3.1ubuntu5.2_amd64.deb ...
Unpacking passwd (1:4.2-3.1ubuntu5.2) over (1:4.2-3.1ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for gnome-icon-theme (3.12.0-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up passwd (1:4.2-3.1ubuntu5.2) ...
(Reading database ... 724279 files and directories currently installed.)
Preparing to unpack .../logrotate_3.8.7-2ubuntu2.16.04.1_amd64.deb ...
Unpacking logrotate (3.8.7-2ubuntu2.16.04.1) over (3.8.7-2ubuntu2) ...
Preparing to unpack .../librtmp1_2.4+20151223.gitfa8646d-1ubuntu0.1_amd64.deb ...
Unpacking librtmp1:amd64 (2.4+20151223.gitfa8646d-1ubuntu0.1) over (2.4+20151223.gitfa8646d-1build1) ...
Preparing to unpack .../openssh-client_1%3a7.2p2-4ubuntu2.2_amd64.deb ...
Unpacking openssh-client (1:7.2p2-4ubuntu2.2) over (1:7.2p2-4ubuntu2.1) ...
Preparing to unpack .../activity-log-manager_0.9.7-0ubuntu23.16.04.1_amd64.deb ...
Unpacking activity-log-manager (0.9.7-0ubuntu23.16.04.1) over (0.9.7-0ubuntu23) ...
Preparing to unpack .../activity-log-manager-control-center_0.9.7-0ubuntu23.16.04.1_all.deb ...
Unpacking activity-log-manager-control-center (0.9.7-0ubuntu23.16.04.1) over (0.9.7-0ubuntu23) ...
Preparing to unpack .../firefox_53.0.2+build1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox (53.0.2+build1-0ubuntu0.16.04.2) over (53.0+build6-0ubuntu0.16.04.1) ...
Preparing to unpack .../firefox-locale-en_53.0.2+build1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox-locale-en (53.0.2+build1-0ubuntu0.16.04.2) over (53.0+build6-0ubuntu0.16.04.1) ...
Preparing to unpack .../flashplugin-installer_25.0.0.171ubuntu0.16.04.1_amd64.deb ...
Unpacking flashplugin-installer (25.0.0.171ubuntu0.16.04.1) over (25.0.0.148ubuntu0.16.04.1) ...
Preparing to unpack .../libwebkit2gtk-4.0-37-gtk2_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37-gtk2:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../libwebkit2gtk-4.0-37_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../libjavascriptcoregtk-4.0-18_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libjavascriptcoregtk-4.0-18:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../gir1.2-webkit2-4.0_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking gir1.2-webkit2-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../gir1.2-javascriptcoregtk-4.0_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking gir1.2-javascriptcoregtk-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Selecting previously unselected package libopenshot-audio5:amd64.
Preparing to unpack .../libopenshot-audio5_0.1.4+0+50+111+201705110801~ubuntu16.04.1_amd64.deb ...
Unpacking libopenshot-audio5:amd64 (0.1.4+0+50+111+201705110801~ubuntu16.04.1) ...
Preparing to unpack .../libopenshot11_0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1_amd64.deb ...
Unpacking libopenshot11:amd64 (0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1) over (0.1.4+0+588+107+201703310337+daily~ubuntu16.04.1) ...
Preparing to unpack .../libxnvctrl0_381.22-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking libxnvctrl0 (381.22-0ubuntu0~gpu16.04.1) over (381.09-0ubuntu0~gpu16.04.2) ...
Selecting previously unselected package linux-image-extra-4.4.0-77-generic.
Preparing to unpack .../linux-image-extra-4.4.0-77-generic_4.4.0-77.98_amd64.deb ...
Unpacking linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
Preparing to unpack .../linux-generic_4.4.0.77.83_amd64.deb ...
Unpacking linux-generic (4.4.0.77.83) over (4.4.0.75.81) ...
Preparing to unpack .../linux-image-generic_4.4.0.77.83_amd64.deb ...
Unpacking linux-image-generic (4.4.0.77.83) over (4.4.0.75.81) ...
Preparing to unpack .../linux-headers-generic_4.4.0.77.83_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.77.83) over (4.4.0.75.81) ...
Preparing to unpack .../linux-libc-dev_4.4.0-77.98_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-77.98) over (4.4.0-75.96) ...
Preparing to unpack .../nvidia-settings_381.22-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-settings (381.22-0ubuntu0~gpu16.04.1) over (381.09-0ubuntu0~gpu16.04.2) ...
Preparing to unpack .../python3-openshot_0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1_amd64.deb ...
Unpacking python3-openshot:amd64 (0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1) over (0.1.4+0+588+107+201703310337+daily~ubuntu16.04.1) ...
Preparing to unpack .../openshot-qt_2.3.2+0+798+110+201705110701~ubuntu16.04.1_all.deb ...
Unpacking openshot-qt (2.3.2+0+798+110+201705110701~ubuntu16.04.1) over (2.3.1+0+785+108+201704010143~ubuntu16.04.1) ...
Preparing to unpack .../ssh-askpass-gnome_1%3a7.2p2-4ubuntu2.2_amd64.deb ...
Unpacking ssh-askpass-gnome (1:7.2p2-4ubuntu2.2) over (1:7.2p2-4ubuntu2.1) ...
Preparing to unpack .../unattended-upgrades_0.90ubuntu0.5_all.deb ...
Unpacking unattended-upgrades (0.90ubuntu0.5) over (0.90ubuntu0.3) ...
Preparing to unpack .../vidcutter_3.2.0~201705111415~ubuntu16.04.1_all.deb ...
Unpacking vidcutter (3.2.0~201705111415~ubuntu16.04.1) over (3.0.1-0~201703071624~ubuntu16.04.1) ...
Preparing to unpack .../rtmpdump_2.4+20151223.gitfa8646d-1ubuntu0.1_amd64.deb ...
Unpacking rtmpdump (2.4+20151223.gitfa8646d-1ubuntu0.1) over (2.4+20151223.gitfa8646d-1build1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for update-notifier-common (3.168.4) ...
flashplugin-installer: processing...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20170509.1.orig.tar.gz
Get:1 http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20170509.1.orig.tar.gz [30.4 MB]
Fetched 30.4 MB in 1min 1s (493 kB/s)                                          
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20170509.1.orig.tar.gz' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20170509.1.orig.tar.gz
Flash Plugin installed.
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up chromium-codecs-ffmpeg-extra (58.0.3029.96-0ubuntu0.16.04.1279) ...
Setting up uno-libs3 (5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up ure (5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4.1) ...
Setting up zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4.1) ...
Setting up zlib1g-dev:amd64 (1:1.2.8.dfsg-2ubuntu4.1) ...
Setting up fonts-opensymbol (2:102.10+LibO5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libfreetype6:amd64 (2.6.1-0.1ubuntu2.3) ...
Setting up libfreetype6:i386 (2.6.1-0.1ubuntu2.3) ...
Setting up openjdk-8-jre-headless:amd64 (8u131-b11-0ubuntu1.16.04.2) ...
Installing new version of config file /etc/java-8-openjdk/security/java.security ...
update-binfmts: warning: current package is openjdk-8, but binary format already installed by openjdk-7
Setting up openjdk-8-jre:amd64 (8u131-b11-0ubuntu1.16.04.2) ...
Setting up logrotate (3.8.7-2ubuntu2.16.04.1) ...
Setting up librtmp1:amd64 (2.4+20151223.gitfa8646d-1ubuntu0.1) ...
Setting up openssh-client (1:7.2p2-4ubuntu2.2) ...
Setting up activity-log-manager (0.9.7-0ubuntu23.16.04.1) ...
Setting up activity-log-manager-control-center (0.9.7-0ubuntu23.16.04.1) ...
Setting up firefox (53.0.2+build1-0ubuntu0.16.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (53.0.2+build1-0ubuntu0.16.04.2) ...
Setting up flashplugin-installer (25.0.0.171ubuntu0.16.04.1) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up libwebkit2gtk-4.0-37-gtk2:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up libopenshot-audio5:amd64 (0.1.4+0+50+111+201705110801~ubuntu16.04.1) ...
Setting up libopenshot11:amd64 (0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1) ...
Setting up libxnvctrl0 (381.22-0ubuntu0~gpu16.04.1) ...
Setting up linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Setting up linux-image-generic (4.4.0.77.83) ...
Setting up linux-headers-generic (4.4.0.77.83) ...
Setting up linux-generic (4.4.0.77.83) ...
Setting up linux-libc-dev:amd64 (4.4.0-77.98) ...
Setting up nvidia-settings (381.22-0ubuntu0~gpu16.04.1) ...
Setting up python3-openshot:amd64 (0.1.5+0+590+111+201705110817+daily~ubuntu16.04.1) ...
Setting up openshot-qt (2.3.2+0+798+110+201705110701~ubuntu16.04.1) ...
Setting up ssh-askpass-gnome (1:7.2p2-4ubuntu2.2) ...
Setting up unattended-upgrades (0.90ubuntu0.5) ...
Installing new version of config file /etc/init.d/unattended-upgrades ...
Synchronizing state of unattended-upgrades.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable unattended-upgrades
Setting up vidcutter (3.2.0~201705111415~ubuntu16.04.1) ...
Setting up rtmpdump (2.4+20151223.gitfa8646d-1ubuntu0.1) ...
Setting up libreoffice-style-galaxy (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-style-tango (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-style-elementary (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-common (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-core (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-base-core (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-calc (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-draw (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-impress (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-gtk2 (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-gnome (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-pdfimport (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up python3-uno (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-math (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Setting up libreoffice-writer (1:5.3.3~rc2-0ubuntu0.16.04.1~lo0) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
```

---

### Post by Bashing-om on 2017-05-11
rolfUser; Uh Huh ...

Looks good .
Reboot .

All good now ?

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-11
All good. Anything that needs to be checked, just ask.

---

### Post by ajgreeny on 2017-05-11
Great news! All now is exactly as I suspected and apart from running ```
sudo apt-get autoremove
``` to now remove unnecessary packages that remain, there is nothing more to do.

Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by rolfUser on 2017-05-12
input:
```
sudo apt-get autoremove
```
output:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 297 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 728427 files and directories currently installed.)
Removing linux-headers-4.4.0-72-generic (4.4.0-72.93) ...
Removing linux-headers-4.4.0-72 (4.4.0-72.93) ...
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
dkms: removing: nvidia-304 304.135 (4.4.0-72-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  nvidia-304
Version: 304.135
Kernel:  4.4.0-72-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


nvidia_304.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-72-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
```

---

### Post by Bashing-om on 2017-05-12
rolfUser; Hummmm

ajgreeny being offline, I jump back in here ,

While all looks good, I have to question why such an old version nVidia driver is installed as you are also running Win10.

*** A change in subject here ! Maybe a quicky ?? ****

Maybe better served with the correct graphic's driver installed ?
what returns :
```

lspci -nnk | grep -iA3 vga

```
see if we can get a different driver .

[INDENT][INDENT]we like squeaky clean
[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-13
> **Bashing-om said:**
> rolfUser; Hummmm

ajgreeny being offline, I jump back in here ,

While all looks good, I have to question why such an old version nVidia driver is installed as you are also running Win10.

*** A change in subject here ! Maybe a quicky ?? ****

Maybe better served with the correct graphic's driver installed ?
what returns :
```

lspci -nnk | grep -iA3 vga

```
see if we can get a different driver .[INDENT][INDENT]we like squeaky clean
[/INDENT]
[/INDENT]


```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330] [1002:9832]    Subsystem: Hewlett-Packard Company Kabini [Radeon HD 8330] [103c:2b18]
    Kernel driver in use: radeon
    Kernel modules: radeon

```

---

### Post by Bashing-om on 2017-05-13
rolfUser; Huh ???

How does nVidia :
> 
-------- Uninstall Beginning --------
Module:  nvidia-304
Version: 304.135
Kernel:  4.4.0-72-generic (x86_64)

play into  AMD graphic's hardware ??


a new thread on this new issue ??


[INDENT][INDENT]so much for a quicky -[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-13
What should we call it?

I was trying to install an Nvidia driver. I thought it would provide for more aspect ratios than just 4:3

---

### Post by vasa1 on 2017-05-13
Something like "How to install the appropriate graphics driver?" and you can post it in the [Hardware subforum]("https://ubuntuforums.org/forumdisplay.php?f=332").

---

### Post by rolfUser on 2017-05-14
[h=1][installing the appropriate drivers (HP)]("https://ubuntuforums.org/showthread.php?t=2361283")[/h][https://ubuntuforums.org/showthread.php?t=2361283&p=13645176#post13645176](https://ubuntuforums.org/showthread.php?t=2361283&p=13645176#post13645176)

---


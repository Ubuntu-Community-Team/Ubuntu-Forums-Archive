---
title: "Ubuntu gives me a black screen at login"
date: 2011-03-17
forum: Desktop Environments
---

### Post by penn919 on 2011-03-17
Hey,

After applying an update about two or three days ago, I restarted my system and now I'm getting a black screen at login. I can hear the brief drum sound clip that plays when the login dialog box pops up, but the screen is completely black and I can't see anything. I'm still able to access low graphics mode via the fail-safe option in the recovery mode menu. So far I've tried the following commands in the terminal:

```
 
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

```
sudo apt-get install --reinstall xserver-xorg
```

```
sudo apt-get install gdm ubuntu-desktop
```

These commands have helped me in the past with nearly identical graphics problems, but they are ineffective this time. I've also checked for broken packages via the recovery mode menu and that didn't work either.

Any ideas what the problem could be?

system specs

Model: Acer Aspire T160
CPU: AMD Athlon 64 3800+ (Socket 939)
Mobo: FC51GM (Foxconn WinFast 6100K8MA-RS)
Bios: Pheonix Technologies R02-B1 (From Acer)
RAM: 4 GB (dual Channel)
GPU: PowerColor ATI RADEON HD 4550 (512MB)
HDD (1): 160 GB
HDD (2): 120 GB
Optical Drive: CD-RW\DVD-Rom Combo
Optical Drive: DVD+RW Drive
OS:Ubuntu 10.04 Lucid Lynx \ Windows 7 Home Premium 64-bit

---

### Post by penn919 on 2011-03-17
Whoa now, don't all rush to respond at once...

---

### Post by YfoMp5QBh2 on 2011-03-17
ATI graphic card support seems to be a recurring issue in the support forums :(
 
So have you ran any of these commands? I take it someone has suggested you remove GDM completely and re-install?
 
Can you get to the CLI terminal by typing Alt+F2?
 
If so can you post your xorg.conf file? I dont suppose you happen to of made a backup of your xorg.conf file before you updated?

---

### Post by penn919 on 2011-03-17
Yes, I have tried all of the commands I posted above which involved uninstalling GDM and reinstalling it again. It worked before, but it's not working this time (although the symptoms weren't exactly the same and neither were the circumstances). 

To answer your second question, yes I still have access to the terminal via low-graphics mode and I'll try to post my xorg.conf file and I doubt if I have a backup because I don't remember making one, but I have a few questions:

1. Where exactly can I find the xorg.conf file?

2. If it so happens that backups are automated, where would  I find it?

and

3. When you say "post" do you mean to copy and paste the contents onto this thread, or do you want access to the actual file itself? For now I'm assuming the former, so I'll post it here tonight when I get back from work.

---

### Post by YfoMp5QBh2 on 2011-03-17
Usually if there is any change to the xorg.conf file a backup of the old one is made automatically (I assume your system may have made one if the display settings have changed recently).

You should be able just to restore the xorg.conf file using the backup providing there is one;

1. the xorg.conf file is in /etc/X11/xorg.conf,

2. the backup is in the same location normally called xorg.conf.backup or xorg.conf-backup or xorg.conf_backup.

and

3. by post i mean post the contents of the xorg.conf text file onto this thread so people can examine it, someone maybe able to point out where the error lies (nobody needs specific access to it).

you can use pastebin.com to put the contents in a hyperlink, and post it in your reply to save you copy and pasting straight into the thread.

---

### Post by penn919 on 2011-03-18
Sorry about the delay, I was supposed to post it the other night, but stuff turned up. Anyways, I was able to find many backups in the location you directed me to; however, I wasn't able to fine a plain "xorg.conf" file. Strangely enough, When I did a file search I found a file named "xorg.conf.new" located in my home directory. I'm guessing it might be the correct file so I posted it's contents at the site you suggested:

[http://pastebin.com/n1x7Vbks]("http://pastebin.com/n1x7Vbks")

Also, here's one of the xorg.conf-backup files. There only seems to be a few lines of commands written in them.

[http://pastebin.com/ze7cjNNP]("http://pastebin.com/ze7cjNNP")

What do you think? See a problem?

**update**

I found a second "xorg.conf.new" file in the "/" directory:

[http://pastebin.com/MFdvpVk0]("http://pastebin.com/MFdvpVk0")

---

### Post by YfoMp5QBh2 on 2011-03-19
I cant see any immediate problems (I am still learning to confirgure the xorg.conf file myself using various online tutorials). However It's interesting that you don't have a plain old xorg.conf file (thats the file ubuntu reads to startx).
 
What happens when you type ```
startx
``` into the terminal? If theres an error, what it is?
 
If startx fails, try renaming xorg.conf-backup to just xorg.conf and put it in the /etc/X11/ directory.
 
In terms of the xorg.conf.new file I think at some point you may have run ```
Xorg -config xorg.conf.new
```
which creates a new xorg.conf file based on the current system configuration

---

### Post by Krytarik on 2011-03-19
Nowadays at least Ubuntu doesn't setup/use a "xorg.conf" by default anymore.

Follow *spadge_2356* suggestion to put one of your xorg.conf's into "/etc/X11", but use the "xorg.conf.new" therefore, it seems more appropriate, since you have an ATI card, not Nvidia. Make sure that it has the correct permissions, if that matters at all:
```
-rw-r--r-- 1 root root 1810 2011-01-21 20:50 xorg.conf
```
Also, you don't have the proprietary driver installed or want to use it, right?

---

### Post by YfoMp5QBh2 on 2011-03-19
If your interested, a quick google search also yields;
 
[http://webcache.googleusercontent.com/search?hl=en&q=cache:9PFopzJKLpoJ:http://hubpages.com/hub/How-to-configure-Xorg-in-Ubuntu+how+to+configure+xorg.conf&ct=clnk](http://webcache.googleusercontent.com/search?hl=en&q=cache:9PFopzJKLpoJ:http://hubpages.com/hub/How-to-configure-Xorg-in-Ubuntu+how+to+configure+xorg.conf&ct=clnk)

---

### Post by penn919 on 2011-03-20
> **spadge_2356 said:**
> I cant see any immediate problems (I am still learning to confirgure the xorg.conf file myself using various online tutorials). However It's interesting that you don't have a plain old xorg.conf file (thats the file ubuntu reads to startx).
 
What happens when you type ```
startx
``` into the terminal? If theres an error, what it is?
 
If startx fails, try renaming xorg.conf-backup to just xorg.conf and put it in the /etc/X11/ directory.
 
In terms of the xorg.conf.new file I think at some point you may have run ```
Xorg -config xorg.conf.new
```
which creates a new xorg.conf file based on the current system configuration

The startx command just brings up a black screen.

I've renamed the xorg.conf.new to xorg.conf and I've moved it into the etc/X11/ directory, but the problem still persists the same way as before.

I haven't checked out the link from your latest post yet, but I'll definitely get around to it either later today or sometime tomorrow.

---

### Post by penn919 on 2011-03-20
> **Krytarik said:**
> Nowadays at least Ubuntu doesn't setup/use a "xorg.conf" by default anymore.

Follow *spadge_2356* suggestion to put one of your xorg.conf's into "/etc/X11", but use the "xorg.conf.new" therefore, it seems more appropriate, since you have an ATI card, not Nvidia. Make sure that it has the correct permissions, if that matters at all:
```
-rw-r--r-- 1 root root 1810 2011-01-21 20:50 xorg.conf
```
Also, you don't have the proprietary driver installed or want to use it, right?

Before I experienced this problem, the hardware manager listed my display driver as ATI FireGL so I suppose that I had the proprietary driver. I'd like to get it working as it was before, so yes. I want the proprietary driver.

---

### Post by Krytarik on 2011-03-20
> **penn919 said:**
> Before I experienced this problem, the hardware manager listed my display driver as ATI FireGL so I suppose that I had the proprietary driver. I'd like to get it working as it was before, so yes. I want the proprietary driver.
Did you install those also through "Hardware Drivers" initially?

---

### Post by penn919 on 2011-03-20
> **Krytarik said:**
> Did you install those also through "Hardware Drivers" initially?

Yes. I tried to use the ones on AMD's website, but I was never able to get it to work.

---

### Post by Krytarik on 2011-03-20
> **penn919 said:**
> Yes. I tried to use the ones on AMD's website, but I was never able to get it to work.
It's really better this way, believe me! ;)

Do you have any remaining files from your trial to install those from the website?
If so, follow its removal instructions before doing the following steps.

So, then please do this:

Purge any remaining packages of the proprietary driver, just to make it clean:
```
sudo apt-get purge fglrx*

```Add Ubuntu-X-Swat's PPA to get the most recent packaged version of the proprietary driver:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

```Install the proprietary driver:
```
sudo apt-get install fglrx
```Make sure that you have a proper "xorg.conf":
```
sudo aticonfig --initial -f
```

---

### Post by penn919 on 2011-03-20
> **Krytarik said:**
> It's really better this way, believe me! ;)

Do you have any remaining files from your trial to install those from the website?
If so, follow its removal instructions before doing the following steps.

So, then please do this:

Purge any remaining packages of the proprietary driver, just to make it clean:
```
sudo apt-get purge fglrx*

```Add Ubuntu-X-Swat's PPA to get the most recent packaged version of the proprietary driver:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

```Install the proprietary driver:
```
sudo apt-get install fglrx
```Make sure that you have a proper "xorg.conf":
```
sudo aticonfig --initial -f
```

I tried what you suggested, but I got an error at the "sudo apt-get fglrx" part. Look below:

```
penn@ubuntu:~$ sudo apt-get purge fglrx*
[sudo] password for penn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting fglrx-driver-dev for regex 'fglrx*'
Note, selecting fglrx for regex 'fglrx*'
Note, selecting xfree86-driver-fglrx-dev for regex 'fglrx*'
Note, selecting fglrx-control for regex 'fglrx*'
Note, selecting fglrx-amdcccle for regex 'fglrx*'
Note, selecting fglrx-dev for regex 'fglrx*'
Note, selecting fglrx-modaliases for regex 'fglrx*'
Note, selecting fglrx-kernel-source for regex 'fglrx*'
Note, selecting xorg-driver-fglrx for regex 'fglrx*'
Note, selecting fglrx-control-qt2 for regex 'fglrx*'
Note, selecting xorg-driver-fglrx-dev for regex 'fglrx*'
E: Couldn't find package fglrx*
penn@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
penn@ubuntu:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release [1,347B]                             
Hit http://mirror.cc.columbia.edu lucid Release.gpg                            
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid/main Translation-en_US
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid/restricted Translation-en_US
Get:3 http://dl.google.com stable/main Packages [1,064B]                       
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid/universe Translation-en_US
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid/multiverse Translation-en_US
Hit http://mirror.cc.columbia.edu lucid-updates Release.gpg                    
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates/main Translation-en_US
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates/restricted Translation-en_US
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates/universe Translation-en_US
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates/multiverse Translation-en_US
Get:4 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_US
Hit http://packages.medibuntu.org lucid Release.gpg                            
Hit http://mirror.cc.columbia.edu lucid-security Release.gpg                   
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-security/main Translation-en_US
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-security/universe Translation-en_US
Ign http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-security/multiverse Translation-en_US
Hit http://mirror.cc.columbia.edu lucid Release                                
Hit http://mirror.cc.columbia.edu lucid-updates Release                        
Get:5 http://ppa.launchpad.net lucid Release [14.0kB]                          
Hit http://mirror.cc.columbia.edu lucid-security Release                       
Hit http://archive.canonical.com lucid Release                                 
Hit http://mirror.cc.columbia.edu lucid/main Packages                          
Hit http://mirror.cc.columbia.edu lucid/restricted Packages                    
Hit http://mirror.cc.columbia.edu lucid/main Sources                           
Hit http://mirror.cc.columbia.edu lucid/restricted Sources                     
Hit http://mirror.cc.columbia.edu lucid/universe Packages                      
Hit http://mirror.cc.columbia.edu lucid/universe Sources                       
Hit http://mirror.cc.columbia.edu lucid/multiverse Packages                    
Hit http://mirror.cc.columbia.edu lucid/multiverse Sources                     
Hit http://mirror.cc.columbia.edu lucid-updates/main Packages                  
Hit http://mirror.cc.columbia.edu lucid-updates/restricted Packages            
Hit http://mirror.cc.columbia.edu lucid-updates/main Sources                   
Hit http://mirror.cc.columbia.edu lucid-updates/restricted Sources             
Hit http://mirror.cc.columbia.edu lucid-updates/universe Packages              
Hit http://mirror.cc.columbia.edu lucid-updates/universe Sources               
Hit http://mirror.cc.columbia.edu lucid-updates/multiverse Packages            
Hit http://archive.canonical.com lucid/partner Packages                        
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Hit http://mirror.cc.columbia.edu lucid-updates/multiverse Sources             
Hit http://mirror.cc.columbia.edu lucid-security/main Packages                 
Hit http://mirror.cc.columbia.edu lucid-security/restricted Packages           
Hit http://mirror.cc.columbia.edu lucid-security/main Sources                  
Hit http://mirror.cc.columbia.edu lucid-security/restricted Sources            
Get:6 http://ppa.launchpad.net lucid/main Packages [8,964B]                    
Hit http://mirror.cc.columbia.edu lucid-security/universe Packages             
Hit http://mirror.cc.columbia.edu lucid-security/universe Sources              
Hit http://mirror.cc.columbia.edu lucid-security/multiverse Packages           
Hit http://mirror.cc.columbia.edu lucid-security/multiverse Sources            
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Hit http://packages.medibuntu.org lucid Release           
Hit http://packages.medibuntu.org lucid/free Packages     
Hit http://packages.medibuntu.org lucid/non-free Packages
Fetched 25.8kB in 2s (12.7kB/s)
Reading package lists... Done
penn@ubuntu:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot fglrx-amdcccle patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  dkms fakeroot fglrx fglrx-amdcccle patch
0 upgraded, 5 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/26.0MB of archives.
After this operation, 78.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package dkms.
(Reading database ... 281611 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Unpacking fglrx (from .../fglrx_2%3a8.801-0ubuntu1~xup~lucid_i386.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.801-0ubuntu1~xup~lucid_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.801-0ubuntu1~xup~lucid_i386.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.801-0ubuntu1~xup~lucid_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is what always happens when I try to install fglrx. It just never works.

---

### Post by Krytarik on 2011-03-20
I guess this is because of the previous unsuccessful trial to install the proprietary driver manually. Please follow this guide on how to remove it:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

After that, run the both last commands mentioned above again.

---

### Post by penn919 on 2011-03-20
> **Krytarik said:**
> I guess this is because of the previous unsuccessful trial to install the proprietary driver manually. Please follow this guide on how to remove it:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

After that, run the both last commands mentioned above again.

I tried the steps that were in that link, but the same thing happens. I get the error telling me that the driver isn't installed, so it doesn't uninstall anything.

---

### Post by penn919 on 2011-03-20
> **spadge_2356 said:**
> If your interested, a quick google search also yields;
 
[http://webcache.googleusercontent.com/search?hl=en&q=cache:9PFopzJKLpoJ:http://hubpages.com/hub/How-to-configure-Xorg-in-Ubuntu+how+to+configure+xorg.conf&ct=clnk](http://webcache.googleusercontent.com/search?hl=en&q=cache:9PFopzJKLpoJ:http://hubpages.com/hub/How-to-configure-Xorg-in-Ubuntu+how+to+configure+xorg.conf&ct=clnk)

I checked out your link and followed the instructions and generated a new xorg.conf, but I still get a black screen when I startx. The dpkg reconfigure command didn't work either. I've already reinstalled GDM,but I gave it another go and still no dice. :(

---

### Post by Krytarik on 2011-03-21
> **penn919 said:**
> I tried the steps that were in that link, but the same thing happens. I get the error telling me that the driver isn't installed, so it doesn't uninstall anything.
Sure, you don't have any "fglrx*" packages installed, just follow the rest of the steps.

---

### Post by penn919 on 2011-03-21
> **Krytarik said:**
> Sure, you don't have any "fglrx*" packages installed, just follow the rest of the steps.

What other steps? You mean the steps to restore the open source driver? I've already tried that like a million times. It doesn't do anything.

Here. Take a look for yourself:

Uninstalling fglrx

```
penn@ubuntu:~$ sudo sh /usr/share/ati/fglrx-uninstall.sh
[sudo] password for penn: 

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

penn@ubuntu:~$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx is not installed, so not removed
Note, selecting fglrx-driver-dev for regex 'fglrx_*'
Note, selecting fglrx for regex 'fglrx_*'
Note, selecting fglrx-driver for regex 'fglrx_*'
Note, selecting xfree86-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-control for regex 'fglrx_*'
Note, selecting fglrx-amdcccle for regex 'fglrx_*'
Note, selecting fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-modaliases for regex 'fglrx_*'
Note, selecting fglrx-kernel-source for regex 'fglrx_*'
Note, selecting xorg-driver-fglrx for regex 'fglrx_*'
Note, selecting fglrx-control-qt2 for regex 'fglrx_*'
Note, selecting xorg-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting xfree86-driver-fglrx for regex 'fglrx_*'
E: Couldn't find package fglrx_*

```

and here's the one for reinstalling the open source driver:

```
penn@ubuntu:~$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-ati* xserver-xorg-video-radeon*
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 1,819kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 281684 files and directories currently installed.)
Removing xserver-xorg-video-ati ...
Removing xserver-xorg-video-radeon ...
Purging configuration files for xserver-xorg-video-radeon ...
Processing triggers for man-db ...
penn@ubuntu:~$ sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xserver-xorg-video-radeon
Suggested packages:
  firmware-linux
The following NEW packages will be installed:
  xserver-xorg-video-ati xserver-xorg-video-radeon
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/881kB of archives.
After this operation, 1,819kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package xserver-xorg-video-radeon.
(Reading database ... 281664 files and directories currently installed.)
Unpacking xserver-xorg-video-radeon (from .../xserver-xorg-video-radeon_1%3a6.13.1-1ubuntu1~xup3~lucid_i386.deb) ...
Selecting previously deselected package xserver-xorg-video-ati.
Unpacking xserver-xorg-video-ati (from .../xserver-xorg-video-ati_1%3a6.13.1-1ubuntu1~xup3~lucid_i386.deb) ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-radeon (1:6.13.1-1ubuntu1~xup3~lucid) ...

Setting up xserver-xorg-video-ati (1:6.13.1-1ubuntu1~xup3~lucid) ...
penn@ubuntu:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 2 not upgraded.
Need to get 0B/5,400kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 281685 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.7.1-1ubuntu3 (using .../libgl1-mesa-dri_7.7.1-1ubuntu3_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.7.1-1ubuntu3 (using .../libgl1-mesa-glx_7.7.1-1ubuntu3_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace xserver-xorg-core 2:1.7.6-2ubuntu7.5 (using .../xserver-xorg-core_2%3a1.7.6-2ubuntu7.5_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Processing triggers for man-db ...
Setting up libgl1-mesa-dri (7.7.1-1ubuntu3) ...

Setting up libgl1-mesa-glx (7.7.1-1ubuntu3) ...

Setting up xserver-xorg-core (2:1.7.6-2ubuntu7.5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
penn@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg
penn@ubuntu:~$
```

It didn't work. I'm still getting a black screen at login.

---

### Post by YfoMp5QBh2 on 2011-03-21
[LEFT]Hi There,

Your display was working fine before the update right? You say you want the proprietary driver like you had before to put the display back the way it was, but before the update I don't think you had the propriatery drivers. A brief comparison between your xorg.conf.new and the backup suggests you went from the default drivers that were initially installed to the new ones.

Use the details from the backup xorg file; where it says ```
Section "Screen"
``` in the current xorg.conf file delete everything between the section "screen" and END SECTION and replace it with what's between those sections in the xorg.conf-backup;

```
 
[LIST=1]
[*]Section "Screen"
[*]        Identifier      "Default Screen"
[*]        DefaultDepth    24
[*]EndSection
[/LIST]

```

do the same for Section "Module" and Section "Device", save the file and then reboot. This should force the system to use the old setting before you updated.

If that doesn't work there's other stuff we can try like re-installing the proprietary drivers (but we should try the easiest fixes first). Let us know how you get on and if there's any further error messages.
[/LEFT]

---

### Post by Krytarik on 2011-03-21
> **penn919 said:**
> 
```
penn@ubuntu:~$ sudo sh /usr/share/ati/fglrx-uninstall.sh
[sudo] password for penn: 

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

```
You have those difficulties because there are still remnants of the proprietary driver you tried to install manually.

Try to remove those by running the following command:
```
sudo env FORCE_ATI_UNINSTALL=1 /usr/share/ati/fglrx-uninstall.sh
```
If that finishes successfully, run those commands again:
```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx
sudo aticonfig --initial -f
```

---

### Post by penn919 on 2011-03-21
> **Krytarik said:**
> You have those difficulties because there are still remnants of the proprietary driver you tried to install manually.

Try to remove those by running the following command:
```
sudo env FORCE_ATI_UNINSTALL=1 /usr/share/ati/fglrx-uninstall.sh
```
If that finishes successfully, run those commands again:
```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx
sudo aticonfig --initial -f
```

Holy *****, it actually worked!
```
penn@ubuntu:~$ sudo env FORCE_ATI_UNINSTALL=1 /usr/share/ati/fglrx-uninstall.sh
[sudo] password for penn: 

Error! There are no instances of module: fglrx
8.753 located in the DKMS tree.
Errors during DKMS module removal
Uninstall fglrx driver complete...

penn@ubuntu:~$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-ati* xserver-xorg-video-radeon*
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 1,819kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 282803 files and directories currently installed.)
Removing xserver-xorg-video-ati ...
Removing xserver-xorg-video-radeon ...
Purging configuration files for xserver-xorg-video-radeon ...
Processing triggers for man-db ...
penn@ubuntu:~$ sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xserver-xorg-video-radeon
Suggested packages:
  firmware-linux
The following NEW packages will be installed:
  xserver-xorg-video-ati xserver-xorg-video-radeon
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/881kB of archives.
After this operation, 1,819kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package xserver-xorg-video-radeon.
(Reading database ... 282783 files and directories currently installed.)
Unpacking xserver-xorg-video-radeon (from .../xserver-xorg-video-radeon_1%3a6.13.1-1ubuntu1~xup3~lucid_i386.deb) ...
Selecting previously deselected package xserver-xorg-video-ati.
Unpacking xserver-xorg-video-ati (from .../xserver-xorg-video-ati_1%3a6.13.1-1ubuntu1~xup3~lucid_i386.deb) ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-radeon (1:6.13.1-1ubuntu1~xup3~lucid) ...

Setting up xserver-xorg-video-ati (1:6.13.1-1ubuntu1~xup3~lucid) ...
penn@ubuntu:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 2 not upgraded.
Need to get 0B/5,400kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 282804 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.7.1-1ubuntu3 (using .../libgl1-mesa-dri_7.7.1-1ubuntu3_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.7.1-1ubuntu3 (using .../libgl1-mesa-glx_7.7.1-1ubuntu3_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace xserver-xorg-core 2:1.7.6-2ubuntu7.5 (using .../xserver-xorg-core_2%3a1.7.6-2ubuntu7.5_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Processing triggers for man-db ...
Setting up libgl1-mesa-dri (7.7.1-1ubuntu3) ...

Setting up libgl1-mesa-glx (7.7.1-1ubuntu3) ...

Setting up xserver-xorg-core (2:1.7.6-2ubuntu7.5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
penn@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg

penn@ubuntu:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/25.7MB of archives.
After this operation, 76.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 282804 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.801-0ubuntu1~xup~lucid_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.801-0ubuntu1~xup~lucid_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up fglrx (2:8.801-0ubuntu1~xup~lucid) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.801 DKMS files...
Building only for 2.6.32-30-generic-pae
Building for architecture i686
Building initial module for 2.6.32-30-generic-pae
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-30-generic-pae/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Setting up fglrx-amdcccle (2:8.801-0ubuntu1~xup~lucid) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-30-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
penn@ubuntu:~$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0
penn@ubuntu:~$ 
```

Can't believe it. Once I restarted my computer, I was finally able to get my native resolution to display again and enable special effects. Lets just hope another disruptive update won't come along and fvck this up again.

Krytarik, spadge

Major thanks!

---


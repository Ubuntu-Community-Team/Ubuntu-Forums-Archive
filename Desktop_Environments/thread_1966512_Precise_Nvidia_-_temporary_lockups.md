---
title: "Precise Nvidia - temporary lockups"
date: 2012-04-27
forum: Desktop Environments
---

### Post by nogoodnamesleft on 2012-04-27
Hi all!

Some weird problems with Precise and Nvidia 8800 GTX. If I enable the (normal) 3d mode, the machine hangs every few seconds. Everything works fine in 2d mode but the performance e.g. dragging windows is obviously slower than it should be . I've tried both nvidia drivers (current, and post distribution updates).

Works fine in Fedora 16 so card not broken.

---

### Post by Pablo Pablovski on 2012-04-27
There are significant problems with the latest nvidia GPU drivers, v 295.40 which, I believe are being included in 12.04. Search here for "295.40" and you'll find plenty of posts about the problems. 

Some workarounds have been identified and are successful for some people, others haven't been so lucky. Seems like downloading to v295.33 is a fix for many - worked for me on 11.04 / GTS8800.
 
I'm amazed that Canonical chose to release 12.04 with these iffy drivers when nvidia themselves have acknowledged the problem. Also amazed that the drivers are still being offered to users of 11.10 and earlier.

---

### Post by nogoodnamesleft on 2012-04-27
I have removed the closed source proprietary drivers from my machine and it works properly now.

I am sure there is a lesson to be learned somewhere from this :-)

---

### Post by Pablo Pablovski on 2012-05-03
Nvidia driver 295.49 released...

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)


Manual installation worked for me - no stops, gaps, freezes or crashes.

---

### Post by garyzw on 2012-05-04
Please can you give step by step instructions on how to do this?


> **Pablo Pablovski said:**
> Nvidia driver 295.40 released...

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)


Manual installation worked for me - no stops, gaps, freezes or crashes.

---

### Post by udumbtu on 2012-07-18
Recently, I built a new computer, but when I tried to install Ubuntu 12.04 Desktop on it I had all kinds of problems. I write this and share it with the hope that other people will find it useful and not go through the days of pain I did. The problems arose from two hardware specifics: Raid 1 configuration through BIOS, and a NVidia video card. The RAID through BIOS  makes installation from a CD  impossible; it gets stuck at the second screen. NVidia card is a problem when installing the desktop ; there is no visible desktop, and no CLI through Ctrl+Alt+F1, etc.
  
  Here's the hardware: 
 	Mobo: 	Biostar TA870U3+ 
 	Memory:	16GB 
 	CPU: 	AMD Phenom II X6 1045T 
 	HDD:	2x2TB as RAID 1 configured through BIOS. This is for my files, etc 
 		320GB for OSs. Half is used for win7. The other half to be used for Ubuntu. 
 	DVD drive 
 	Video	: NVidia GT520 by Asus with a large heat sink and no fan, so no extra noise. This is not a gaming PC, but it it can play flawlessly 1080p videos in the end, has a lot of computing muscle, and can run easy 12 virtual machines in VirtualBox.  There are two monitors connected to this: one HDMI 1920x1080p (primary) and one VGA 1280x1024.
 

 Here is  my very easy and flawless installation procedure:
 

 # boot from an unetbooting usb flash drive with ubuntu 12.04 server 64bit on it 
 # at menu choose "install ubuntu server" 
 # at sever selection menu (based on tasksel) just hit enter 
 # when done, run the following commands as root (do not reboot in between, just at the end): 
  
 tasksel install ubuntu-desktop 
 apt-add-repository ppa:ubuntu-x-swat/x-updates 
 apt-get update 
 apt-get install nvidia-current 
 apt-get install ubuntu-restricted-extras   #this is needed to play almost any media files 
 /usr/share/doc/libdvdread4/install-css.sh3  	#this is needed to play DVDs 
 apt-get install gnome-session-fallback   	#if you want the classic gnome desktop 
 reboot 
 

 #enjoy!

---

### Post by glennric on 2012-07-18
The simplest way to obtain the nvidia 295.49 drivers is by installing the nvidia-current-updates package.  This is in the precise-updates suite of the Ubuntu repositories, which I believe is enabled by default.

---


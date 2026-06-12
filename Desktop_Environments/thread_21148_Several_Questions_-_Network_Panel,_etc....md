---
title: "Several Questions - Network Panel, etc..."
date: 2005-03-20
forum: Desktop Environments
---

### Post by vvu on 2005-03-20
Folks, I am quite new to Linux and Ubuntu in general.  I actually decided to wipe my laptop out because I have now Kubuntu (KDE 3.4 based Ubuntu).  This is great!  Anyhow, I am configuring several things to make it function like my Windows - for work related.  One main problem - task/issue #6 below.

(1)  VPN - COMPLETE (pptp-linux)

(2)  RDP to Terminal Servers at work - Complete (remote desktop connection)

(3)  Evolution for Exchange email (not complete - working on it...)

(4)  Video recorder for Linux (still looking)  - Please provide options

(5)  What GUI based tool in this distro can I use to centrally manage Network configurations?  Hostname, ipaddress, DNS, etc?  

(6)  Install VMWare for Linux 4.5 (problem - not working) - it asks for linux kernel info - /usr/src/linux/include but there is nothing there and I even resinatlled via Kynaptics the kernel header - STILL no GO. I referred to this for troubleshooting - [http://www.ubuntuforums.org/showthread.php?t=18136&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=18136&highlight=vmware) but still no go.  There is nothin in that location as far as kernel headers - /usr/src/linux/  <-- this is my main concern now -  ](*,) 

I am running kernel - Linux kubuntuwks01 2.6.10-5-386 #1 Tue Mar 15 14:43:37 UTC 2005 i686 GNU/Linux  (the latest download and patches for Kubuntu).

Can someone help more or point me to better resources to task/issue #6 with VMWare?

Thank you for any help!

---

### Post by Roptaty on 2005-03-21
(6) 
What is the contents of the directory /usr/src ? 
If linux-headers-your-kernel-version exists, try creating a symlink from that to /usr/src/linux
For instance:
ln -sf linux-headers-your-kernel-version linux
(when you are inside the /usr/src directory)

---

### Post by vvu on 2005-03-21
Yes, your suggestion is similar to that link I provided; however, the only item in the /usr/src IS /usr/src/rpm  - so again that's my dilemma.  There is nothing to even link to in that location.  Does it make a difference with this brand new install of Kubuntu Hoary 5.04?  By the way, the forum must be moving around because earlier this was in Application top level, then Kubuntu, KDE, and NOW Gnome!  =; 

So, the problem is that there is NOTHING in the /usr/src directory pertaining to the linux kernel / headers or their versions.

Thanks again everyone.

---

### Post by Roptaty on 2005-03-21
Okei... Which files does your linux-header package provide? 
I'm not familiar with kynaptics, but with synaptics you can find this out by locating the package, and then choose Properties->Installed files.

---

### Post by vvu on 2005-03-21
Okay, this is my second full day on Linux - I really love Kubuntu!  

Anyhow, back to the problem at hand...if the applications you are installing (such as VMWare in my example) are looking for linux headers - just use apt-get or synaptic or kynaptic to retrieve the version for your kernel - get it from the Development Section of Synaptic of Kynaptic (gui front ends to apt-get).  You might as well as install the other GCC / GNU compilers also (i.e. gcc-3.3, gcc-3.4).  This is something I am now just learning on my own.  Basically, some apps have dependency you just have to just read up on its requirement and download them.  Being a first time user, I depended entirely on the apt-get tool retrieve all dependencies - not necessarily correct.  Afterall, I can from a Windows world where everything just works. 

Thanks.

 :p

---


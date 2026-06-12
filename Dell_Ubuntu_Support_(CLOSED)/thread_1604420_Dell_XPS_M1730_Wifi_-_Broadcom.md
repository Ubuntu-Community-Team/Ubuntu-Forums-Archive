---
title: "Dell XPS M1730 Wifi - Broadcom"
date: 2010-10-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PhantomSAP on 2010-10-24
Hi,
    I own a Dell XPS M1730 which I bought almost a year back and it runs windows vista. it uses a Broadcom Card for wifi. I see that there are a list of packages already present for braodcom but I am unable to figure out which packages I must use. I believe I have a BCM 4312. 

the list of packages that I got for when I searched the description as broadcom are :
**Package bcmwl-kernel-source**

   
[LIST]
[*][lucid]("http://packages.ubuntu.com/lucid/bcmwl-kernel-source")  (admin): 	Broadcom 802.11 Linux STA wireless driver source [**restricted**]              
5.60.48.36+bdcom-0ubuntu3: amd64 i386
[/LIST]
    **Package broadcom-sta-common**

   
[LIST]
[*][lucid]("http://packages.ubuntu.com/lucid/broadcom-sta-common")  (admin): 	Common files for the Broadcom STA Wireless driver [**multiverse**]              
5.10.91.9.3-3: all
[/LIST]
    **Package bcm5700-source**

   
[LIST]
[*][lucid]("http://packages.ubuntu.com/lucid/bcm5700-source") (net): 	module source for Broadcom's bcm5700 ethernet driver [**multiverse**]              
8.3.14-5: all
[/LIST]
    **Package broadcom-sta-source**

   
[LIST]
[*][lucid]("http://packages.ubuntu.com/lucid/broadcom-sta-source")  (admin): 	Source for the Broadcom STA Wireless driver [**multiverse**]              
5.10.91.9.3-3: all
[/LIST]
    **Package b43-fwcutter**

   
[LIST]
[*][lucid]("http://packages.ubuntu.com/lucid/b43-fwcutter") (utils): 	Utility for extracting Broadcom 43xx firmware            
1:012-1build1: amd64 i386
[/LIST]
    **Package bcmwl-modaliases**

   
[LIST]
[*][lucid]("http://packages.ubuntu.com/lucid/bcmwl-modaliases")  (admin): 	Modaliases for the Broadcom 802.11 Linux STA driver            
5.60.48.36+bdcom-0ubuntu3: amd64 i386
[/LIST]

I can download the packages on my windows and later try get them installed in ubuntu( i use ubuntu from USB stick to try out the software V 10.04 | 64-bit)

Can kindly suggest what needs to be done to get my wifi running in Ubuntu please ?

Thanks.

PS : I am as well new to ubuntu.

---

### Post by mörgæs on 2010-10-25
Hi, welcome to the forum.

Is there a particular reason that you are running from a live USB and not installing to the hard drive?

---

### Post by PhantomSAP on 2010-10-25
Yes I would like to perform a test before I actually install it and see if suits my needs, or is it feasible for me to install ubuntu in the USB Drive itself ?

My problem is that my wired internet connection doesnt work (have never used it to be franked and now its not working even in my windows) but my wifi works fine on Windows. So I am trying to see if there is anyway I can download the missing drivers / Packages and Update ubuntu offline.

Any information regarding how to set my Wifi will be great and I can do an Install of Ubuntu as well in a USB if that is possible.

Thanks.

---

### Post by garvinrick4 on 2010-10-25
[http://ubuntuforums.org/showthread.php?t=1598698&page=5](http://ubuntuforums.org/showthread.php?t=1598698&page=5)

---

### Post by PhantomSAP on 2010-10-28
Thanks that worked like a charm :)

---

### Post by PhantomSAP on 2010-11-07
> **garvinrick4 said:**
> [http://ubuntuforums.org/showthread.php?t=1598698&page=5](http://ubuntuforums.org/showthread.php?t=1598698&page=5)

the instructions given was working for me before, but now when I was trying a fresh download of everything and using a persistent USB (Casper 2 GB) I am getting errors.

When deploying the packages I get the following error

:~/Downloads$ sudo dpkg -i linux*.deb
Selecting previously deselected package linux-headers-2.6.37-999.
(Reading database ... 121715 files and directories currently installed.)
Unpacking linux-headers-2.6.37-999 (from linux-headers-2.6.37-999_2.6.37-999.201011041120_all.deb) ...
Selecting previously deselected package linux-headers-2.6.37-999-generic.
Unpacking linux-headers-2.6.37-999-generic (from linux-headers-2.6.37-999-generic_2.6.37-999.201011041120_amd64.deb) ...
Selecting previously deselected package linux-image-2.6.37-999-generic.
Unpacking linux-image-2.6.37-999-generic (from linux-image-2.6.37-999-generic_2.6.37-999.201011041120_amd64.deb) ...
Done.


Setting up linux-headers-2.6.37-999 (2.6.37-999.201011041120) ...
Setting up linux-headers-2.6.37-999-generic (2.6.37-999.201011041120) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.37-999-generic /boot/vmlinuz-2.6.37-999-generic
Setting up linux-image-2.6.37-999-generic (2.6.37-999.201011041120) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-999-generic

**cp: cannot stat `/vmlinuz': No such file or directory**

Failed to create initrd image.
dpkg: error processing linux-image-2.6.37-999-generic (--install):
 subprocess installed post-installation script returned error exit status 2

Errors were encountered while processing:
 linux-image-2.6.37-999-generic

I have tried the command 
```
ln -s /cdrom/casper/vmlinuz /vmlinuz
```but the problem still persists. Any idea as to what this issue due to or how to make a work around ?

Thanks.

PS: I am not sure if this issue has to be addressed on a separate post or can be addressed here.

---


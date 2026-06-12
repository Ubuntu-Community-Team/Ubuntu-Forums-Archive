---
title: "Ubuntu 10.04 LIVE Via PXE (Network boot)"
date: 2010-07-28
forum: Desktop Environments
---

### Post by TyTiger on 2010-07-28
Hi people, 

Ive recently been playing around with PXE (network booting)ubuntu and various other OS's (thinstation eg) and I was able to get ubuntu 8.04 LTS to boot the live disk entirely over the network using a combination of tftp and the disk image mounted and shared as an NFS share on a server..

I however have had no such luck doing the same thing with ubuntu 10.04 TLS using the exact same method as used previously, 
(Download iso, extracted vmlinuz and initrd out of casper directory) and so on, to find that the boot process stops after running the pre mount scripts (see attached image for details)

from what i can gather its related to the network drivers/modules, but dont take my word for it 

Also the same error occurs on multiple PXE Enabled clients i have tested this on, not just virtual box. all machines have different nics and so fourth and are all (normally) compatible with ubuntu out of the box.

you can see a write up of my full method of booting via PXE **_[Here]("http://www.rons-forum.co.uk/viewtopic.php?f=9&t=2&sid=0025f156adceac5fbf6d94781a1b9a77")_**
thanks.

---

### Post by TyTiger on 2010-07-28
Bump

---

### Post by TyTiger on 2010-07-29
bump

---

### Post by TyTiger on 2010-07-30
Anybody?

---

### Post by hakkie42@gmail.com on 2010-08-04
Seem to remember the way that newer Ubuntus boot is different than 8.04. Probably not much help to you, but at least it's an indication you're not going mad.

Random copy/paste from my notes (at the time working with Ubuntu 9); sorry it's been too long so I don't know whether this works.
Modify our PXELINUX configuration file.
#note: I lowercased all names to avoid confusion
sudo nano /var/lib/tftpboot/pxelinux.cfg/default
DEFAULT vesamenu.c32 
TIMEOUT 6000
ONTIMEOUT BootLocal
PROMPT 0
MENU INCLUDE pxelinux.cfg/pxe.conf
NOESCAPE 1
LABEL BootLocal
        localboot 0
        TEXT HELP
        Boot to local hard disk
        ENDTEXT
MENU BEGIN Ubuntu
MENU TITLE Ubuntu 
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE ubuntu/ubuntu.menu
MENU END
MENU BEGIN CentOS
MENU TITLE CentOS 
        LABEL Previous
MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE centos/centos.menu
MENU END
MENU BEGIN Fedora
MENU TITLE Fedora 
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE fedora/fedora.menu
MENU END
MENU BEGIN SystemRescueCd
MENU TITLE SystemRescueCd 
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE systemrescuecd/systemrescuecd.menu
MENU END
MENU BEGIN VMware 
MENU TITLE VMware 
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE vmware/vmware.menu
MENU END
MENU BEGIN Tools and Utilities
MENU TITLE Tools and Utilities
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE utilities/utilities.menu
MENU END
MENU BEGIN DOS Based
MENU TITLE DOS Based
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE dos/dos.menu
MENU END

sudo nano /var/lib/tftpboot/pxelinux.cfg/pxe.conf
MENU TITLE  PXE Server 
MENU BACKGROUND pxelinux.cfg/logo.png
NOESCAPE 1
ALLOWOPTIONS 1
PROMPT 0
menu width 80
menu rows 14
MENU TABMSGROW 24
MENU MARGIN 10
menu color border               30;44      #ffffffff #00000000 std

Create the Ubuntu menu and files:
#files:
Mount the Ubuntu DVD ISO and copy the kernel and initrd to the previously created location.
sudo mount -o loop -t iso9660 /myth/tmp/ubuntu-9.10-desktop-i386.iso /mnt
#for fedora type:
sudo cp /mnt/images/pxeboot/vmlinuz /var/lib/tftpboot/centos/5.3/amd64
sudo cp /mnt/images/pxeboot/initrd.img /var/lib/tftpboot/centos/5.3/amd64
#for ubuntu type:
sudo cp /mnt/casper/vmlinuz /var/lib/tftpboot/ubuntu/9.10/i386
#ubuntu 9.04:
sudo cp /mnt/casper/initrd.gz /var/lib/tftpboot/ubuntu/9.04/i386
#ubuntu 9.10:
sudo cp /mnt/casper/initrd.lz /var/lib/tftpboot/ubuntu/9.10/i386
sudo cp -R /mnt/* /myth/install/ubuntu/9.10/i386
sudo umount /mnt

#menu:
sudo mkdir -p /var/lib/tftpboot/ubuntu/
sudo touch /var/lib/tftpboot/ubuntu/ubuntu.menu
#the tftp paths are relative to /var/lib/tftpboot.
sudo nano /var/lib/tftpboot/ubuntu/ubuntu.menu
LABEL 2
        MENU LABEL 9.10 Gnome Live (32-bit)
        KERNEL ubuntu/9.10/i386/vmlinuz
        APPEND boot=casper netboot=nfs nfsroot=192.168.153.20:/myth/install/ubuntu/9.10/i386 initrd=ubuntu/9.10/i386/initrd.lz
        TEXT HELP
        Boot the Ubuntu 9.10 Live CD
        ENDTEXT
LABEL 1
        MENU LABEL 9.04 Gnome Live (64-bit)
        KERNEL ubuntu/9.04/amd64/vmlinuz
        APPEND boot=casper netboot=nfs nfsroot=192.168.153.20:/myth/install/ubuntu/9.04/amd64 initrd=ubuntu/9.04/amd64/initrd.gz
        TEXT HELP
        Boot the Ubuntu 9.04 Live CD
        ENDTEXT

---

### Post by TyTiger on 2010-08-04
Hi, thanks for the reply, 

The text i have in my PXE menu is: 
label Ubuntu 10.04 LTS LIVE
		MENU LABEL Ubuntu 10.04 LTS (Experomental)
		kernel bootimages\ubuntu\vmlinuz_ub104
		append initrd=bootimages\ubuntu\initrd_ub104.lz root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.250:/mnt/ubuntu104/ splash=silent

(the _ub### at the end of the images denotes versions as i have more than one image in the tftp folder) 

this isn't working though (obviously) i cant figure out what needs adding, taking away etc

thanks

---

### Post by TyTiger on 2010-08-04
> **TyTiger said:**
> Hi, thanks for the reply, 

The text i have in my PXE menu is: 
label Ubuntu 10.04 LTS LIVE
		MENU LABEL Ubuntu 10.04 LTS (Experomental)
		kernel bootimages\ubuntu\vmlinuz_ub104
		append initrd=bootimages\ubuntu\initrd_ub104.lz root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.250:/mnt/ubuntu104/ splash=silent

(the _ub### at the end of the images denotes versions as i have more than one image in the tftp folder) 

this isn't working though (obviously) i cant figure out what needs adding, taking away etc

thanks

I changed the "APPEND" line to the following, but still no luck. same error

APPEND boot=casper netboot=nfs nfsroot=192.168.1.250:/mnt/ubuntu104/ initrd=bootimages\ubuntu\initrd_ub104.lz

---

### Post by raysolomon on 2010-08-06
Here, see if you can make sense of this.
I don't have time to explain it but I can easily setup any Debian in a snap if I need to. I basically dedicate one machine(laptop) that acts as a dhcp/tftp/pxe server. If it does not help, sorry.

[http://ray-solomon.com/tech/networking/pxe-boot-server/](http://ray-solomon.com/tech/networking/pxe-boot-server/)


I'm not a fan of TFTPd32

---

### Post by TyTiger on 2010-08-06
> **raysolomon said:**
> Here, see if you can make sense of this.
I don't have time to explain it but I can easily setup any Debian in a snap if I need to. I basically dedicate one machine(laptop) that acts as a dhcp/tftp/pxe server. If it does not help, sorry.

[http://ray-solomon.com/tech/networking/pxe-boot-server/](http://ray-solomon.com/tech/networking/pxe-boot-server/)


I'm not a fan of TFTPd32

Still not getting anywhere thanks though

---

### Post by c0mm on 2010-09-23
I don't think your network card is even being detected.

---

### Post by c0mm on 2010-09-23
Oh and take out splash=silent so you can see more information.

---

### Post by TyTiger on 2010-09-24
> **c0mm said:**
> I don't think your network card is even being detected.

I know its a bit random, its hard to tell what's going on because that's literally all it gives you, Even with boot splash, off nothing I can see that's of any use, most of its gone too fast to read in any case... i wonder if this is fixed in 10.10

---

### Post by naptastic on 2011-02-12
(I found this thread by googling to find out if the 10.10 live image can be network booted. Why is it so freaking hard to get a live image that isn't corrupted in some way?!)

I am pretty sure, having done my share of network boots on both Ubuntu and Fedora, that the initrd file that's part of the live image does not contain the correct modules for your network card, and therefore will not be able to boot completely.

I just tried booting the live image using a kernel / initrd combination that I already know work for network booting, and they failed, getting stuck with an error, "mount: device or resource is busy", repeating indefinitely. I don't know how to fix that.

The kernel / initrd for the live image probably has some weird option for booting, like init=/some/bizarre/program or something, making it incompatible with a stock kernel combo. Grr!!

---

### Post by TyTiger on 2011-02-13
> **naptastic said:**
> (I found this thread by googling to find out if the 10.10 live image can be network booted. Why is it so freaking hard to get a live image that isn't corrupted in some way?!)

I am pretty sure, having done my share of network boots on both Ubuntu and Fedora, that the initrd file that's part of the live image does not contain the correct modules for your network card, and therefore will not be able to boot completely.

I just tried booting the live image using a kernel / initrd combination that I already know work for network booting, and they failed, getting stuck with an error, "mount: device or resource is busy", repeating indefinitely. I don't know how to fix that.

The kernel / initrd for the live image probably has some weird option for booting, like init=/some/bizarre/program or something, making it incompatible with a stock kernel combo. Grr!!

10.10 does boot over network compared to 10.04, I know the 10.04 Net install images (Text install) work over PXE however. 

If you need me to walk you through it, Send me a PM. :popcorn:

---

### Post by mrebholz on 2012-05-08
Hi all, I've read this post and similar ones with interest. Did anyone get anywhere with it or know of any potential resolution or was 10.04 just broken as far as PXE netboot goes and wasn't going to be fixed?


Aim: To get edubuntu 10.04 to boot and install over the network using PXE but *not* to download the edubuntu files from the internet but to take the files from the ISO (extracted) on the server. 

Setup: I'm using a Windows 2003R2 server with WDS configured and using PXElinux to boot the workstation into a custom menu with the Linux options.I used this guide to help me (URL). I am therefore using the files under /casper from this distro which by all accounts are supposed to be netbootable (so one would assume nfs-capable). Furthermore, MS-nfs is configured on the server with 'everyone read' and anonymous access to share the extracted ISO contents. The root of the ISO contents is exported as /ubuntu1004 (so /casper with squashfs as a content is a subdir). I have checked that nfs is configured ok by using another Ubuntu 10.04 desktop to mount this export by creating an empty dir /ubuntu1004 under /mnt and using sudo mount -t nfs serverip:/ubuntu1004 /ubuntu1004 and that works. I can then read the whole contents from that desktop.

Problem: The vmlinuz kernel loads fine, and so can the ramdisk image initrd.gz from the initial PXE boot folder on the server. The issue seems to be with mounting/parsing/just damn using the nfs-served squashfs load. I get the error message during setup that 'NFS over TCP is not available from 192.168.1.20 connect: Network is not available'. I know that's simply not true though, as (a) it works on an already-built ubuntu 10.04 desktop mount and (b) I've broken back to the command line in this pxe-boot system (initramfs) and do an ifconfig which returns valid info. I can also check on the DHCP server and see the machine's valid lease.

If I wait long enough then I also get another error "FATAL: could not load /lib/modules/2.3.32-21-generic/modules.dep: No such file or directory" but that could be because it has now given up trying to mount the nfs drive and get the squashfs file?

Here is the contents of the pxeconfig default file

label Ubuntu1004
menu label Edubuntu 10_04
KERNEL /linux/edubuntu/vmlinuz
append break=init root=/dev/nfs netboot=nfs boot=casper nfsroot=192.168.1.20:/ubuntu1004/casper ip=dhcp initrd=/linux/edubuntu/initrd.gz

So I've reached a conclusion that one of the following is wrong:
1. I need additional arguments in my default pxeconfig file, but I don't know which. Other folks seem to have it working with what I have in mine, and/or
2. The kernel/ramdisk used are for some reason NOT nfs-capable. Is there any way to check for the right versions (I took them from the /casper dir of the official edubuntu 10.4 release ISO 

Can anyone please shed any light on what it might be and help me troubleshoot further?



[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

---

### Post by Jonathan L on 2012-05-11
Hi mrebholz

>  get edubuntu 10.04 to boot and install over the network using PXE but *not* to download the edubuntu files from the internet but to take the files from the ISO (extracted) on the serverI tried my instructions ([http://ubuntuforums.org/showthread.php?p=11888507](http://ubuntuforums.org/showthread.php?p=11888507)) with the Edubuntu 10.04 DVD image and it works perfectly -- or fails -- depending on your hardware.
I've had the exact same message as yours on various hardware: > 'NFS over TCP is not available from 192.168.1.20 connect: Network is not available'In my case, it was caused by a kernel which doesn't have the driver for the ethernet card in your computer.  (It absolutely doesn't mean anything about the varioius UDP vs TCP options of NFS.)  The driver which TFTP-loaded the kernel and initrd.lz is the one built into the firmware of the ether card; the driver which fails to load the NFS is the one from the kernel.

Suggestions:
1.  Add an ether card which is supported by the kernel you're using.
2.  Add the kernel modules for the ether card you're using (see optional steps in my notes)
3.  Use a later edubuntu which whose kernel has drivers for your card.



Hope that's helpful for you.

Kind regards,
Jonathan.

---

### Post by mrebholz on 2012-05-17
Now I'm all done, I'm happy to share the HOW-TO on this. I hope anyone else searching for help on this like I was a couple of weeks ago can use it...
 
[http://rebholz.wordpress.com/2012/05/17/technical-how-to-installing-linux-edubuntu-using-pxe-boot-and-windows-7-as-a-server/](http://rebholz.wordpress.com/2012/05/17/technical-how-to-installing-linux-edubuntu-using-pxe-boot-and-windows-7-as-a-server/)

---


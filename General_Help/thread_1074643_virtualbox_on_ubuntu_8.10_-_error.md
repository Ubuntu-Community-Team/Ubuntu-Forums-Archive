---
title: "virtualbox on ubuntu 8.10 - error"
date: 2009-02-19
forum: General Help
---

### Post by hockman5 on 2009-02-19
I am trying to install virtualbox and I get this error. What does it mean? I can't have virtualbox?

Setting up virtualbox-ose-source (2.0.4-dfsg-0ubuntu1) ...
 * Reloading kernel event manager...                                     [ OK ] 
Adding Module to DKMS build system
Doing initial module build

Error! Your kernel source for kernel 2.6.27-11-generic cannot be found at
/lib/modules/2.6.27-11-generic/build or /lib/modules/2.6.27-11-generic/source.
Installing initial module

Error! Could not locate vboxdrv.ko for module vboxdrv in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.
Done.
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
Setting up virtualbox-ose-source (2.0.4-dfsg-0ubuntu1) ...
 * Reloading kernel event manager...                                     [ OK ] 
Adding Module to DKMS build system
Doing initial module build

Error! Your kernel source for kernel 2.6.27-11-generic cannot be found at
/lib/modules/2.6.27-11-generic/build or /lib/modules/2.6.27-11-generic/source.
Installing initial module

Error! Could not locate vboxdrv.ko for module vboxdrv in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.
Done.
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.

---

### Post by konqueror7 on 2009-02-19
its better to use the non-OSE version in my opinion, here's a [guide]("http://ubuntuforums.org/showthread.php?t=1074160")

---

### Post by hockman5 on 2009-02-19
> **konqueror7 said:**
> its better to use the non-OSE version in my opinion, here's a [guide]("http://ubuntuforums.org/showthread.php?t=1074160")

Followed the link and it works great. Just installed WINXP in Ubuntu and getting ready to install Quicken. If that works, I can say goodbye to Microsoft.

---

### Post by Mercury_Alpha on 2009-02-19
> **hockman5 said:**
> Followed the link and it works great. Just installed WINXP in Ubuntu and getting ready to install Quicken. If that works, I can say goodbye to Microsoft.

Don't forget to enable Guest Additions :)  It allows you to move your mouse pointer smoothly between the host desktop and the VM, among other things. And there's Seamless Mode. It's nifty.

You'll also want to tweak how much video memory the VM gets. By default, it's only 8MB.

---

### Post by hockman5 on 2009-02-19
Well I had it all set up and installed and running, and installed quicken.
Everything was working great, then I shutdown Windows, closed VirtualBox, and when I went to open it to start it again, the machine is gone. Do I have to install everything all over again? I created a seperate folder on my serial drive for the stuff but it looks like it is going to start me over from scratch. How do I get VB to remember the machine?
Maybe my problem was running it from a terminal?  oops.

---

### Post by hockman5 on 2009-02-19
OK I figured how to set it back up and use the existing location so I didn't have to reinstall. I created a shortcut to run VB and it remembers the machine now. wheeew that was close.
Thanks again for your help, I will install the guest now.

---

### Post by howefield on 2009-02-19
What is the output from the terminal if you try and start it from there, ie

VBoxManage startvm nameofyourvm

Edit, ok I see you are sorted  :)

---

### Post by hockman5 on 2009-02-23
I got VB installed and running. I set assign 50 gig on a SATA drive for this. When I start installing software (Quicken, MS Office, etc) I receive an error stating that the file size exceeds the allowable for my file system. Move it to a different filesystem. I formatted that file system as NTFS. My only way out is to recreate the hole machine again, including the virtual disk. Then I get a little farther and the error message hits again. Any clues why my NTFS has file size limits that aren't very big? The last time it happen I was installing software for a printer. The download was only 45mb (compressed). Any clues?

---

### Post by hockman5 on 2009-02-24
I figured it out. I had the virtual disk installed on an SATA drive that was format with Fat32 even though in VirtualBox I set it to format the file in NTFS. Duh, It didn't even dawn on me that the real harddrive had to be NTFS as well..... FIXED!!!

---


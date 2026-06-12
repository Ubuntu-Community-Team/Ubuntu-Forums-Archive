---
title: "Expert install without bootloader?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by kikinovak on 2006-07-27
Hi,

One of the few things that I don't like about Ubuntu is that a "normal" install just installs GRUB on my MBR without asking... which is bad manners, a thing you normally only encounter with M$-crap. On my testing machine, I have no less than ten different distros in various configs, and I hate having to write my menu.lst from scratch again.

Even the install in 'text mode' doesn't offer the option of installing no bootloader... or is there a special CD offering this? The local LAN here has a mix of Ubuntu server with some Ubuntu and Xubuntu clients.

Cheers.

---

### Post by go2dell on 2006-07-27
Have you tried the Alternate Install CD?  You can drop down to the full Debian installer and proceed step-by-step through the whole thing, which should allow you to bypass bootloader installation completely.

---

### Post by kikinovak on 2006-07-27
That's exactly what I'm looking for!

Are there Alternate CD's for Ubuntu Server and Xubuntu as well?

---

### Post by jacquelineZ on 2006-07-27
I don't like automatic installers ( and automatic partitionners : the worst  ! ) but  we can't always escape to their bad jokes.. ( i use and test  several systems..)

 So i've a boot partition, and i let the installer works on the directory boot of the new system. Sometimes it changes the MBR  and runs the grub menu of the boot directory of the new system ( no problem  let it work ! no stress !).

Then, when this new system runs correctly,  you can run the grub of the boot partiton to get a correct  MBR and a correct multiboot with  a fine menu.lst  ( You can use Live CD to change this )

If you get  lost, you can edit the menu.lst to know which grub is working at the boot time... ( Sometimes i don't know...)

 Sometime you can install the bootloader on a floppy disk at the beginning for a new system, or choose not install the boot loader  when it's possible. You just have to edit the menu list of the main bootloader on the boot partition to run all your systems.. 

I'm found of Grub...you can do a lot with Grub..

Grub is a bootloader, but also an "autonom program" to install itself in the right place....when you need. 

For partitions, I fix them one time at the beginning for several systems and i install in "expert mode" to avoid very bad surprises. I use labels not to be lost in my partitions.. 

Ubuntu desktop 6.06 works correctly :), and i throw others, like mandriva with diskdrake : the worst installer in the world : It does not know the basic "partitions" : primary, extended and logical, to help newbies, but it's a very bad education and they cry because they loose their old  partitions )

 Jacqueline

---

### Post by compuguy1088 on 2006-07-27
[QUOTE=kikinovak]Are there Alternate CD's for Ubuntu Server and Xubuntu as well?[/QUOTE]
I know definatly for a fact that there is an alternate installer for Xubuntu, but for the server version, I don't think there is one....

---

### Post by doobit on 2006-07-27
> **kikinovak said:**
> Hi,

 I hate having to write my menu.lst from scratch again.

Cheers.

I always keep a spare copy of my last menu.lst on a pendrive and also on a partition of my hard drive that I will never format.

---

### Post by go2dell on 2006-07-27
Yes, there is an Alternate Install for the Big Three:  Ubuntu, Kubuntu and Xubuntu.  There is not an Alternate Install for Server, since it doesn't run a full GUI desktop in the first place (talking about the Server CD, not installing Server from a Desktop CD).

You'll need to go to [http://www.ubuntu.com/download]("http://www.ubuntu.com/download") and select your mirror, then grab either the ISO or torrent link from there.

The Alternate Install is especially useful for Xubuntu.  The GUI sometimes is too slow or completely unable to run on very low-end systems, but the text-based installer runs fine and gives you a running system.

---

### Post by Herman on 2006-07-28
If you would like to see an illustrated web site that goes into great details about how to use the 'Alternate' CD installer and partitioner, here is the link to the main page: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

There you will find, if you look around and read enough, just about everything you can think of do with Ubuntu and bootloaders. If I have missed something you would like to see added, just P.M. me and let me know. I edit bits  of the site every weekend at least, to make sure it's what people want and try to keep it up to date.  
Here is a link to the part of it that deals with all the choices the 'Alternate' CD has for installing a bootloader, [http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu](http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu)
If you look carefully at **fig 12 mbr**, there, you will even see an option for '**Continue without  bootloader**' if you want that.

Regards, Herman :D

EDIT: I do not discuss the use of Windows NTLDR and boot.ini to boot Ubuntu though. I consider that to be a Windows subject, not a Linux (Ubuntu) one. There are already enough websites about that in any case.

---

### Post by kikinovak on 2006-07-29
Thanks for all the detailed replies. Being a Slackware user since 2001 or so, I'm all for text installers and simple tools: fdisk, mke2fs, tune2fs, ...

I've been working until recently on a custom Slackware-based distro with XFCE and some GNOME libs. Tried Zenwalk, but building on -current is a no-no for me, I hate moving targets. Building even a base GNOME from scratch is a bear, and I soon ended up with hundreds of build scripts... until I discovered Xubuntu had more or less exactly what I was looking for. Nice work, indeed. (OK, some things I don't like about it, so I just tweak them...)

Cheers.

---


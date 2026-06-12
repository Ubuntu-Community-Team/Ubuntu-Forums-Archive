---
title: "Qemu problem with Gutsy"
date: 2007-10-19
forum: Desktop Environments
---

### Post by SteveF on 2007-10-19
I installed Gutsy and chose Qemu from Synaptic.  I have an image for Qemu already created.  That image works fine under Feisty with whatever version of Qemu is in the repositories there.  The image has Windows 98 installed.

When I load Qemu, Windows 98 starts to load and then I get "Window Protection Error.  You need to restart your computer."

I reloaded Feisty and the image loads without problems.

Has anyone else has problem running Qemu under Gutsy?

Steve

NOTE:  I meant to put this under General, clicked on wrong link.  Is there a way to move it?

---

### Post by lynrees on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There seem to be problems with qemu in gutsy. I've got a Win 2K3 and a centos 5 image working fine, but I've had problems with opensuse 10.3 and gutsy.

the ata_piix.blacklist=yes grub kernel line fixed worked, and gutsy seemed to install fine, but now it won't boot claiming that it can't find its disk!

Any body know what's going on?:confused:

---

### Post by jellybear on 2007-10-20
I'm having the same problem, if you boot your 98 image to safe mode and set it to 640x480x16colors you can boot into normal mode, but using higher graphics settings causes the protection fault for some reason.

---

### Post by Zeroedout on 2007-10-22
Hey. I'm using qemu with the usb multi-configs patch, and when i load the xp image, it freezes on ndis.sys (sademode anyway, I can't tell where it freezes in the normal boot). I was thinking it was the patch, as I never tried the unpatched version in gutsy, but I don't think the multiconfig patch would effect boot like that. Should we file a bug report at launchpad?

---

### Post by flinkdeldinky on 2007-10-22
I've got a problem with the new qemu too.  I use qemu to run Ubuntu Server 7.04 so I can learn about setting up a server and running drupal, etc.

In fiesty this command would work fine (my actual start up command is more complex  than this):
qemu-system-x86_64 -S ubuntu-server.img -m 378

But the same command in Gutsy fails to successfully boot up.  It gets me to the point were it would (eventually) drop me into initramfs with an ash shell.  I don't think qemu can see the what's supposed to be the hard disk.

When I first start the qemu command a bios screen flashes but it's to quick to read.  But I definately see something near the top of the screen that seems to indicate that you've got the option of using switching between 3 different bios's.  Any ideas about that?

PS. How do I downgrade to the old Ubuntu 7.04 qemu?  I need to get my server image up and running?

---

### Post by lavagolemking on 2007-10-24
It freezes for me when I try to boot Windows XP in version 7.10.

---

### Post by SteveF on 2007-10-25
I've downgraded to the Feisty version and that has solved my problem.  One other issue though, I get told there is an update waiting all the time.  Is there a way to turn that off, but just for Qemu?

Steve

---

### Post by ahaslam on 2007-10-26
> **flinkdeldinky said:**
> It gets me to the point were it would (eventually) drop me into initramfs with an ash shell.
I get this trying to run the xubuntu live iso.

---

### Post by ahaslam on 2007-10-28
Works perfectly in Arch, same version: 0.9.0 :-?

---

### Post by flinkdeldinky on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185](https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok guys, looks like this problem was, as suspected, BIOS related.  The old Feisty Qemu used the BIOS that is included in Qemu.  The Gutsy Qemu uses the bochs (processors emulator) BIOS.

The problem is Gutsy's bochbios package is no good.

However, there's a Debian package package that you can install that will fix it.

I found out about this on this launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185](https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185)

Go here:
[http://packages.debian.org/lenny/bochsbios](http://packages.debian.org/lenny/bochsbios)

grab the debian package and use:
dpkg -i bochsbios_2.3+20070705-2_all.deb

My ubuntu server image and XP image run perfectly now.

---

### Post by ahaslam on 2007-10-29
Thanks for the info ;)

---

### Post by schorem on 2007-10-31
Tried the Bochs Bios from Debian with qemu 0.9 and a Gutsy 7.10 image it still drops into initrmfs (BusyBox). Any solutions?

I get the following error:

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/5beed6d0-bc8b-4224-8d89-4720c2f9d58 does not exist. Dropping to a shell!

When I ls /dev there are no folders called by-uuid.

EDIT: I am reinstalling a VM with Gutsy. Seems to be working fine until now

UPDATE: After installing the Debian package for Bochs Bios and reinstalling Ubuntu 7.10 as a commandline system. it actually works :)

---


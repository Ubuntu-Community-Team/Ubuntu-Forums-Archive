---
title: "OpenOffice will not start"
date: 2006-07-11
forum: Desktop Environments
---

### Post by hsmith on 2006-07-11
I installed the latest version of Ubuntu from the CD download and for the most part I have been very pleased. 

I am running an IBM T42 Thinkpad.

Everything seems to start up and run just fine except for Open Office.  When ever I try to start this program, from the menu or from Terminal I get the following error.

herm@herm-laptop:~$ ooffice -writer

no suitable windowing system found, exiting.

 

** (process:5744): WARNING **: Unknown error forking main binary / abnormal early exit ...

herm@herm-laptop:~$


I've tried everything that I can think of but nothing seems to work. I uninstalled and reinstalled both the Open Office program and the entire OS.

I would appreciate any help or ideas this forum may have to offer.

Thanks,

HSmith

---

### Post by wpshooter on 2006-07-11
Did you check the integrity of your ISO image download by running the sum check utililty that is shown on the initial boot screen ?

P. S. - some further research, seems to indicate that this is a problem related to video card drivers.

What video card are you using ?

---

### Post by hsmith on 2006-07-12
The ThinkPad T42 has a Mobility Radeon 7500 AGP [LW], ATI Technology Inc Compatible video adapter in it.

Thanks for your response.

HSmith

---

### Post by kevin1 on 2006-07-16
Hi hsmith,

I have the same problem, except I can run OO by doing 'sudo nautilus --browser', then double-clicking on an OO document. I don't think it is a driver issue.

This thread shows what I have tried without success:

[http://www.ubuntuforums.org/showthre...ght=openoffice](http://www.ubuntuforums.org/showthre...ght=openoffice)

Kevin

---

### Post by Amaroq on 2007-04-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/32827](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/32827) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having the same problem, and i'm using 32 bit.

I managed to fix it though by reinstalling a bunch of packages.

Paste this into a terminal.

```
sudo aptitude reinstall alsaplayer-common apache-common evolution-data-server evolution-data-server-dbg evolution-dbg evolution-plugins gnucash gnusound gstreamer0.8-audiofile kdelibs-dbg kdelibs4-dev kdelibs4c2alibaudiofile-dev libc6 libc-dbg libc6-i686 libggi2 libgii0 libgnome-vfs-common libgnomepring2.2-0 libgnomevfs2-0 libgnomevfs2-0-dbg liblockfile-dev liblockfile1 liblockfile1-dev libvorbis-dev libvorbisfile-ruby1.6 libvorbisfile-ruby1.8 libvorbisfile3 libxine-main1 python2.4-kde3
```

I have absolutely ***no*** idea which one of these fixed it. I just know it worked.

If anybody's got some free time on their hands, perhaps they could go through reinstallation of these one by one to determine which one it is.

Whether or not you're lookin for the quick fix or the one-by-one-and-let-us-know fix, no need to worry about whether or not you actually have those packages. If it isn't installed yet, aptitude skips it.

---

### Post by benner on 2007-04-09
anyone know if this will work on a 64-bit?  i'm running feisty 64 with an ati x550 chipset on an asus graphics card.

---

### Post by DChamp on 2008-07-01
Didn't work for me on 32bit.

---


---
title: "gtkpod with SLVR"
date: 2006-02-22
forum: Desktop Environments
---

### Post by souled on 2006-02-22
I picked up a Motorola SLVR L7 this past weekend, and I am wondering how to use gtkpod with it. When I try to read the iTunesDB, gtkpod tries to read the file from ~/iPod_Control/iTunes/iTunesDB. However, the SLVR L7's iTunesDB is located at ~/iTunes_Control/iTunes/iTunesDB. How can I change the path that gtkpod looks to find iTunesDB?

---

### Post by souled on 2006-02-23
Can anyone help?

---

### Post by Zodiac on 2006-02-23
Check the Ubuntu Wiki B!

> Getting started with gtkpod

PLEASE NOTE: This is for Hoary Only. These instructions are not needed on Breezy!

Before using gtkpod, there are a few system settings that you have to change to make things work properly.

First, create a directory called /mnt/ipod to serve as a mount point for the iPod (do a sudo mkdir /mnt/ipod at a terminal). Then, edit your /etc/fstab file (sudo nano /etc/fstab will work for this) and add the following line to the end of the file:

/dev/sda2               /mnt/ipod               auto    noauto,user,rw 0 0

This is assuming that you are using a PC-formatted iPod, and that the iPod appears to the system as /dev/sda (which is the case if you have no other devices using the SCSI interface connected). In other cases, your device name will be different (you can check this by looking at dmesg in a terminal).

Secondly, you will have to change the sudoers setup so that gtkpod can "eject" the iPod (allowing it to be disconnected safely) after use. To do this, add the following to /etc/sudoers (you MUST use "sudo visudo" to edit this file):

%username         ALL=NOPASSWD:/usr/bin/eject /dev/sda2

(substitute your username for username, and the actual device name for /dev/sda2 if it is different)

Finally, you have to set up gtkpod to "eject" the iPod when it is closed. To do this, create a new file called ~/.gtkpod/gtkpod.out (create the .gtkpod directory in your home directory first) containing the following text:

sudo /usr/bin/eject /dev/sda2

(once again, substitute your device name if different from /dev/sda2)

You should now be set to use gtkpod to sync your iPod - plug your iPod in, launch gtkpod (Applications --> Sound & Video --> gtkpod), and load your favorite MP3s or AACs to your iPod (be careful, since you can lose the contents of your iPod). Once you close gtkpod, the iPod will be safe to disconnect (the "Do not disconnect" message will disappear). 

---

### Post by souled on 2006-02-23
Thanks for the response. I can get my SLVR to mount at /dev/sda1, but mounting the phone isn't my problem. My problem is gtkpod looking at the wrong directory for iTunesDB. On an iPod, iTunesDB is located at /iPod_Control/iTunes/iTunesDB. On my SLVR, iTunesDB is not located at this directory. it is located at /**iTunes**_control/iTunes/iTunesDB. I need to change the path that gtkpod searches for iTunesDB.

---

### Post by Schmots on 2006-05-11
Anyone found out how to do this yet?

---

### Post by ComplexNumber on 2006-05-11
have a read of [this]("http://tuxmobil.org/").

---

### Post by souled on 2006-05-11
I helped the developer of gtkpod and libgpod to support the SLVR. Try installing the latest versions... They might work if they're recent.

---

### Post by Pcmikepl on 2006-05-11
hmmm... how about creating a link to that iTunesDB on the phone itself?

---

### Post by cam1968 on 2006-05-17
[QUOTE=souled]Thanks for the response. I can get my SLVR to mount at /dev/sda1, but mounting the phone isn't my problem. My problem is gtkpod looking at the wrong directory for iTunesDB. On an iPod, iTunesDB is located at /iPod_Control/iTunes/iTunesDB. On my SLVR, iTunesDB is not located at this directory. it is located at /**iTunes**_control/iTunes/iTunesDB. I need to change the path that gtkpod searches for iTunesDB.[/QUOTE]

I had this problem using a Motorola E1 ROKR with latest **CVS** gtkpod & libgpod.

Try backing up and then removing the iPod_Control directories.
Gtkpod & libgpod looks for iPod_Control first, followed by iTunes/iTunes_Control/iTunes.
If it finds the iPod_Control directory first it won't look anywhere else.

If that fails get the latest **CVS versions** of gtkpod and libgpod and make sure there are no iPod_Control directories on your phone.

---

### Post by damotor on 2006-05-25
[QUOTE=cam1968]I had this problem using a Motorola E1 ROKR with latest **CVS** gtkpod & libgpod.

Try backing up and then removing the iPod_Control directories.
Gtkpod & libgpod looks for iPod_Control first, followed by iTunes/iTunes_Control/iTunes.
If it finds the iPod_Control directory first it won't look anywhere else.

If that fails get the latest **CVS versions** of gtkpod and libgpod and make sure there are no iPod_Control directories on your phone.[/QUOTE]
cam1968, can you tell us what's the CVS version wich includes rokr support? pls

---

### Post by xhie on 2006-06-09
I just bought the same phone, the pink slvr is so sexxy. 

When I plug my phone in it mounts to /media/usbdisk and my phone displays a message saying it was mounted as a storage device and some features my not be avalable. Does anyone know how to fix this?

---

### Post by damotor on 2006-06-16
Yamipod works like a charm with rokr [http://www.yamipod.com](http://www.yamipod.com)

---

### Post by bigdaddyjohn on 2006-06-20
I can't get it to work with my ROKR. Any help would be appreciated. In fact, the only way to sync the phone is to use Windoze and iTunes. That defeats my current efforts to be windose free. I've tried Banshee, Amarok, gtkpod, Yamipod, etc. They all seem to recognize ipods just fine. Problem is the folder structure in the phone. It's slightly different than an iPod.

bigdaddyjohn

---

### Post by souled on 2006-06-21
Hmmm... I tried Yamipod too, and it seems unstable. I got it to recognize some songs on my SLVR, but I couldn't add anything becuase it kept crashing. According to Jorg Schuler (gtkpod maintainter) The SLVR is written in reverse endian mode (whatever that means), which is why the programs won't recognize the phones. I am currently having trouble with the latest CVS version of gtkpod. It keeps crashing when I try to set a mountpoint. I helped Jorg out a few months ago with getting the SLVR to work so the newer CVS versions should support the phone, however, I am unable to get gtkpod to work =(. When I try the older versions that Jorg sent me (with mobile support) gtkpod won't even load at all. The files worked under Breezy, so something must be different with Dapper. 

bigdaddyjohn, did you try using the CVS version of gtkpod? If you haven't, try it out and post your results here. 

Thanks

---

### Post by bigdaddyjohn on 2006-06-21
Well I hate to admit that I'm not an Ubuntu Guru. Windows Guru yes, Ubuntu, no. (Although I'm leaving windoze in the dust....)   So I'm not really sure what version of gtkpod I have. I installed via Synaptic if that helps you. I have tried searching for info regarding the SLVR 6 and SLVR 7 as the ROKR isn't "in vogue" anymore. The directory structure appears the same. If anyone has made the SLVR work, please tell how you did it.

bigdaddyjohn

---

### Post by cam1968 on 2006-06-27
[QUOTE=damotor]cam1968, can you tell us what's the CVS version wich includes rokr support? pls[/QUOTE]


I am using GtkPod 0.99.6CVS and libgpod 0.3.3 which I got using the instructions on the GtkPod website for CVS downloads.
I recently tried a newer CVS and it wouldn't compile on my system and I don't know how to get older versions using this method.

Another gotcha is to make sure that there are some folders named from f00 to f19 under the <mountpoint>/iTunes_Control/iTunes/Music/  directory. 
If there aren't any GtkPod will try and recreate the folders you need to delete, ie <mount_Point>/iPod_Control/iTunes/...;. I made the mistake of not having them after deleting too many files when I ran out of space.

---

### Post by Floola on 2006-07-12
floola should support ROKR as well, [www.floola.com](www.floola.com)

If you can give it a try please report.

Thanks,
Tomas

---

### Post by error27 on 2006-07-18
I guess the first time you use an iPod iTunes sets up a bunch of directories and your itunes db.

I used gnupod_INIT and that almost worked.  :P  But not quite.

---

### Post by error27 on 2006-07-18
Actually the gnupod_INIT thing did work.

Here are the steps that I went through.  Skip the ones that made me curse a bit.

1)  gnupod_INIT -m /media/ipod
2)  gnupod_addsong -m /media/ipod foo.mp3
3)  that didn't work
3a)  gnupod_check says everything is fine.
4)  Use gtkpod to copy an mp3 over.  that worked.
5)  gnupod_check says that first mp3 is a waste of space.  delete it.

6)  use gktpod for everything else.

---

### Post by sonoma on 2006-07-18
> **cam1968 said:**
> I am using GtkPod 0.99.6CVS and libgpod 0.3.3 which I got using the instructions on the GtkPod website for CVS downloads.
I recently tried a newer CVS and it wouldn't compile on my system and I don't know how to get older versions using this method.
...snipped...

I just got the source files for GtkPod 0.99.4 and compiled on my Ubuntu Dapper. It works great. However 0.99.6CVS is supposed to keep bookmarks like iTunes does according to the changelog (if I read it right).

I can get the compiled files to you or point you to the source and tell you how it worked for me. Do you have the 0.99.6 files or a pointer to them? I couldn't find a working (compilable) 0.99.6CVS?

---

### Post by starscalling on 2006-08-07
none of these things work with my cingular branded slvr ~_~
however ive grabbed a copy of DAP and tossed that in so i can toss stuff into my phone music direcory etc ~_~

---

### Post by christhemonkey on 2006-08-07
Cant remember if anyone answered your question souled;
 ~/iPod_Control/iTunes/iTunesDB to ~/iTunes_Control/iTunes/iTunesDB.

```
mkdir ~/iPod_Control/iTunes
sudo ln -s ~/iTunes_Control/iTunes/iTunesDB ~/iPod_Control/iTunes/iTunesDB 
```

(although, it is unlikely that ~/ is where all these files are? That is your home directory...)

---

### Post by starscalling on 2006-08-08
nope
no symbolic links allowed on phone itunes db
:/

---

### Post by clink on 2006-10-28
It looks like the latest release of gtkpod ( 0.99.8 ) has the iTunes mobile support in it. Here's how I built myself the latest version on ubuntu dapper using the latest version downloaded from gtkpod.sf.net

Step 1: Download latest gtkpod & libgpod source from gtkpod.sf.net

Step 2: Prep system for build
[FONT="System"]
sudo apt-get build-dep gtkpod libgpod0
sudo aptitude install devscripts fakeroot
apt-get source gtkpod libgpod0 [COLOR="DimGray"]# Note: You'll need the dapper deb-src entries in your /etc/apt/sources.list[/COLOR]
[/FONT]

Step 3: Build & Install libgpod
[FONT="System"]
cd libgpod-0.3.2
uupdate ../libgpod-0.4.0.tar.gz
cd ../libgpod-0.4.0
fakeroot dpkg-buildpackage -b -uc
sudo dpkg -i ../libgpod0_0.4.0-1_i386.deb ../libgpod-dev_0.4.0-1_i386.deb
[/FONT]

Step 4: Build & Install gtkpod
[FONT="System"]
cd ../gtkpod-0.99.2
uupdate ../gtkpod-0.99.8.tar.gz
cd ../gtkpod-0.99.8
rm debian/patches/02-japanese_charset.dpatch debian/patches/00list [COLOR="DimGray"]# wasn't able to apply this patch to the new rev[/COLOR]
fakeroot dpkg-buildpackage -b -uc
sudo dpkg -i ../gtkpod_0.99.8-1_i386.deb
[/FONT]

---

### Post by PedroCastro on 2006-10-31
Worked with my Motorola Rokr E1!!! Thanks man

---

### Post by drobvice on 2006-11-12
I am following this guide on edgy and I get to this step:

uupdate ../libgpod-0.4.0.tar.gz

And it stops and asks

File to Patch:  See below.

New Release will be 0.4.0-1.
Symlinking to pristine source from libgpod_0.4.0.orig.tar.gz...
-- Untarring the new sourcecode archive ../libgpod-0.4.0.tar.gz
The text leading up to this was:
--------------------------
|--- libgpod-0.3.2.orig/bindings/python/examples/play.py
|+++ libgpod-0.3.2/bindings/python/examples/play.py
--------------------------
File to patch:   


Huh?  I'm lost.

---

### Post by giruzz on 2006-12-17
> **drobvice said:**
> I am following this guide on edgy and I get to this step:

uupdate ../libgpod-0.4.0.tar.gz

And it stops and asks

File to Patch:  See below.

New Release will be 0.4.0-1.
Symlinking to pristine source from libgpod_0.4.0.orig.tar.gz...
-- Untarring the new sourcecode archive ../libgpod-0.4.0.tar.gz
The text leading up to this was:
--------------------------
|--- libgpod-0.3.2.orig/bindings/python/examples/play.py
|+++ libgpod-0.3.2/bindings/python/examples/play.py
--------------------------
File to patch:   


Huh?  I'm lost.

Hi,

have you solve your problem? I got the same here...

bye

g.

---


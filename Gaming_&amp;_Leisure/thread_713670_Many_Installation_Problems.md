---
title: "Many Installation Problems"
date: 2008-03-03
forum: Gaming &amp; Leisure
---

### Post by LynxKItten on 2008-03-03
Hi! I installed Ubuntu a month back, and I think I've figured out the basic stuff. 

But I seem to have some problems running games and installation disks (the ones you get with mp3 players and mobiles). I've got Wine installed, and the setup runs fine. But after installation, I am unable to run the required programs. Double clicking on the icon on the desktop doesn't open any window, though it shows the round hourglass thing for a while. 

I've tried to install Motorola Phone Tools, Creative Installation CD and a few games in the same manner, with no success. Could someone help me out?

Also, when I try to compress some video files (archive manager, .rar format) it takes a very long time. Compressing Season 3 of Friends took close to 25 minutes. I'd appreciate advice. 

Cheers! :)

---

### Post by cor2y on 2008-03-03
Welcome to ubuntu and linux as a whole.
Sounds like you still have some reading to do.
For your motorola phone tools you will need the linux version  moto4lin ```
http://moto4lin.sourceforge.net/
``` its not as glamorous in the GUI department as Motorola Phone Tools but it gets the job done.

What exactly is Creative Tools and what does it do?
Perhaps theres a Linux equivalent.
As for Windows video games on Linux you will have to research if they run via wine, just because the program installs via wine doesn't always mean it will run without you having to tweak something in wine, sometimes no amount tweaking will help until a new version of wine is released or perhaps it might require an older version.
Search out your apps at the wine database ```
http://appdb.winehq.org/
```or the wine section of the forums right here.

Rar compression i don't know too much about in the speed department, if compression is slow make sure dma is enabled on your harddrive how to check i know of only from the terminal something you may have to familiarize yourself with
```
sudo hdparm /dev/hda
```
Normally hda is your linux harddrive it may be different for you.

---

### Post by LynxKItten on 2008-03-03
@cor2y, thanks!

/dev/hda:
 IO_support    =  0 (default 16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

Creative Tools is an Installation Disk for my mp3 player, I need it to transfer files and stuff. One of the games I'm trying to install is SIMS, but I'm not able to get it running

---

### Post by wednesday allfather on 2008-03-03
Something else you can try

I used to dual boot Vista and Ubuntu (Vista came installed)

Then I started using WINE, but it was kinda buggy, but still a great program.

Now i use VMWARE

It creates a virtual machine on your comp, so you can run windows from linux.

If you have the system resources, you should give it a try.

You can get it from Synaptic.  

I can boot up XP (I gave up on Vista, it's just not ready) from Linux for testing things, which saves me lots of time.  

Truth be told, I just really think it's cool.  

Does anyone know about any drawbacks of VMWARE?

---

### Post by cor2y on 2008-03-03
It will not do 3d gaming or 3d applications.
But for 2d regular applications it will work.

As for the sims not too sure if you can play that via Wine.

Creative Tools , i am sure there is a linux tool that can make use of the zen mp3 player if thats what you have that allows you to drag and drop mp3 files in and out of it or manage them.
Search on the forums for that , search by your mp3 player name.

DMA is on, so raring files up should be a snap.
You could try installing the commercial version of rar if you haven't already (its in the repos) not there is a free version and commercial version available check to see which one is installed.

---


---
title: "nVidia graphics driver for XFX GeForce FX 5200"
date: 2005-03-22
forum: Gaming &amp; Leisure
---

### Post by Coutsos on 2005-03-22
Hi,

Has anybody experienced problems with the nVidia drivers in Ubuntu? I've installed them as explained in the unofficial ubuntu howto, but I seem to get pretty bad OpenGL performance. A game I'm working on, would get an average of about 80 frames per second when I was working under Slackware10.0 (I had the drivers downloaded from the nVidia website). Now under Ubuntu without any changes to the code I'll get around 40-50 frames per second. And trying to use Blender gives choppy response as well.

Could it be that I'm missing something? I tried to install the drivers from nVidia's website, but they require the kernel sources to install which I don't have. Running linux kernel 2.6.8-1-386 (or something like that, I can't check right at this moment) and I can't find the sources for that anywhere on the Ubuntu installation CD or in Synaptic.

-Nick

---

### Post by audax321 on 2005-03-24
Hello,

I actually just installed the nVidia drivers from their website. This is one reason I hate getting video cards drivers that are precompiled. I've noticed that when nVidia releases drivers they release patches for those drivers as well and these patches may or may not be incorporated into the premade drivers.

Installing the drivers on Ubuntu using nVidia's drivers is not that hard, here is how I did it:

---------STEP 1: REMOVE THE OLD DRIVERS-----------
Just remove any drivers for this card you installed from apt.
Edit your XF86Config so that the driver portion for the video card says "vesa" and reboot.
--------------------------------------------------------------------------

-------STEP 2: GET DRIVER PRE-REQUISITES----------
1. Open up Synaptic
2. Install gcc
3. Install linux-source for the 2.6.8.1 kernel or whatever kernel you are using (can be found out by doing 'uname -r' in the console)
4. Download the latest nVidia driver
5. Go to the nVidia Forums and look for a sticky thread at the top that says something about updates for the version of the driver you downloaded and follow the directions here to patch your driver (optionally, there are also directions to repackage the driver in case you want to backup the patched copy somewhere).
LINK: [http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14) 
-----------------------------------------------------------------------------

-------STEP 3: BUILD LINUX-SOURCE--------------
1. Open up a console window.
2. cd /usr/src
3. sudo tar xjvf name_of_source_file.tar.bz2
4. sudo ln -s name_of_dir_where_file_was_untarred_to linux
4. cd /boot
5. dir
6. make a note of the config file for your kernel (e.g. for the 2.6.8.1-5-386 kernel it is config-2.6.8.1-5-386)
7. sudo cp name_of_file_from_step_6 /usr/src/linux/.config
8. cd /usr/src/linux
9. make

NOTE: The make will take a long, long time :)
---------------------------------------------------------------------

----------STEP 4: INSTALL THE DRIVER----------------------
1. Goto console without X running:

Ubuntu apparantly has no init 3, like other distros so I just put an invalid driver for the video card in the XF86Config file which made X crash after a reboot and gave me a console. Kind of weird way to do it, but it works.
2. If you are using Kernel 2.6, then type:

modprobe -q agpgart
3. Go to where the nVidia driver is run it:

If you didn't repackage the driver, then go to the folder where you extracted and patched the driver and run

sudo sh nvidia-installer

OR

If you repackaged the driver, go to where the repackaged driver is and run

sudo sh name_of_driver_file.run

4. Edit your XF86Config by commenting out:

Load dri
Load GLCore

and make sure this line exists:

Load glx

also in the Video driver section, change the name of the driver from whatever you had to:

nvidia
-----------------------------------------------------------------------

And that should get the driver running. If you have any questions, just ask.

---

### Post by Coutsos on 2005-03-24
I'll give it a go when I get home. But in the XF86, should I be concerned where it says:
[COLOR=DimGray]        BusID           "PCI:1:0:0"[/COLOR]
It's an AGP graphics card, so, I don't know...

---

### Post by audax321 on 2005-03-24
[QUOTE=Coutsos]I'll give it a go when I get home. But in the XF86, should I be concerned where it says:
[COLOR=DimGray]        BusID           "PCI:1:0:0"[/COLOR]
It's an AGP graphics card, so, I don't know...[/QUOTE]

Well, probably not. That is what mine says and its AGP as well. I think that's just the usual BusID that most motherboards use for AGP cards. It won't affect the driver installation though, just whether or not X will be able to start after the install is finished (because if the BusID is wrong the driver will be trying to use the wrong card in your computer). If your current driver can get you into X, then that BusID is fine.

---

### Post by Gtaylor on 2005-03-29
Is there a noticable performance gain from using the official nvidia drivers? Is there any difference at all?

---

### Post by daniels on 2005-03-29
All the patches nVidia have released for 1.0.6629 have, to the best of my knowledge, been incorporated into the packages.  And you don't have to recompile the driver when you update the kernel.  I would recommend not compiling stuff yourself unless you have to.

---

### Post by audax321 on 2005-03-29
Gtaylor, I have a GeForce 6600GT so there is a very big difference for me using the latest drivers over the 6629 ones. Not to mention, I've always installed the drivers this way and prefer it.

As far as compiling software goes, its not that bad with the nVidia drivers because they compile themselves with the correct options for your system and have an uninstaller that can be run in the event something goes screwy (which it never has for me). There is a lot of documentation about the installer at [www.nvidia.com](www.nvidia.com) under the linux drivers section in the readme. Also, if you want to upgrade the driver later on, there is no need to uninstall the previous driver because it will be automatically removed during the install process of the new driver.

I should also mention that to improve performance, under Section "Device", add the following lines:

Option "NvAGP" "2"
Option "RenderAccel" "true"

and optionally, if you don't want the nVidia logo to pop up whenever X starts:

Option "NoLogo" "true"

:)

---

### Post by Gtaylor on 2005-03-29
I can see there being big benefits for the 6000 series but I'm running an older 5500 that's been out for quite some time. I've installed the nVidia drivers manually several times, I just don't know if it'd be worth it in my case (running an older card that is probably mostly implemented).

---

### Post by audax321 on 2005-03-29
Well the 7167 drivers don't seem to have any fixes specifically related to your video card and the patches fix these issues;

    * This patch fixes 2D/3D performance problems when using the Linux AGP driver, AGPGART; the built-in NVIDIA AGP driver, NvAGP, is not affected by this problem.

    * This patch fixes a compile time error when building against Linux 2.6.11-bk3 or later, configured without support for AGPGART (i.e. CONFIG_AGP unset).

So, unless you are using AGPGART (which I do, because my performance seems to be better with it) I would just do whatever you feel more comfortable with. 

To find out info about your current nVidia driver if you have one installed, do this in terminal:

cat /proc/driver/nvidia/agp/status

The driver entry will list whether or not you are using AGPGART or something else.

---

### Post by kfburnt on 2005-08-18
Please help - I have an amd 64 with an XFX GeForce FX 5200
my problems:

cat /proc/driver/nvidia/agp/status

returns 

Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

and

dmesg

returns

NVRM: loading NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
NVRM: WARNING: Your Linux kernel has problems in its implementation of
NVRM: the change_page_attr kernel interface.  The NVIDIA kernel
NVRM: module will attempt to work around these problems, but
NVRM: system stability may be affected.  It is recommended that
NVRM: you update to a 2.6.11 or newer kernel.

and

uname -a

returns

Linux 2.6.10-5-amd64-k8 #1 Fri Jun 24 17:08:40 UTC 2005 x86_64 GNU/Linux

but that is the optimized driver I get from using

apt-get install linux-amd64-k8 linux-restricted-modules-amd64-k8 nvidia-glx

I am trying to configure my system by the instructions of

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

which goes through the process of retrieving/enabling/optimizing a nvidia driver on Ubuntu with the apt-get command

My ultimate goal:

I have transgaming's point2play installed and I want to use it to play World of Warcraft.

In the hardware checks my video card fails hardware rendering.

Now, I have gotten WoW to work but I have an issue where I can't target anything in the game due to a opengl coordinate error that should be resolvable using step 2 I found a transgaming forum where you have to change the memory allocations for the game. But that only works if you have opengl enabled.

My system categorizes my video card under (unknown 0x5246)
NV32 Geforce FX 5200
and says I have a pci bus- which is really an agp8x --- but the whole idea of what "pci" means in linux was already gone over in this thread.

Now... I am a real linux newb if you couldn't already tell. On an Ubuntu build and you know my kernel.

I would love and bow down to someone who could give me a detailed step by step on how to get my video card working 100% properly and (if u know about this) tell me the best way to get WoW running in full gear on my system (I didn't have sound either)

AMD 64 3200+
FX 5200 nvidia
1024 3200 ram

---

### Post by sbentjies on 2009-01-06
I am experiencing the exact same thing with my eVGA FX 5200. The best resolution I get is 800x600. I just loaded 8.04 fresh and have tried 8.10 with no luck either. Am I missing some steps? The restricted drivers make the problem worse. I don't know how to compile a kernel as I'm a Linux noob. Is there a way to get the right driver from Nvidia and the right kernel in 8.04? Surely I don't have to compile a kernel just for this card....

---


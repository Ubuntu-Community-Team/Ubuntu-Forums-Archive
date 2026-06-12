---
title: "Graphics card driver update - system now fails to boot"
date: 2010-01-24
forum: Desktop Environments
---

### Post by simondbarnes on 2010-01-24
Please excuse the clueless ramblings of a Linux newbie but I could do with a bit of help if possible :)

Running Kubuntu 9.1, all has been fine until I decided to install an nvidia graphic card driver for my geforce5200 (think that's what is there, haven't used this computer for years). I rebooted the system after installation as requested, now can't get past the kubuntu splash screen when booting - the system just locks up :(

Tried going into recovery mode to see if there were any easy options for removing the driver and reverting back to the default one but couldn't make anything work.

I'm sure it's something that is easy to do from the command line but I wouldn't have a clue where to start! Can anyone help?

Currently running from the live cd...

---

### Post by Zorael on 2010-01-24
Picking **fix X** from the recovery menu should disable the Nvidia driver. Else you can pick **root shell** and rename/remove the **/etc/X11/xorg.conf** file manually, which is what **fix X** basically does.
```
# mv /etc/X11/xorg.conf /etc/X11/xorg.conf.borked1001
# exit
```

How did you install the drivers? From the official repository packages; **nvidia-glx-***? Or did you the Restricted Driver thing pop up and do it for you?

The log file for X, located at **/var/log/Xorg.0.log**, should tell you what went wrong with the last *OR CURRENT* session. As such, if you manage to fix X and start it up, the file containing the failed boot will be overwritten. If that happens, have a look at **Xorg.0.log.old** in the same directory for the previous log.
```
*(to print the last 20 lines of that file)*
# tail /var/log/Xorg.0.log

*(to browse the entirety of it)*
# less /var/log/Xorg.0.log

*(to copy it elsewhere for later reading)*
# cp /var/log/Xorg.0.log /home/*yourusername*
```

Hopefully it should be spouting some concrete error messages near the end.


**edit:** If you're on a live cd right now, you should be able to mount your root system and view the logs right away.

---

### Post by simondbarnes on 2010-01-24
Thanks for the reply.

I installed the driver using KPackageKit and searching for Nvidia as far as I can remember.

I don't appear to be able to get into the recovery menu now, is there a way of forcing this to come up when I boot from the HD?

---

### Post by simondbarnes on 2010-01-24
Btw, I can view all of the files on my HD whilst running from the live cd. This is the Xord.0.log...

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux kubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=b9d85eef-430a-48af-9da8-bcf26c607fa4 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 23 22:47:28 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0322:0000:0000 nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by Zorael on 2010-01-24
There should be GRUB entries to get you into recovery mode, unless you have tinkered with the default settings. Look for something like "Ubuntu, Linux 2.6.31-17-generic (recovery mode)".

You can also force it if you edit a normal entry *(in GRUB)* (by hitting E), navigating down to the **linux** line, and adding '**single**' to the end of it. Then executing the entry by hitting Ctrl+X (GRUB2, different keystroke in GRUB Legacy but it should say on the screen). If it boots but the splash never goes away, reboot and at the same time as adding '**single**', remove '**splash**'. The changes aren't saved so you can't mess anything up.

I'd try to (go into recovery mode,) pick **root** and reinstall the Nvidia package. You seem to have installed **nvidia-glx-96**, as per this tidbit in your pasted Xorg.0.log.
```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Server Extension
(II) **NVIDIA GLX Module 96.43.13** Thu Jun 25 18:56:56 PDT 2009
```

Looking at [Nvidia's list of cards with regards to what drivers they can use](http://www.nvidia.com/object/IO_32667.html), the FX 5200 (which you do seem to have according to your Xorg.0.log) should be able to use the **-173** driver. The [description of the repository **nvidia-glx-173** package](http://packages.ubuntu.com/karmic/nvidia-glx-173) confirms this.

```
# aptitude purge nvidia-glx-96 && aptitude install nvidia-glx-173
# reboot
```
The 5200 is not listed in the description of later drivers (there are -180 and -185 drivers, too), so likely the -173 one is the one you need.

---

### Post by simondbarnes on 2010-01-24
Thanks. I was getting GRUB entries with recovery and memory test options before, now they are not coming up for some reason so I can't see a way of getting a command line up so that I can edit or rename etc/X11/xorg.conf :(

---

### Post by Zorael on 2010-01-24
Well, you do get normal GRUB entries, no?

> You can also force it if you edit a normal entry *(in GRUB)* (by hitting E), navigating down to the **linux** line, and adding '**single**' to the end of it. Then executing the entry by hitting Ctrl+X (GRUB2, different keystroke in GRUB Legacy but it should say on the screen). If it boots but the splash never goes away, reboot and at the same time as adding '**single**', remove '**splash**'. The changes aren't saved so you can't mess anything up.

---

### Post by simondbarnes on 2010-01-24
No, I am no longer getting any GRUB entries...

---

### Post by Zorael on 2010-01-24
Ok, hold on. So when your computer boots, it doesn't get to GRUB and instead just hangs after the power on self-tests?

Or does it get to GRUB but it's completely empty? Like as attached?

---

### Post by simondbarnes on 2010-01-24
It gets through the POST fine and then goes straight through to the Kubuntu splash screen and then locks up after this.

When I first had the problem, it gave me GRUB options after going through POST, now it doesn't :confused:

---

### Post by Zorael on 2010-01-24
Very strange.

All right, so your options are to wipe your **xorg.conf** from your live cd, or to **chroot** into the disk (also from your live cd), and from there try to reinstall the package. Wiping xorg.conf is by far the easiest task.

You managed to mount your root drive when you fetched your Xorg log file, right? So just do the same and navigate into **/etc/X11**, then rename/delete **xorg.conf** and give it a whirl.

---

### Post by simondbarnes on 2010-01-24
> You managed to mount your root drive when you fetched your Xorg log file, right?

It just shows up in Dolphin as a drive. I didn't need to do anything to get it there. I can read any of the files but not write them.

My Live cd is a CD-R not RW so how can I delete files from it?

Thanks for your patience, must be a PITA dealing with someone with very little linux knowledge!

---

### Post by Zorael on 2010-01-24
Just to clear stuff up now so we're not confusing eachother more than necessary. :3

When you say that you don't get GRUB and instead the Kubuntu splash just pops up, that's not with the live cd inserted, is it? If so, (depending on how your system is set up) it would probably load the live cd instead of your hard drive (root disk), and GRUB would never show. Which we want it to.

-----

Assuming it's not booting the live cd, I think you'd need to manually mount the drive, but first try opening Dolphin with superuser permissions and see if you have write permissions then. And again, this is to the **root disk**, and not the **live cd**. To open Dolphin with sudo, pop up a run box with Alt+F2 and enter '**kdesudo dolphin**'.

Otherwise, to manually mount it, install **gparted** on your live cd. It's in the main repositories so you wouldn't need to enable any extra. Don't install any other updates, since it wouldn't fit into your memory at this point (unless you have lots and lots of RAM). To explain, you *can* install packages in a live environment (such as from a CD), as it would hold the changes you made (files installed) in memory (RAM). So if you start installing lots and lots, it would gradually eat up your memory, and you'd eventually run into a "disk full" message.

Install it via the package manager or from a terminal.
```
$ sudo aptitude install gparted --without-recommends
```
Once installed, open it up from a run box (Alt+F2) with '**kdesudo gparted**'.

First, make sure you're on the correct harddrive if you have several, with the dropdown menu at the top right. Then try to *judge* which partition is your root drive, by its size, label, or just guess. Note its *device node*, which it says in the Partition column all the way to the left. It might, for instance, be something like **/dev/sda3**.

Then open up a terminal and do the following in your home directory, or just someplace where you have write permissions.
```
$ mkdir root
$ sudo mount *<partition device node>* root
$ dolphin root
```
That should have mounted your root drive and Dolphin should be sitting in it, with write permissions.

If you guessed partition earlier and it now turns out it's the wrong partition, just unmount close Dolphin, unmount the partition we just mounted (command below) and redo the steps with some other partition listed in gparted.
```
$ sudo umount root
```

---

### Post by simondbarnes on 2010-01-24
> Assuming it's not booting the live cd, I think you'd need to manually mount the drive, but first try opening Dolphin with superuser permissions and see if you have write permissions then. And again, this is to the **root disk**, and not the **live cd**. To open Dolphin with sudo, pop up a run box with Alt+F2 and enter '**kdesudo dolphin**'.This let me get to the root drive with write permissions so I then went to **/etc/X11/xorg.conf** and renamed the file to [B]/etc/X11/xorg.conf.borked

[/B]I then rebooted (remembering to remove livecd) and it worked first time :D

Many thanks for your help. It may have taken some time but I now have a working system again and a tiny bit more Linux knowledge!

---

### Post by Zorael on 2010-01-24
Awesome. :3

You can try to install the Nvidia driver again, but this time pick the **nvidia-glx-173** one. Alternatively **envyng-qt**, which is an installer app that will identify your videocard model, then download the appropriate driver and install it for you. At least now you know how to undo it if things don't work out.

---

### Post by simondbarnes on 2010-01-24
After spending most of the day trying to sort the problem I think I'll leave the graphics card drivers alone for now! I'll save that task for another day :)

---


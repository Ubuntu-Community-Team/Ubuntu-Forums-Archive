---
title: "PCSX2 (Linux Version) - Plugin Problem"
date: 2008-03-27
forum: Gaming &amp; Leisure
---

### Post by Prefix100 on 2008-03-27
Right,
Im having an issue installing a plugin correctly for PCSX2.

PCSX2 is a program that emulates a play station 2 for pcs which enables you to play ps2 games on your pc.
Their homepage is found [here]("http://www.pcsx2.net/").

I downloaded the .deb for my 64bit ubuntu machine from get deb. [Link]("http://www.getdeb.net/release.php?id=1986").

It works fine I guess, but it was a bit slow and my cd drive makes a seriously annoying noise, so I've made iso files of the game I want to play, Final Fantasy 12. I googled it and came up with this plugin - '[CDVDiso]("http://www.ngemu.com/ps2/pcsx2.php?action=plugins")', the plugins near the bottom of the page linked.

The readme states,
> CDVDiso v0.3
------------

 This is an extension to use with play station2 emulators 
 as PCSX2 (only one right now).
 The plugin is free open source code.

Linux requeriments:
------------------
 You need the GTK library, compiled with GTK v1.2.5, 
 the Zlib library (v1.1.3) and the bz2 library (v1.0.0).

Usage:
-----
 Place the file "libCDVDiso.so" (linux) or "CDVDiso.dll" (win32) at the Plugin 
 directory of the Emulator to use it.

 Linux only: Also place the cfgCDVDiso file at your $HOME directory or at the 
 Emulator directory.

Configuration:
-------------
 You can either write the iso you want to use in the config dialog, or everytime
 you run the emu open it, if you're doing this don't write anything in the dialog.

Creating an iso (linux only):
---------------
 To create an iso you can use the buttons 'Create Iso' or 'Create Compressed Iso',
 the file will be the one in the Iso Edit, and the Cdrom Device is the cdrom that
 will be used as source.
 The compression method is specified by the Compression Method Combo.

 Note: This will fail if the file in the Iso Edit already exists (if it's
 compressed the .Z or .bz suffix will be added).

Compressed isos:
---------------
 You must create them by the Compress Iso button, this will create a .Z or .bz
 file (the compressed image) and a .Z.table or .bz.index file (this is a table,
 for speed reasons), both will be created in the same dir the selected iso 
 image, the original image will not be deleted and/or changed, and also you can
 decompress the compressed iso with Decompress Iso button.
 The compression method is specified by the Compression Method Combo.

 Note: you only can decompress the images with the Decompress button, not with
 compress or bzip2.

Compression Method:
------------------
 .Z  - compress faster: this will compress faster, but not as good as the .bz.
 .bz - compress better: will compress better, but slower.

Changes:
-------
 v0.3:
 * Better Iso detection, thx florin :)
 * Updated to PS2Edefs v0.4.5

 v0.2:
 * Added support for isos using 2048 blocksize
 * Nero images are supported
 * Better extension filtering

 v0.1:
 * First Release
 * Tested with Pcsx2

 Email: <linuzappz@hotmail.com>

After following the steps under usage the plugin still doesn't show up in my PXSX2. Any chance someone could give me a step by step of how to do it? I think its something to do with the dependencies, but I don't know how to update them.

EDIT: Also heres a [link]("http://www.ngemu.com/download.php?action=plugin&id=88") to the plugin in case you cant find it.

Cheers, its appreciated,
Prefix

---

### Post by barius on 2008-03-28
I haven't used the .deb myself, though I know some people have had it working.  Personally, I compile the SVN myself.  I wrote a guide for others:

[http://ubuntuforums.org/showthread.php?t=631979](http://ubuntuforums.org/showthread.php?t=631979)

The SVN contains all the necessary plugins, and my guide only requires copy/paste skills.  You could just compile then transfer the plugins to where the .deb needs them.

---

### Post by hectic1 on 2008-04-07
no it doesnt contain everything needed,svn runs slower,crashes more
the plugins u get for pcsx2 by default are actualy a joke,they are kinda old,you have to get new ones,and install them,thats not easy
for ex you cant play the game normaly using the plugin you get by default,you have to get lilypad,and by any chance you get to actualy install it correctly you still will spend hours trying to figure out how to get it working correctly,took me a while but i made it work using the mouse too :P and at max fps under linux,thats just cause i like playing FF12

---

### Post by barius on 2008-04-08
uh...right...

Well, considering that Lilypad is a WINDOWS ONLY* plugin perhaps you need to get your eyes checked out since you obviously aren't running Ubuntu.  The rest of your assertions are similarly false.

* ['Official' Lilypad forum post at NGemu]("http://forums.ngemu.com/ps2-plugin-questions-troubleshooting/87274-lilypad-new-pad-plugin-lame-name.html")

---

### Post by crazyfuturamanoob on 2008-12-26
Most plugins are for windows ONLY, and the ones that should work on Linux don't work. :(

---

### Post by jorj82 on 2008-12-26
Here's a link to the Linux plug-ins.  You'll have to scroll down the page to find them [http://www.ngemu.com/ps2/pcsx2.php?action=plugins](http://www.ngemu.com/ps2/pcsx2.php?action=plugins)

---


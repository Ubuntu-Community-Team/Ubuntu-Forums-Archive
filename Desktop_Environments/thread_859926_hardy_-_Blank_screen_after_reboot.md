---
title: "hardy - Blank screen after reboot"
date: 2008-07-15
forum: Desktop Environments
---

### Post by ubuian on 2008-07-15
I have seen a few similar threads but nothing seems to be quite helping me so I hope someone out there has some ideas.

I am running a clean install of Ubuntu 8.04 after ditching a XP system.  The install went great from the desktop disk.  I then followed some tips to get a wireless card to work and created new users.  On reboot I got as far are the UBUNTU loading screen and then went to a blank (but backlit) screen and crashed (nothing from keyboard, mouse etc)

I figured I had done something bad so tried to reinstall the system (clean again, no partitions) - same result.  From the text installer - same result.

I have now figured that I can start in recovery mode run some repairs (dpkg repair broken packages [don't get any upgrades] and xfix [again nothing I notice happens]) it loads !!???  seems to run well (although kinda slow)

I now think the original changes I made had nothing to do with this bug - but I cannot get rid of it despite innumerable re-installations and searching for fixes any hep greatly appreciated.  I am no very computer literate, but can follow instructions very well :)

I am running a 2.6Ghz Celeron with 2x256 DDR SRAM.  Inbuilt video. This is looking like my third failed attempt to switch to Linux (3 different machines) and I would really like to turn it around.

---

### Post by lesergi on 2008-07-15
Hello!

I have the same problem. When I boot system X server runs, but when the system try access to user desktop screen become black and turn back to KDM.

I tried used XDM instead KDM, but the same. I tried access tu others users, but the same.

Help please!

---

### Post by PmDematagoda on 2008-07-15
Can you post the outputs of:-
```
cat /var/log/Xorg.0.log
```

---

### Post by ubuian on 2008-07-15
aghhh - after multiple attempts cannot paste into here or upload as attachment (file too big or when I split it up its a wrong file type??  just txt docs though??)  can you either give me some tips on how to upload it here or give me a email address I can try??

thansk

---

### Post by PmDematagoda on 2008-07-16
> **ubuian said:**
> aghhh - after multiple attempts cannot paste into here or upload as attachment (file too big or when I split it up its a wrong file type??  just txt docs though??)  can you either give me some tips on how to upload it here or give me a email address I can try??

thansk

Just paste the contents of the file in a post, don't attach it.

---

### Post by ubuian on 2008-07-16
I get the following error message when pasting directly:

You have included 14 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

not sure where they are in the text but will post the beginning section here to see if that helps...
sorry if this is all pretty obvious - still pretty green with this linux stuff.  Thanks for the patience.



This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux StudyPC 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 15 16:35:42 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
RgbPath set to "/etc/X11/rgb"
ModulePath set to "/usr/lib/xorg/modules"
|-->Input Device "Configured Mouse"
|-->Input Device "Generic Keyboard"
The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
 Open ACPI successful (/var/run/acpid.socket)
 Loader magic: 0x81dc500
 Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
 Loader running on linux
 LoadModule: "pcidata"
 Loading /usr/lib/xorg/modules//libpcidata.so
 Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
using VT number 7

---

### Post by lesergi on 2008-07-17
After checking log files and see any error I tried run X from root.

```
sudo startx
```

KDE runs with no problems!! WTF!!

So, I think it was permission problem... I tried with home directory, creating new one, chmod-in', chown-in', nothing...

I couldn't view errors in console after running startx with normal user, so I redirected output to file
```
startx &> xlog
```

I could see /tmp error!! I solved my problem doing:

```
sudo chmod -R 1777 /tmp
```

But, I don't know /tmp had no valids permissions...

See you!!

---

### Post by ubuian on 2008-07-20
Hey PM - are you still reading this??  Lesergi seems (??) to have found a solution, but I am still doing a bodgy workaround every time I turn the computer off.  Have discovered when a boot in recovery mode I seem to have an error in the fix server option. Says is repairing a possibly changed Xlog file and saves a copy.  I can't see much difference in them only a line that has "#" before it that I assume is only notes...
any further advice??

---


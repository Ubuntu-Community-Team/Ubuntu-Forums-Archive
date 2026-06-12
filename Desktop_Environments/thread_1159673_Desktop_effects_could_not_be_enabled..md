---
title: "Desktop effects could not be enabled."
date: 2009-05-14
forum: Desktop Environments
---

### Post by marshmallow1304 on 2009-05-14
I take it I'm not the only one with this problem.  When I try to enable desktop effects I get "Desktop effects could not be enabled."

I'm running Ubuntu 9.04.
NVIDIA GeForce 6200 256MB DDR2 PCI
1GB RAM

I also have a crappy Intel integrated graphics chipset, which I can't disable from the BIOS because Dell, in its infinite wisdom, decided that its users are too desperately stupid to handle the power to disable integrated graphics.

I am using the NVIDIA driver (version 180).

compiz-check gives me
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n

```


Any solutions/advisories?

---

### Post by marshmallow1304 on 2009-05-17
More: I uninstalled and reinstalled drivers.  Same thing, except now in the "Hardware Drivers" pane, only one driver shows up ("nvidia") instead of the range of options I had before.

compiz-check now gives me this:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by eekfonky on 2009-05-17
same issue here except I'm using intel on-board graphics with ubuntu 9.04 64-bit

---

### Post by andrea000 on 2009-05-18
Hello,

Try removing the card's PCI ID from the blacklist
that should fix it it did mine anyway.

---

### Post by marshmallow1304 on 2009-05-18
> Try removing the card's PCI ID from the blacklist
that should fix it it did mine anyway.

I just did a clean install to help this and some other issues.  If it doesn't work after I get the driver installed, I'll try removing the ID from the blacklist.

I let compiz-check set compiz to skip the blacklist check and now it works.  Thanks.

---

### Post by andrea000 on 2009-05-18
no problem glad that worked for you

---

### Post by ConnorMarc on 2009-05-25
What do I need if the compiz -check says:

[quote=output]
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -check
[/quote]

---

### Post by zarthon on 2010-08-09
I want to clarify two things in this thread because I was perplexed.
 
compiz-check is NOT a command. It is not in the default path and does not have a man page.
also -check is NOT an option to compiz*.

On my Lucid (10.04) system it is at:
```
/usr/share/checkbox/scripts/compiz-check

```
Anyway Thanks! The script found my problem:
```
It has been detected, that you are currently running xcompmgr, which is a
 standalone compositing manager.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable xcompmgr? (Y/n) Y
```
After that I could *finally* enable compiz in System->Preferences->Appearance->Visual Effects

I just went with out them for the last few months. It's really nice to have them back!

*Running compiz from the command line is NOT a good idea! If it fails and you loose title bars and other window management functions. You can log out and log back in which will restart your X server, desktop, and window manager.

---

### Post by glenn69 on 2011-03-03
Running 10.10
Video card : GeForce 6200

nvidia (current) driver working
gfxgears runs at 1100 fps
compiz-check shows all boxes OK and nvidia driver running

When I try to enable effects via Appearances > Visual Effects, the system tries to download a driver, then displays "Desktop effects could not be enabled"

What do I try now?

Thanks

Temporary Solution [http://ubuntuforums.org/showthread.php?t=1467202](http://ubuntuforums.org/showthread.php?t=1467202)
Apparently compiz blacklists this card within its code.  This solution did work for me.

---


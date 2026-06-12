---
title: "Trying to set up dell mini, Compiz problems"
date: 2008-12-26
forum: General Help
---

### Post by Neablis on 2008-12-26
I have a new dell mini with ubuntu 8.04 on it. Ive been trying to get the cube working, and i have CCSM installed and i clicked the cube to enable it and i try the hot key and nothing happens. Im not getting errors but no matter what i do, nothing in CCSM seems to be working. Plus the bottom of the CCSM program is cut of from the screen and i cant click all the options. Any ideas whats going on? thanks for your time.

Also under System, preferences -> appearance there is no visual effect tab which i think should be there.

---

### Post by pytheas22 on 2008-12-26
Did you enable the 'rotate cube' plugin as well as the 'cube' plugin.  It's confusing, but you have to enable this before you can actually rotate the cube (what the point of the cube is without being able to rotate it is a mystery).

Also, are your other desktop effects working?  Do you have wobbly windows and window shadow for example, and can you zoom?  If you think compiz may not be enabled at all, open a terminal and type:
```

compiz --replace
```

to start it manually (press control-C to kill it if something goes wrong).

> Also under System, preferences -> appearance there is no visual effect tab which i think should be there. 

Yes, that's weird.  But I think the Dell Minis come with their own interface, right?  This may explain the difference.

---

### Post by Neablis on 2008-12-27
thanks for your reply, i did turn rotate on from the start so thats not the problem, i tried running compiz -- replace and this is what it does 
```

mitchell@mitchell:~$ compiz -- replace
Checking for Xgl: not present. 
FATAL: Module battery not found.
Detected PCI ID for VGA: 00:02.0 0300: 8086:27ae (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator


```

and if i control c from that spot to cancel, the computer crashes
btw i turned most of the dell enviroment of so i dont think thats a problem, is there an alternative command line way to get there?

---

### Post by pytheas22 on 2008-12-27
It looks like you didn't quite type the command correctly.  It's:
```

compiz --replace
```

Note that there's no space between the -- and replace (when you ran the command, you typed 'compiz -- replace').

Please give that a try.

Also, if pressing control-C crashes the computer, press control-alt-backspace and you should be sent back to the login screen.  This is better than having to do a hard reboot.

---

### Post by NestoRotseN on 2008-12-28
hi

im also having the same problem as the og poster.

i dont have a dell mini, but i have another netbook its an Averatec Buddy, which is just a re-branded MSI Wind. ^_^.Any ways...i have Ubuntu 8.10 and i re-installed compiz hoping that it solved the problem and nothing.I dont get the CCSM under system>preferences> either....i tried installing xubuntu and installed compiz and it worked, but i couldn't get the cube to work because it wouldn't let me add 4 colums,which means no cube.

---

### Post by pytheas22 on 2008-12-28
NestoRotseN: do you have compiz working at all on Gnome?  Can you start it by typing 'compiz --replace'?

---

### Post by cgault9 on 2008-12-29
I have a Sylvania Meso netbook and can;t get the cube running - I have plenty of HDD space and over 1gb of RAM but I'm not sure that the graphics cards in these tiny things have enough juice or whatever to work the cube (if that thereoy at all makes sense- i'm running an Intel 945 Express chipset) i have the Ubuntu Hardy 8.04 (except it is labeled as the UBUNTU NETBOOK REMIX) and have the cube running on my desktop with the identical advanced desktop settings- any help would be appreciated.


oh and does my refresh rate at all contribute to the cube?

---

### Post by pytheas22 on 2008-12-29
As far as I know, the Intel 945 chipset should definitely be capable of handling desktop effects.

I'm not positive but it seems to me that perhaps the 'Netbook Remix' desktop environment that Dell puts on these machines is the reason that compiz won't work.  Could any of you try booting to a normal Ubuntu live CD or USB drive to see if desktop effects work there?

---

### Post by stemno on 2008-12-29
> **pytheas22 said:**
> As far as I know, the Intel 945 chipset should definitely be capable of handling desktop effects.

I'm not positive but it seems to me that perhaps the 'Netbook Remix' desktop environment that Dell puts on these machines is the reason that compiz won't work.  Could any of you try booting to a normal Ubuntu live CD or USB drive to see if desktop effects work there?
Hi ! I am new ubuntu (8.10 desktop) user and i have this problems:
1. with compiz
some effects works well but not cube why???!!! Please Help
I activate Ati drivers, and compiz-check say:
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3600 Series
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
but only i can change desktop by pressing <shift>+<left mouse> (screen rotate around midle ax) i activate rotate cube ...
problem 2: The workspace switcher applet works only with 2 columns/1 row => 2 desktops only. If i put 2 rows 2 columns then the row 2 is inactive (when i put mouse cursor say only "workspace 1" and "workspace 2" I have gnome and kde and i use gnome, where in Aplications-system utils-System settings (kde i think but i try them in gnome to try solve the problem) -Desktop-multiple desktops i set number of them to 4.... but the problem persist

---

### Post by pytheas22 on 2008-12-29
stemno: your problem isn't the same as that of the other users in this thread, because you're using a normal Ubuntu system, not the Dell Mini.  You may want to start a new thread for your issue in order to get better help.

That said, to solve your problem, try right-clicking on the desktop-switcher applet in the Gnome panel and select Preferences.  Configure Preferences so that it looks like the screenshot.  This should allow you to have a cube.  You need at least four desktops in a horizontal row to use the cube; it sounds like you had two *rows* of two desktops each, which won't work.

If I understand your problem correctly, this should solve it.  If not, please start a new thread and let me know the URL so that I can reply there.

---

### Post by cgault9 on 2008-12-30
oddly enough I have just started installing Hardy onto my external usb HDD from my desktop and will try that out once I have it installed....

if this can be considered related, once I have the OS installed on the external HDD will my system recognize it and not see it as an unmountable drive?

---

### Post by pytheas22 on 2008-12-30
> if this can be considered related, once I have the OS installed on the external HDD will my system recognize it and not see it as an unmountable drive?

If you want to boot to the USB stick, you'll need to bring up a boot menu and tell the computer to boot to USB when BIOS first loads.  Simply plugging the USB stick into your computer while it's already booted into Ubuntu won't work (if you did that, the stick would mount and you would be able to read and write files and everything, but I don't think that's what you want to do).

---

### Post by NestoRotseN on 2009-02-22
> **pytheas22 said:**
> NestoRotseN: do you have compiz working at all on Gnome?  Can you start it by typing 'compiz --replace'?

sorry i didn't check up on this.but a day after i posted my problem i re-installed ubuntu 8.10, re-installed compiz and went to the package manager installed ccsm. it didn't work. haha. so i unistalled compiz completely and went online and found a site where it showed me how to compile it from scratch, which was a pain. im thankful for my linux class which made me understand a lot of what i was doing. so now i have it working just fine cube works fine, the only thing is that when the windows close and they "burn" up, it kind of lagged and didn't look good, so a made it close quicker and it looks just perfect.

---


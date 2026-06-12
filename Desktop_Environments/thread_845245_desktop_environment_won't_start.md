---
title: "desktop environment won't start"
date: 2008-06-30
forum: Desktop Environments
---

### Post by wildman4god on 2008-06-30
my dell latitude d600 with ubuntu 8.04 updated some software after I enabled the bottom two options in the update tab of software sources (backports and something else) I then did a restart but gnome won't start I just get a cli and I try to manually start gnome but it fails, please help, I have basic cli skills so you might want to write out any commands you give me to use. Thanks in advanced

---

### Post by mitya on 2008-06-30
Hi.
Login to the console and type in following:

[FONT="Courier New"]sudo /etc/init.d/gdm restart[/FONT]

and look what it says. This command will restart GDM (gnome desktop manager).

I guess you know how to use [FONT="Courier New"]sudo[/FONT] command?

---

### Post by wildman4god on 2008-06-30
*stopping GNOME Display Manager...                       [OK]
*Starting GNOME Display Manager...                       [Fail]

---

### Post by mali2297 on 2008-06-30
Try
```

startx

```
and see if you get more informative error messages.

---

### Post by adewale on 2008-06-30
@wildman4god 
This doesn't relate to your problem, i got my sister a dell latitude d600 and since she needs xp i have to start hunting for the drivers. I've spent close to 4hours and no luck even windows update doesn't work. Anyway do you know where i can get the drivers from ? The ones at dell's website are too big to be downloaded via my gprs connection. Also how does one activate the bluetooth. I ran a live cd on it and everything works, apart from the bluetooth which also doesn't show in windows. Thanks

---

### Post by wildman4god on 2008-06-30
disable montype: 2
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
enable montype: 2
[config/hal] couldn't initialise context: (null) ((null))

waiting for X server to shut down disable montype: 2
finished PLL2
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

---

### Post by wildman4god on 2008-06-30
> **adewale said:**
> @wildman4god 
This doesn't relate to your problem, i got my sister a dell latitude d600 and since she needs xp i have to start hunting for the drivers. I've spent close to 4hours and no luck even windows update doesn't work. Anyway do you know where i can get the drivers from ? The ones at dell's website are too big to be downloaded via my gprs connection. Also how does one activate the bluetooth. I ran a live cd on it and everything works, apart from the bluetooth which also doesn't show in windows. Thanks
Sorry I havn't used windows on mine for almost a year and I don't have the original disc because i got it on ebay.

---

### Post by mali2297 on 2008-06-30
Check
```

egrep "WW|EE" /var/log/Xorg.0.log

```
What does it say? (If anything.)

Perhaps you can try reinstalling ubuntu-desktop:
```

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop

```

---

### Post by wildman4god on 2008-06-30
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist
(IT) Loading extension MIT-SCREEN-SAVER
(WW) RADEON(0): LVDS Info:
(WW) RADEON(0): No crtc mode list for crtc 1, continuing with desired mode
(WW) RADEON(0): DRI init changed memory map, adjusting...
(WW) RADEON(0):   MC_FB_LOCATION was: 0xebffe800 is 0xebffe800
(WW) RADEON(0):   MC_AGP_LOCATION was 0xffffffc0 is 0xe07fe000
(WW) AIGLX: 3D driver claims not to support visual 0x23
(WW) AIGLX: 3D driver claims not to support visual 0x24
(WW) AIGLX: 3D driver claims not to support visual 0x25
(WW) AIGLX: 3D driver claims not to support visual 0x26
(WW) AIGLX: 3D driver claims not to support visual 0x27
(WW) AIGLX: 3D driver claims not to support visual 0x28
(WW) AIGLX: 3D driver claims not to support visual 0x29
(WW) AIGLX: 3D driver claims not to support visual 0x2a
(WW) AIGLX: 3D driver claims not to support visual 0x2b
(WW) AIGLX: 3D driver claims not to support visual 0x2c
(WW) AIGLX: 3D driver claims not to support visual 0x2d
(WW) AIGLX: 3D driver claims not to support visual 0x2e
(WW) AIGLX: 3D driver claims not to support visual 0x2f
(WW) AIGLX: 3D driver claims not to support visual 0x30
(WW) AIGLX: 3D driver claims not to support visual 0x32
(WW) configured Mouse: No Device specified, Looking for one...

Apt-get is not working

---

### Post by mali2297 on 2008-06-30
> **wildman4god said:**
> 
Apt-get is not working

How come? Any error message?

---

### Post by wildman4god on 2008-06-30
it works but it says it can't resolve repositiries, this means a) it can't connect to the internet or b) servers are down or c) something else I can't think of

---

### Post by wildman4god on 2008-06-30
This all happened after i did an update and i remeber X11 was one of the updates and all the error messages i saw said that there was something wrong with the x11 file, maybe the update ruined it.

---

### Post by wildman4god on 2008-06-30
I got apt-get working, i had to manually set networking since gnome couldn't do it, i reinstalled ubuntu desktop and it starts to load i see a checker background and and x in the middle for the mouse, then it fails and goes right back to cli. I am trying xfce to see if that works

---

### Post by ticthak@AOL.com on 2008-07-11
emachines desktop w/ Sempron 3200, 512MB, nVidia onboard geforce4
        About a week ago I did a fresh install of Hardy on a new partition, everything seemed to work fine out of the box, installed KDE4, and that worked fine, but in really boosting the OS with apps to turn this into a heavy inhouse testbed/workstation, something has happened to the desktop load process- I get the KDE logon screen, logon successfully (if I put in an incorrect logon, it returns an error, so the logon process is OK) and the desktop will not load (cycles back to the logon screen, only now if I switch to console, I am correctly logged in.) Startx also fails, but I can load and run gdm by changing sessions at the logon screen (but not KDE3.5 unless I use that form my Gutsy partition- I have found a few leads here and other forum posts, I will try some things and post my progress.

---


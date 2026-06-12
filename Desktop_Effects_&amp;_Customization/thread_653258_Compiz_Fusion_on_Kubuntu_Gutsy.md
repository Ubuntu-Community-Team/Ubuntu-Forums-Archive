---
title: "Compiz Fusion on Kubuntu Gutsy"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by Alex135 on 2007-12-29
I hate having to create a topic that asks a question that is asked so much but nothing i can find fixes my problem.

I am running the 64 bit version of Ubuntu 7.10 with KDE installed.
I am using a Nvidia Gforce 6200 Video card with the proper drivers installed.
I really like KDE but i love Gnome's advanced desktop effects.
I would like some help with getting the same thing out of KDE.
I have installed all the stuff that Compiz Fusion needs according to what i have found, including *compiz-kde*. 
I ran *compiz --replace* and things change into what seem like what i want but i get the fallowing problems.

1. i have 4 virtual desktops, lined up as a square, 2x2. I go from the top desktop in one column to the bottom desktop in the same column it doesn't do any cube animation or flip animation. it also makes the icon for the desktop above it go blank if there is anything in that desktop. the top desktops i can switch to normally. I tried to put them into 1 row and the same thing happens, desktops 1 and 2 work but 3 and 4 don't, or something like that anyway.

2. the Adept Notifier shows up as a small window that i cant get rid of.

When i stop the process it takes me to a screen where i have no boarders. I am forced to restart the Xserver to fix this.

I might have installed everything wrong or not configured something right but im sure i got it working properly. 

i also get the fallowing output when i type in *compiz --replace*.
```
alex@localhost:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:014f (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'

```

I also get 8 screens up when i go into this, and only 1 and 3 seem to work.

Thanks in advance. :)

---

### Post by glantucan on 2007-12-30
Hi
I do get more or less the same as you, but I don't think it's so bad.

For question 1 the answer you are looking for is compizconfig-settings-manager install it from synaptic or run:
```
sudo apt-get install  compizconfig-settings-manager
```
Then you should get something like *Advanced Desktop Effects Manager* in preferences menu of the KDE. You can run ccsm from konsole alternatively.
Also, it's recommended that kde users start compiz with:
```
compiz --replace --ignore-desktop-hints
```
which may solve your issues with virtual desktops.

I share question 2 with you, but that shouldn't be so hard to solve, hopefully :D

About the output it's quite similar to mine. It's normal xgl is not detected (probably you are using AIGLX instead). The YV12 image format thing has to do with your settings on xorg.org (if you used ```
Option "OpenGLOverlay" "off"
``` on device section, which I believe is necessary, as I was told)

Hope this helps:)

---

### Post by Alex135 on 2007-12-30
i had installed *compizconfig-settings-manager* before.

I tried the other command option and the desktops are still screwed up. It seems as though nothing has changed.
If anyone wants ill upload my xorg.conf file, perhaps that will help.

---

### Post by jabeez on 2007-12-30
I've never understood why compiz-fusion/beryl has been such a pain in Kubuntu. I thought it must be something with KDE, then I installed Sabayon and it works just as good as in Gnome, then I installed Arch and it was literally 3 easy steps to get it up and running with tray icon and everything. With the popularity that has come from these fancy effects, I don't understand why the Kubuntu devs haven't made it a priority to make it as simple as it should be.

---

### Post by Forlong on 2007-12-30
> **jabeez said:**
> I don't understand why the Kubuntu devs haven't made it a priority to make it as simple as it should be.
They are focussing on KDE4 which will have similar effects.

I know it's not a reason why they didn't integrate it better in Gutsy but they obviously don't think much of Compiz (but keep in mind that resources for Kubuntu are somewhat limited).


Sorry I can't be of more help here...

---


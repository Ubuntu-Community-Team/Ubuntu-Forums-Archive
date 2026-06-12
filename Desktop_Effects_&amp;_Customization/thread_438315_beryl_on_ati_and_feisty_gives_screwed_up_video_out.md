---
title: "beryl on ati and feisty gives screwed up video output"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by insert_name_here on 2007-05-09
For a while, Beryl worked on my Fiesty Instlal with an ATI Radieon xSomething (I'll look it up if its relevant) card.  But today, when I went to boot into Gnome with Xgl, I get this crazy screwed-up output, like lines were in the wrong place.  (For reference, it looks like the output you get before the video driver initializes and I dont have the 'vga=791' option on grub)

How do I fix this?  Should I just 'aptitude reinstall beryl'?  

Thanks for the help.

---

### Post by sowelie on 2007-05-09
Hey,
We'll need more information to help.  First, check to see if your driver is configured properly by executing the following command in the console:
```
glxinfo | grep direct
```

If the output is "Direct rendering: no" then your driver is not configured properly.

By the sounds of it though you could have a hardware issue.  I had a similar issue a months back and it ended up being my AGP slot.

---

### Post by insert_name_here on 2007-05-09
It worked minutes before it failed with fglrx and xgl and gnome. 

 I doubt it is a hardware issue because gnome wihtout beryl/xgl works fine, as do watching movies (using the video card), plus it is a laptop, so the graphics card is onboard, so it can't have fallen out.  

The glxinfo thing returns "no" while not in XGL - I can't check to see what it says with Xgl because I can't see anything.

---

### Post by insert_name_here on 2007-05-10
Having disabled beryl from starting on startup, I got into Gnome with XGL.  glxinfo still says  "Direct Rendering: No."

If I start beryl from the command line, it tries to start up, but stops, and leaves me with no window manager stuff (like the top bar of windows, gnome-panel, etc.)  I can reload the window manager to metacity, if I want.  

When it starts, Beryl says:
me@mycomputer $: beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

---

### Post by insert_name_here on 2007-05-10
Sorry for way multi-posting, but I kinda fixed it.  Starting beryl, then beryl-manager and reloading the window-manger as beryl works.  But that's kinda complicated for startup.  Can I use dbus or something to tell beryl-manager to do all this on startup?

---

### Post by sowelie on 2007-05-11
It is good to hear that it doesn't seem to be your hardware. But, again just because it is a laptop and the graphics processor is on board doesn't mean it can't be broken.

When you get beryl running, does it run well.  When I had it running without direct rendering it was extremely slow.  The GLX errors you are getting from Beryl seem to be related to the fact that direct rendering is disabled.  I would look into that.  What you'll need to do is first ensure that in your xorg.conf the module dri is being loaded.

```

Section "Module"
...
Load "dri"
...
EndSection

```

If that is already there,  you need to analyze the output in your Xorg logs by executing the following two commands:

```

cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

```

---

### Post by strumluff on 2007-05-11
Definately appears to be the graphics driver if you have XGL and Beryl setup correctly.

If you're using feisty just reinstall the ATI proprietary driver from the Restricted Drivers Manager.

If not, then I recommend you download the Envy script, uninstall your current drivers first and then use this script to install the ATI drivers for you, it does a great job of setting up xorg.conf and everything too.
Get it here: [linky]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by kpolice on 2007-05-11
Just for the record: You **always** will get direct rendering: No **if you use** XGL.

---

### Post by insert_name_here on 2007-05-11
It's good to know that "Direct Rendering: No" is normal.

Since I have restarted/logged in and out repeatedly without any problems, my guess as to what happened is that Beryl didn't understand what it was supposed to do, however now that my varous configs are set right, it works.

I do have the "dri" module loaded in my xorg.conf.  Here are my logs, but I don't understand them, particularly because AIGLX is complaining, although it shouldn't even be installed...

$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "UseFBDev" is not used

---

### Post by kpolice on 2007-05-11
Is normal if you set up XGL to run as another session and you login into that session. If you have a separate "normal" GNOME session without XGL then yes it should say driect rendering true.

I also have
```
Section "ServerFlags"
	Option	"AIGLX" 	"off"
EndSection
```

in my xorg.conf .

The other errors are about an input device that is not present, a wacom. I know Ubuntu adds some unneeded lines to your xorg like the wacom one or do you use a wacom?

---

### Post by sowelie on 2007-05-11
Ahh, I didn't realize the "direct rendering: no" thing with XGL.  Also, I hear XGL interferes with other GL Apps such as games. I am using AIGLX for both my NVIDIA and ATI cards (NVIDIA on my computer, ATI on my wife's).  It works great on the NVIDIA, on the ATI Beryl consumes the CPU.  However, XGL was even worse.

---


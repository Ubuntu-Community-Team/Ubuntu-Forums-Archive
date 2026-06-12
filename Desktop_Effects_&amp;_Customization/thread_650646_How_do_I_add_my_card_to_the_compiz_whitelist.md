---
title: "How do I add my card to the compiz whitelist?"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by JohnnyBoy022 on 2007-12-26
I am running Ubuntu 7.10 with an ATI Mobility Radeon 1400. When I installed Ubuntu, I enabled the restricted fglrx driver and it installed correctly. Everything works great.

When I type fglrxinfo in the terminal it shows the name of my card correctly.
When I run glxgears, everything works great and the gears show up.

The only problem is when I start compiz, it says there is no whitelisted driver found. How can I add my card to the whitelist, or enable compiz to use my card?

---

### Post by Forlong on 2007-12-26
> **JohnnyBoy022 said:**
> I am running Ubuntu 7.10 with an ATI Mobility Radeon 1400. When I installed Ubuntu, I enabled the restricted fglrx driver and it installed correctly.
Did you install Xgl afterwards:
```
sudo apt-get install xserver-xgl
```

---

### Post by JohnnyBoy022 on 2007-12-26
The links in your profile are great, they really clear up a lot of the confusion.

Is Ubuntu supposed to automatically install XGL or do I have to do it myself? Bear with me as I am a total n00b when it comes to compiz and all this stuff.

Also, is there any way I can check to see if XGL is installed?

---

### Post by JohnnyBoy022 on 2007-12-26
I ran the command you gave me, and I also skipped the compiz checks. Here is the output of some commands. Any help would be appreciated.

fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

```

glxgears:
```
8271 frames in 5.0 seconds = 1654.192 FPS
8384 frames in 5.0 seconds = 1676.609 FPS
```

compiz:
```
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:6478): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:6478): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension

```

Thanks!

---

### Post by Forlong on 2007-12-27
> **JohnnyBoy022 said:**
> Is Ubuntu supposed to automatically install XGL or do I have to do it myself?
You have to do it yourself (that's why I posted the command).
And please don't use SKIP_CHECKS=yes unless you need it (you don't).

---

### Post by JohnnyBoy022 on 2007-12-27
Wow I am such an idiot. All I had to do was restart my computer and everything works great. Sorry for all the trouble I put you through. I guess I learned a lesson today, if in doubt reboot.

---

### Post by hack124x768 on 2008-02-11
Rebooting is for windows people. Us linux users have a friends named CTRL-ALT-BackSpace that will restart our graphical stuff. :)

---

### Post by JohnnyBoy022 on 2008-02-16
I figured that out after a couple days of using linux... i dont know how much time it has saved me

---


---
title: "COMPIZ in XFCE Gutsy"
date: 2007-11-15
forum: Desktop Environments
---

### Post by sergiodavila on 2007-11-15
Hi all!

Just installed XFCE and have problems running COMPIZ on it - no 3D effects. Searched the web to find some guide for customizing XFCE but didn't find anything.

Any help would be appreciated!

Thank you in advance!

---

### Post by Kevuntu on 2007-11-15
Same thing for me. There's no step by step tutorial showing how to  installing Compiz Fusion on Xubuntu 7.10 Gutsy Gibbon running on an Intel i830 graphics card. I prefer no to use XGL and Emerald (XGL is really slow on my computer and Xfwm4 is better than Emerald). I could try AIGLX, but I don't know where to start. Please help.

---

### Post by PeterJS on 2007-11-15
Ok, first things first, is your graphics card running the right drivers to be handling a 3d desktop? Run:
```

glxinfo | grep direct

```

That will tell you if direct rendering is setup properly on your machine if it its you are most of the way there.

To get compiz working you're going to want to install two packages: compiz and compizconfig-settings-manager. Once that is done you will want to run:
```

compiz --replace &

```
To start compiz and have it replace your current window manager. Once compiz is running you can configure it by going to Settings > Advanced Desktop Effects Settings.

Kevuntu:
Sorry I can't help you with getting your graphics card set up I don't know about intel cards, but being that they have open source drivers I would assume that they would just work.

---

### Post by sergiodavila on 2007-11-15
Thank you, PeterJS. I'll try that and post reply of what happened.

---

### Post by desudesudesu on 2007-11-17
Still not working for me.

I also tried installing emeralrd, and I am going to soon try installing XGL

---

### Post by SQuark on 2007-11-17
I'm guessing you've all got Intel graphics cards?

[http://ubuntuforums.org/showthread.php?t=576169](http://ubuntuforums.org/showthread.php?t=576169)

---

### Post by sergiodavila on 2007-11-18
Didn't get success at first time.:)

---

### Post by sergiodavila on 2007-11-18
Hallo again :)

After the command 

```
glxinfo | grep direct
```

I get an aproval of my nvidia graphic card - all correct with it.

Problem comes with the next step

```
compiz --replace &
```

System responds this:

```
sergio@sergio-desktop:~$ compiz --replace &
[1] 7310
sergio@sergio-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:0d.0 0300: 10de:03d0 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

What does that mean?

---

### Post by sergiodavila on 2007-11-18
OK, :)

after that I installed xgl pasting the following in terminal

```
sudo apt-get install xserver-xgl
```

Than logged out, and logged in. Than typed again 

```
compiz --replace &
```

Then got another ammount of missunderstanding by the system :)

```
sergio@sergio-desktop:~$ compiz --replace &
[1] 9309
sergio@sergio-desktop:~$ Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3000020 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3000020 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

---

### Post by SQuark on 2007-11-18
Have you got libgl1-mesa-dev installed? If not, try installing that and removing xserver-xgl again (AIGLX seems to be the preferred over Xgl, but I'm no expert).
This should get rid of the "Xgl: not present" message.

If, after that, you get "GLX_EXT_texture_from_pixmap is missing", try starting Compiz with "LIBGL_ALWAYS_INDIRECT=1 compiz --replace".

---


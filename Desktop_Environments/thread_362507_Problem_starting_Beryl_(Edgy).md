---
title: "Problem starting Beryl (Edgy)"
date: 2007-02-15
forum: Desktop Environments
---

### Post by Onyx_47 on 2007-02-15
I installed Beryl following the instructions on [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

When I try to start it:

```
onyx@onyx-desktop:~$ beryl-manager
onyx@onyx-desktop:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I'm a Linux newbie so this is like Greek to me... XP

---

### Post by vav on 2007-02-15
Check your /etc/X11/xorg.conf

Scroll down to where it says Section "Modules"

Is there a line that says Load "glx" ??
If not put it in there. That should fix the problem.

---

### Post by vav on 2007-02-15
You'll need to restart your X server afterward - Press Ctrl+Alt+Bksp and login again

Note: To edit the xorg.conf file, you'll need sudo permissions:

sudo gedit /etc/X11/xorg.conf

Put in your password and edit it, save it, exit gedit and then restart xserver

---

### Post by Onyx_47 on 2007-02-15
I already checked that... the line is there...

---

### Post by tomm3h on 2007-02-15
What wasn't mentioned, was if the line was commented?

#Load "glx"

...Wouldn't work. Removing the hash, removes the comment and ensures that the line is not ignored :)

---

### Post by Onyx_47 on 2007-02-15
it's uncommented...  oh yeah... here's a screenshot of NVidia X server settings... so it's not just beryl...

---

### Post by Onyx_47 on 2007-02-16
Sorry for bumping but this is still unsolved... Tried reinstalling libgl1-mesa-glx and installing nvidia-glx, still not working...

```
onyx@onyx-desktop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```

what should I try now?

---

### Post by Waappu on 2007-02-16
Hi

Try re-install / install latest Nvidia driver

download envy and install it
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb)
press Ctrl+Alt+F1.
Login virtual terminal and type```
envy
```
select install Nvidia driver

Edit:

Read howto use envy from here
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Onyx_47 on 2007-02-16
I did that already before installing beryl and couple of times after that... just my luck I suppose, I even managed to get Ubuntu 6.06 to the point only reinstall could help me :P

---


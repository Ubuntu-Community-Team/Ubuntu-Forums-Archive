---
title: "NVIDIA driver doesn't work when set up VNC server with resumable sessions"
date: 2008-12-02
forum: General Help
---

### Post by highnelly on 2008-12-02
Hi all,

I'm a newbie to Ubuntu and have just updated to Intrepid. 

I have just setup the remote desktop VNC server with resumable sessions according to [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) and it works great. 

The only thing is that the NVIDIA driver doesn't seem to work once I am accessing it from the remote machine. When on the remote machine and I go to Admin|NVIDIA Server Settings I get an error saying  

"You do not appear to be using NVIDIA X driver etc. etc." 

Also if I enter glxinfo into the terminal i get

Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Error: couldn't find RGB GLX visual or fbconfig

This only happens when I remote to the host; when on the machine itself the driver works fine. Please help me with this cos I really need to run software that needs acceleration.

Thanks in advance for any help

---

### Post by burning-daylight on 2012-11-20
> **highnelly said:**
> Hi all,

I'm a newbie to Ubuntu and have just updated to Intrepid. 

I have just setup the remote desktop VNC server with resumable sessions according to [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) and it works great. 

The only thing is that the NVIDIA driver doesn't seem to work once I am accessing it from the remote machine. When on the remote machine and I go to Admin|NVIDIA Server Settings I get an error saying  

"You do not appear to be using NVIDIA X driver etc. etc." 

Also if I enter glxinfo into the terminal i get

Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Xlib: extension "GLX" missing on display "127.0.0.1:1.0"
Error: couldn't find RGB GLX visual or fbconfig

This only happens when I remote to the host; when on the machine itself the driver works fine. Please help me with this cos I really need to run software that needs acceleration.

Thanks in advance for any help
I know, the thread is old, but i have the same problem on Ubuntu 12.04 with KDE.
It also appears on VNC or if I press ctrl+alt_F1. If i run it in KDE terminal emulator - everything is fine. Nvidia drivers.

---


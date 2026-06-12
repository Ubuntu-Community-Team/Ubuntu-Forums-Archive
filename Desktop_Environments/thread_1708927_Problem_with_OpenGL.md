---
title: "Problem with OpenGL"
date: 2011-03-17
forum: Desktop Environments
---

### Post by Artemus on 2011-03-17
I have five identical machines that I am running Maverick on. The four that I did an upgrade from Lucid on are running fine, but on the fifth that was a clean install gives me the following messages when I try to plot under SciLab:

```
WARNING: Due to your video card drivers limitation 
      s, that are not able to manage OpenGL, Scilab 
       will not be able to draw any graphics. Pleas 
      e update your driver.                         
```

Running glxinfo gives
```

$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
$

```

I've copied everything from /etc/X11 over from one of the working machines and even ran dpkg --get-selections/dpkg --set-selections to make sure that the configurations are the same, but I still get the problem. What driver do I need to install? lspci gives


```
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

---

### Post by Dutch70 on 2011-03-17
Is there any way to set it to direct rendering? If so, see if that helps. Also, this may be irrelevant, but check the link in my sig, even though it's pertaining to Compiz, you may find a clue there that helps you figure it out.

---

### Post by Artemus on 2011-03-17
> **Dutch70 said:**
> Is there any way to set it to direct rendering? If so, see if that helps. Also, this may be irrelevant, but check the link in my sig, even though it's pertaining to Compiz, you may find a clue there that helps you figure it out.

Thanks for responding. I couldn't figure out a way to set SciLab for direct rendering, unfortunately. I tried toggling the compiz rendering as in your link and it didn't help either.

---

### Post by Krytarik on 2011-03-17
Try upgrading the driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
Greetings.

---


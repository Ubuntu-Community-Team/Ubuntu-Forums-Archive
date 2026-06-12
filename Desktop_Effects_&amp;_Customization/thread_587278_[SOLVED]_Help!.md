---
title: "[SOLVED] Help!"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by mellflores1 on 2007-10-22
I have been trying to make my desktop effects work for a long time. 
I did everything here: [http://ubuntuforums.org/showthread.php?t=585045](http://ubuntuforums.org/showthread.php?t=585045).
So now I don't get that error message but I get 'Desktop effects could not be enabled' when trying to enable Normal, Extra or Custom. It's really frustrating. I an ATI Graphics card with all the drivers installed so what's the problem?:confused::confused:

---

### Post by Chonnawonga on 2007-10-22
Hi mellflores1,

Don't panic! :)

Did you have any trouble with any of the steps described in that guides? Did the driver install correctly?

What happens when you type this into a terminal?
```
fglrxinfo
```

Also, what motherboard are you using? That might be a factor.

---

### Post by mellflores1 on 2007-10-22
When i put fglrxinfo, it shows:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)


Im on an HP SR2050NX.
I previously had XP Media Center Edition 2005.

---

### Post by Chonnawonga on 2007-10-22
OK, so your graphics card drivers are installed properly, it seems. So far, so good.

How did the installation of xserver-xgl go? What happens if you enter this command again?
```
sudo apt-get install xserver-xgl
```

---

### Post by mellflores1 on 2007-10-22
This:

```
emilio@emilio-desktop:~$ sudo apt-get install xserver-xgl
[sudo] password for emilio:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1843kB of archives.
After unpacking 4854kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libglitz1.
(Reading database ... 111164 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

---

### Post by Chonnawonga on 2007-10-22
Oh, OK... that looks like it wasn't previously installed. Was it?

What happens if you restart X with CTRL+ALT+BACKSPACE and try Compiz now?

---

### Post by mellflores1 on 2007-10-22
It works! Thanks so much! How do I mark this as solved and how do I do that cube thing?

---

### Post by mellflores1 on 2007-10-22
nvm. got the cube thing working.

---

### Post by Chonnawonga on 2007-10-22
Great! Have fun with it.

---

### Post by Chonnawonga on 2007-10-22
To mark the thread as solved, go to the top of the screen and click on "Thread Tools" (just above your first post). Then click "Mark this thread as solved."

I'm glad I was able to help. Not so long ago I was just starting to learn the ropes myself. The forums aren't perfect, but they're a pretty darn good system!

Enjoy your desktop effects, and don't forget to show off to your friends. :)

---


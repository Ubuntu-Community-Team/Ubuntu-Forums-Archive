---
title: "AIGLX, ATI, Edgy, Beryl Speed"
date: 2006-11-04
forum: Desktop Environments
---

### Post by dnaxx on 2006-11-04
Hello,

I have installed Beryl over a standard Ubuntu installation. It realy looks great and works fine, but it is extremely slow (e.g. window scrolling).
I still have the standard graphic-drivers installed. Would the speed significantly increase, with the original ATI drivers?
If yes, is there a tutorial on how to install them with AIGLX? I just found tutorials for XGL. And when I try to install the drivers the conventional way, either Beryl itself stops working, or Gnome hangs up when it tries to start Beryl.

btw: "glxinfo |grep direct" returns "yes" for "direct rendering".

Thank you,

---

### Post by hegenious on 2006-11-04
I had a similar speed issue. This is how I fixed it:

I gather from your post that you run on an ATI card
install the fglrx driver through synaptic (search fglrx, install everything except fglrx-control, you don't need that one).
after fglrx is installed, run the following command in a terminal window:

sudo dpkg-reconfigure xserver-xorg

in the first window, select "fglrx" as the driver (not "ati")
accept defaults as you move along through driver setup, and in the "modules" window, select all modules except "v4l".
move along with setup and if not sure what to answer, accept the defaults.

reboot

login to your xgl session. In a terminal, type glxgears to test speed.
The gears should run fast and smooth. If so, your beryl will operate smooth as well!

hope this helps, please let us know.

---

### Post by dnaxx on 2006-11-04
Did not work, but in my oppinion Beryl is currently just for playing around and so the worse speed is "ok" ;).

---

### Post by CarpKing on 2006-11-04
The fglrx drivers do not support AIGLX, so all the tutorials for them must be for XGL.  Incidentally, did you have to do anything strange to get direct rendering with the open source drivers?  I seem to be having trouble with it.

---

### Post by dnaxx on 2006-11-05
I just followed this tutorial and it works like a charme with the default ATI drivers (after a fresh Edgy installation):
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

---


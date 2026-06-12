---
title: "Adding new mode by xrandr"
date: 2008-10-18
forum: Desktop Environments
---

### Post by jis on 2008-10-18
xrandr does not show all modes possible by a connected monitor (which is Nokia Valuegraph 447V). I don't know too much about the monitor, and xrandr manual has this:
>  --newmode <name> mode
              New modelines can be added to the server and then associated with outputs.  This option does the for&#8208;
              mer. The mode is specified using the ModeLine syntax for xorg.conf: hdisp hsyncstart hsyncend  htotal
              vdisp  vsyncstart vsyncend vtotal flags. flags can be zero or more of +HSync, -HSync, +VSync, -VSync,
              Interlace, DoubleScan, CSync, +CSync, -CSync.

I know that the monitor is capable at least 1024x768@72Hz. How do you tell it to xrandr?

---

### Post by murak on 2008-11-12
I would really like to know that too.

For example, if I have a monitor capable of 1680x1050 @ 60hz but xrandr says max resolution is 1024x768, how do I "make" the new mode?

Borowng your thread, hope its ok..

---

### Post by jis on 2008-11-12
It is ok; you have the same problem. And bumping is ok, too ;)

---

### Post by overdrank on 2008-11-12
Hi and maybe this link can help
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by jis on 2009-01-17
Thanks, overdrank. gtf and cvt utility give sligthly different results, though. Anyway I still haven't been able to use the generated mode; xrandr displayed: > xrandr: Configure crtc 0 failed

More about the problem with the monitor and graphics adatper [here]("https://answers.launchpad.net/ubuntu/+question/57763").

---


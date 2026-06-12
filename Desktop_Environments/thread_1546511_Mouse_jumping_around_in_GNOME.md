---
title: "Mouse jumping around in GNOME"
date: 2010-08-05
forum: Desktop Environments
---

### Post by Klopenator on 2010-08-05
For some weird reason whenever I start up my Ubuntu 10.04 laptop and log on, the mouse just randomly jumps over by the top right corner and right clicks.  This isn't just a major annoyance because whenever this happens my mouse can no longer left click.

---

### Post by jtarin on 2010-08-25
I have been having a very similar problem and reinstalls have no effect neither kernel upgrades. Usually, but not confined to, the behavior exhibits itself when any window is open...particularly a browser. The mouse will jump from one side of the screen to the other and back and forth. When it stops I still cannot gain control because any movement will over-compensate to a much higher degre tan input. The only way I can gain control is by a right-click and even then its not instantaneous. It will then start right ckicking and opening any menu it can find, but then eventually stops. Does anyoneelse share this behavior? Lucid 10.04 USB and PS2 Optical Mouse

---

### Post by x1a4 on 2010-08-27
Is it a USB mouse?  If so try a different port.  Also try changing mouse settings.  

Most likely though, it's a problem with the mouse itself, sending random signals.  Test using a different mouse (borrow one if you don't have extras) and see if it keeps happening with a different mouse.  If not, buy a new mouse.  

As a last resort try changing mouse drivers.  Edit /etc/X11/xorg.conf and change your mouse driver from the default /dev/input/mice to /dev/psaux

---

### Post by jtarin on 2010-08-27
> **x1a4 said:**
> Is it a USB mouse?  If so try a different port.  Also try changing mouse settings.  

Most likely though, it's a problem with the mouse itself, sending random signals.  Test using a different mouse (borrow one if you don't have extras) and see if it keeps happening with a different mouse.  If not, buy a new mouse.  

As a last resort try changing mouse drivers.  Edit /etc/X11/xorg.conf and change your mouse driver from the default /dev/input/mice to /dev/psauxNot USB..PS2...different mouse have tried and also USB. I have no xorg is the problem, I believe.
10.04 comes with no xorg configured. I'm thinking to install one to solve this problem as in all my years in Linux I never had this problem with any mouse and xorg.

---

### Post by sml on 2010-12-15
How is progress with this one .. any solutions?

---

### Post by Snoring Pug on 2011-06-13
I am having the same problem, but on a desktop (not laptop).  Using a rather old computer as an emergency, so hardly worth a system mention.  However, did try to install 11.04 first, regressed to 10.10 and am now on 10.04.2 LTS...  Tried 3 different mice, even the old roller ball type.
  
The crazy mouse syndrome happened on the first two installations (11.04 & 10.10), then installed 10.04.2 LTS - all seemed well and good, no jumping mouse and a steady OS.  Then installed Wine via the Software Center to get Native Instruments Audio Kontrol 1 up and running (to no avail).  Mouse went nuts!  Uninstalled NI-AK1 and Wine and rebooted.  Problem partially solved...

The only way I have managed to solve this extreme irritant is to do a fresh install.  Looks like I'm going to have to take that tedious route again.


Fujitsu Mainboard (?)
Intel(R) Pentium(R) 4 CPU 3.06GHz
1GB RAM

---


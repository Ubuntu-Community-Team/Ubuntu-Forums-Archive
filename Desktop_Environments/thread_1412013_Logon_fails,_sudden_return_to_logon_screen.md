---
title: "Logon fails, sudden return to logon screen"
date: 2010-02-20
forum: Desktop Environments
---

### Post by pudge on 2010-02-20
Juanty (9.10) xubuntu will not log on due to screen resolution changes, or sometimes no screen resolution changes at all. Something burps in the XFCE environment during the logon process and I am immediately returned to the logon screen.
 
I've been diligently trying to solve this problem for over a week by searching support forums and google searches. I've been digging into the depts of Jaunty far beyond my novice capabilities looking at xorg.conf files, using xrandr, adding PPAs with updated drivers, runing apt-get reconfigure, and still cannot solve this problem. I've tried two different video cards - ATI Radeon X300 SE and NVIDIA GeForce 7600gs - and still get the same result.
 
The symptom is that the logon process starts - the firefiles splash screen appears - then a wink and a blink and an immediate return to the logon screen. I know the window manager is blowing up somewhere and have tried my best to find it and fix it.
 
What is needed for users like me is the BulletProofX function described here - 
[https://wiki.ubuntu.com/BulletProofX](https://wiki.ubuntu.com/BulletProofX)
 
 
I'm downgrading to 9.04 simply to get an operational system. This is a dissapointment, it really is, as the few times I've been able to use Jaunty have been quite impressive, that is before the next disastrous logon.

---

### Post by knurledflanges on 2010-02-20
I'm having a very similar problem - [http://ubuntuforums.org/showthread.php?t=1410583](http://ubuntuforums.org/showthread.php?t=1410583) . On my system, I have xubuntu-desktop installed on a regular Ubuntu 9.10 install, but suddenly can't login to xfce, so I've been using Gnome instead, which works fine.

---

### Post by Hero of Time on 2010-02-21
Sounds like your sessions are bugged. Log in to a TTY (ctrl+alt+f1) and clear ~/.cache/sessions. Now try to log on again. You can also select a different session to log on to than your last session, as that should not load the session files.

---

### Post by efflandt on 2010-02-21
I had that issue with an old ATI card. Xubuntu 9.10 worked before first set of updates, then after that it would just recycle to login (xterm or console worked).  Gnome in regular Ubuntu 9.10 would not work at all from the start (half loaded and froze) unless I selected Failsafe GNOME (but that limits what you can do).

The (old ATI) solution for Xubuntu was to install xorg-driver-fglrx before doing any updates, or to install that package from "Failsafe GNOME" in regular Ubuntu.  Unfortunately Xubuntu has no failsafe X except a simple xterm.  So it helps to know how to use **sudo apt get** and what package you are looking for (assuming you have functioning network or install CD).

I am not familiar at all with what you may need for nVidia.

---

### Post by knurledflanges on 2010-02-21
> **Hero of Time said:**
> Sounds like your sessions are bugged. Log in to a TTY (ctrl+alt+f1) and clear ~/.cache/sessions. Now try to log on again. You can also select a different session to log on to than your last session, as that should not load the session files.

I tried this (although I deleted the files from within Gnome, but I don't suppose that should matter) and it didn't work.

---

### Post by U2010 on 2010-02-21
Hi,

had the same problem last month. In my case, there have been two files in my home directory with root:root ownership (.ICEauthority and .nvidia-settings-rc). Just changed ownership and everything is back to normal.

Hope this helps and greetings.

---

### Post by knurledflanges on 2010-02-22
I reported this is as a bug [(https://bugs.launchpad.net/ubuntu/+bug/525476)]("https://bugs.launchpad.net/ubuntu/+bug/525476"), and on the advice of the person who triaged it, I was able to finally solve the problem for me. 

> I deleted ~/.cache and everything in ~/.config/xfce4/ except for the /panels folder (didn't wanna have to set it up again if I didn't have to).

---

### Post by etisdale on 2012-03-26
I, too, recently dealt with this loop of returning to the login screen after a "successful" log in.

As best as I remember, my Xubuntu session froze after I moved a window by the title bar. The arrow pointer became a hand for moving the window, but would not function in any way. I do remember having some keyboard functionaliy (e.g., ALT would highlight menubar options) though, but that's about it.

Figuring my session was damaged, I killed the lightdm session from TTY1, and I deleted ~/.cache/sessions as described here:

> **Hero of Time said:**
> Sounds like your sessions are bugged. Log in to a TTY (ctrl+alt+f1) and clear ~/.cache/sessions. Now try to log on again. You can also select a different session to log on to than your last session, as that should not load the session files.

I then tried to restart lightdm, but I ended up with an XFCE Desktop. At this point, I simply rebooted--which is when I ran into the "login loop."

Per the following, I was able to find that .ICEauthority had become owned by root.

> **U2010 said:**
> Hi,

had the same problem last month. In my case, there have been two files in my home directory with root:root ownership (.ICEauthority and .nvidia-settings-rc). Just changed ownership and everything is back to normal.

Hope this helps and greetings.

I changed owndership as described, rebooted, and now everything is working again. :)

---


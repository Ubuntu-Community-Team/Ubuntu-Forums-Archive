---
title: "Kubuntu resolution problem, but not the one you've heard before"
date: 2009-08-26
forum: Desktop Environments
---

### Post by foufga on 2009-08-26
I've used Ubuntu for a while now with Gnome. I've decided I want to try out KDE.

I can't find the answer to my question on Google. Therefore, it has not been answered ;-)

_The short version_
**My Kubuntu VM will not render my desktop at the right resolution.**

_The long version_
My setup: Linux in a virtual machine on OS X.

Linux version: Kubuntu 9.0.4, fresh install
Virtual machine: VMware Fusion 2.0 (vmware-tools installed on Kubuntu)
Host OS: Mac OS X 10.5.8
Host machine: 15" Unibody MacBook Pro, resolution 1440 x 900
Graphics card: Nvidia GeForce 9600M GT, 256MB RAM

After installing Ubuntu, I installed vmware-tools from the virtual machine. No problem, except for seemingly unrelated problems (for example, vmware sharing did not install because of known VM sharing issues).

I then changed the resolution (through System Settings) to 1400 x 900, which seemed to work great. The desktop and all fonts rendered at the right resolution. But when I opened any window (by clicking on a folder or app), the fonts appeared entirely too large... as if they were still being rendered at 800 x 600.

I've tried restarting the xorg xserver (via dpkg-reconfigure xserver-xorg), but that doesn't change anything. Logging out/in or restarting doesn't help either. In fact, when you log back in, the screen resolution stays at 800 x 600 until you click on something, and then the whole desktop renders correctly. (Window fonts are still sized badly.)

Manually changing /etc/X11/xorg.conf values to my screen size make the desktop normal size but the window fonts extra small.

Very annoying, but I'd really like to check out KDE.

Any advice?

---

### Post by krazyd on 2009-08-27
Have you tried forcing a DPI value in System Settings > Appearance > Fonts ?

---

### Post by foufga on 2009-08-27
I just tried that, and it seems to have worked, thanks!

Now, it's not perfect, though, and I wonder if you could help me work out a couple of kinks. Logging out brings me to a login screen rendered at 800x600. Logging back in brings me to a desktop rendered at 800x600 that refreshes into a 1440x900 desktop after about 5 seconds. Can I fix those two problems? Are they indicative of a deeper problem?

---

### Post by krazyd on 2009-08-27
Seems that the X-server isn't detecting the correct DPI of your monitor for some reason.

Setting the DPI in system settings means that KDE resets DPI only once it starts - hence the correct DPI isn't set until KDE loads.

There are ways to set it manually as soon as the X-server starts, though I've never had to do it myself.

See this thread for some info on how to do this, especially Zorael's post: [http://ubuntuforums.org/showthread.php?t=1238039](http://ubuntuforums.org/showthread.php?t=1238039)

---

### Post by foufga on 2009-08-29
Hmm... I tried adding the -dpi 96 to kdmrc, but nothing changed. Do you think this is a problem with VMware and not KDE?

---

### Post by krazyd on 2009-08-31
could be...

you could try setting the DPI in xorg.conf instead of kdmrc. I'm not sure how though, you'd have to google.

---

### Post by foufga on 2009-09-03
Interesting update, this problem is systemwide and even affects X11 from within OS X (ie, running an X11 application using OS X's version of X11).

Does that mean it's a problem between X11 and my nVidia graphics card?

---

### Post by krazyd on 2009-09-03
Nope, what it probably means is that your monitor has a buggy [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data") implementation. X relies on reading that info from the monitor (or you setting it manually), while I suspect that OSX would have a specific monitor driver that provides the info.

---

### Post by foufga on 2009-09-09
Thanks for all your help, krazyd. It's people like you who make me want to come back (once I figure out KDE) and help out other people. Much appreciated.

---


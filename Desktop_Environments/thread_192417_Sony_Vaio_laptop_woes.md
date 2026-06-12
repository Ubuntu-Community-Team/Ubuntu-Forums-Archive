---
title: "Sony Vaio laptop woes"
date: 2006-06-08
forum: Desktop Environments
---

### Post by timelord726 on 2006-06-08
I just installed Ubuntu 6.06 fresh on my Sony Vaio PCG-K15 laptop, and now there are a few things that I'd like to get working before I go any further.  The operating system itself runs fine, but I'm very restricted in what I can do because the laptop's full functionality is not yet unlocked.

First of all, hotkeys.  I have a variety of Fn key combinations that do important things for me, like volume, brightness, and switching between LCD and external monitors.  There is also a hibernate shortcut.  Frankly, I don't much care about either the monitor control or the hibernate shortcut, but the volume and brightness controls are essential to me using the laptop properly.  I understand there might be some kind of kernel module or something to help me with this but I haven't been able to find out any more.

Next up is getting my graphics card handling 3D properly.  The card is an ATI Radeon Mobility IGP 345M.  It actually runs games surprisingly well in Windows, but I don't know how to get the ATI driver running in Ubuntu.  I experimented a bit with no luck.

Last, I want to try and be able to get suspend and hibernate working.  Right now, when I suspend, the machine will not come back on, and when I hibernate, the computer turns off, but when I boot it back up, it boots normally and doesn't restore the session like it should.  Any suggestions here would also be appreciated.

Thank you for any assistance you can offer!

---

### Post by fritz_monroe on 2006-06-19
I just corrected my FN key problem.  I made use of the posts on the [Gentoo forums]("http://forums.gentoo.org/viewtopic-t-335267-postdays-0-postorder-asc-start-0.html").  I didn't have to do all the patching of the kernel since I had acpi installed already.  About half way down, I grabbed the code and compiled it for use on my system.  I then tested and it lets me use the FN keys.  Eventually I'll set my system up to start this at boot up.

Hope this helps.

---


---
title: "Two gnome-shell processes"
date: 2015-12-19
forum: Desktop Environments
---

### Post by npsomas on 2015-12-19
I'm getting a weird problem on UbuntuGnome 15.10 (with the default version of gnome - 3.16.4) where there are two high-memory consuming gnome-shell processes running on the system from boot.  Observe the wonders of a ps aux | grep gnome-shell after a fresh boot:

gdm       1087  0.8  1.4 1351376 114600 tty7   Sl+  10:44   0:04 gnome-shell --mode=gdm --wayland --display-server
nick      2449  5.7  2.0 1530828 164620 ?      Sl   10:46   0:21 /usr/bin/gnome-shell
nick      2475  0.0  0.2 603012 16268 ?        Sl   10:46   0:00 /usr/lib/gnome-shell/gnome-shell-calendar-server
nick      3724  0.0  0.0   9504  2172 pts/2    S+   10:53   0:00 grep --color=auto gnome-shell

Doing a pstree, it appears that they both spawn from the same gdm session, however I can't figure out why two are remaining in what appears to be a completely loaded state in memory when only one is needed.  For a bit of background, despite fairly successfully trying the wayland session for about a week previously, I have discontinued it's full time use because I missed the ability to do 'alt-f2', 'r', but I see no reason why both sessions are still being loaded.

The second question is... anyone have any thoughts on why they are both running at about 1.5Gb?  I am running quite a few extensions which I'm guessing is the problem, but does anyone know of a good way to see their memory usage?  LookingGlass might have potential, but I can't see where it might reflect memory usage per extension (I have tried the garbage collector, but it doesn't recover much, maybe 100-200Mb, and is only temporary).  I'm trying to avoid going through and manually turning on/off extensions to diagnose this.

Thanks!

**edit:** Modifying "/etc/gdm/custom.conf" to include the line "WaylandEnable=false" doesn't appear to have any effect.

---

### Post by npsomas on 2015-12-19
Ok, I'm feeling a bit foolish.  I was looking at virt, not res memory, which is much more acceptable (although both virt and res still seem high).  Also, I believe the gdm owned gnome-shell is the login screen, whilst the user owned one is my session.  Doing a kill and locking the computer re-creates the login/gdm one, but at a quarter of the memory usage (100mb to 20mb resident).

So the remaining question is still, is there any good way of debugging extension memory usage?

---


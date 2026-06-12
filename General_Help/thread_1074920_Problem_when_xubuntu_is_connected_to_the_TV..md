---
title: "Problem when xubuntu is connected to the TV."
date: 2009-02-19
forum: General Help
---

### Post by IrishWristwatch on 2009-02-19
I installed xubuntu on my old Dell Dimension 2350, with Intel graphics, to use as a temporary htpc.  I had Windows XP on it before, but it was having problems so I decided to switch to Linux.  I have it connected to a sharp lc-30hv4u, which accept a max resolution of 1024x768.  Immediately after installing xubuntu, I got an incompatible resolution error from the television.  I busted out an old 19" LCD monitor, with a 1280x1024 max res, and connected it to the computer.  I saw that the resolution xubuntu was outputting at was 1152x865.  I logged in and changed the resolution via the control panels to 1024x768, and hooked it back up to the tv.  

Every works fine until I restart the machine.  I've noticed the login screen tries to default to 1280x1024 when connected to the monitor, even though I changed the resolution within the control panels to 1024x768.  The resolution returns to the correct size after I log in, but I'm out of luck at the login screen.  This is probably what causes the resolution to change to 1152x865 when the PC is connected to the television, the computer is trying to change to 1280x1024.  

How do I force the login screen to stick to a resolution of 1024x768?  I've read around and saw that I have to edit my /ect/X11/xorg.conf file, but when I opened it, the file was blank.

---

### Post by IrishWristwatch on 2009-02-20
bump.  I tried to reinstall xubuntu with the computer connected to the TV.  I also tried to make a custom xorg.conf file, but it gave me errors.  I'll post it later.

---

### Post by dabl on 2009-04-14
I'm dealing with the same problem, same Dell Dimension 2350 (Intel 845G/GL chip) and Dell 772c monitor, with a Kubuntu 9.04 installation.  After login, the display comes up at 1024 x 768, and I can manually set it to 1280 x 1024, "auto" refresh (which turns out to be 60Hz) and it looks fine and supports modest display demands, as long as I leave the Desktop Effects off, and don't try to run Google Earth.  But the screen setting will not survive a reboot -- it comes back up at 1024x768.  I've tried a "Mode" stanza in xorg.conf, and also a "metamodes" option in the "Screens" stanza, but they make no difference.

Has anyone got this chip to stay at 1280 x 1024 with the new Xorg?

---


---
title: "Dual Monitors worked - now borked"
date: 2008-09-18
forum: Desktop Environments
---

### Post by tinge on 2008-09-18
Hi - I hope this is the right place, it was a toss-up between here, Multimedia, and Hardware/Laptops.

I've been using Ubuntu as my exclusive desktop for around 6 months, and early on I configured my second monitor using Envy & Nvidia X Server Settings, and life was good.

Recently I thought I'd try some gaming and so disabled a monitor in Nvidia X Server Settings (it always failed if I tried it with both monitors running).  The game worked, but when I re-enabled the second monitor with Nvidia X Server Settings there was an accidental click-drag that moved X's thinking on the relative positions of my monitors.  I tried to undo the damage by dragging things back into alignment, but this only made things worse - MUCH WORSE.

my whole X window setup is now pushed down 300px-ish on both monitors by a black bar that doesn't redraw itself when content leaves (fills with ghosts of anything that has been in it)  See Screenshot:

[IMG]http://farm4.static.flickr.com/3195/2867479873_aa6952b2ec_b.jpg[/IMG]

I've done the googling I was capable of doing, and tried a few things including:
moving to my backup xorg
manually editing xorg
uninstalling and reinstalling my Nvidia drivers
getting a fresh xorg via:  sudo dpkg-reconfigure -phigh xserver-xorg
deleting a .nvidia-settings file

and there were a lot of results that were less usable that the screenshoted problem above, but none better.  I've managed to get it back to the problem described above, and would LOVE thoughts as to what I could do next.

thanks in advance
~tinge

Edit: More Info:

I've disabled desktop effects, and now that wonky area at the top of both screens stays the same, but still won't allow objects to be move onto it.  Further, when booting the screen appears normal and correct for 5-10 seconds, but then shifts down as the boot process completes.  This is driving me nuts.

---


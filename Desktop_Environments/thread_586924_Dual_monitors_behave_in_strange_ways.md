---
title: "Dual monitors behave in strange ways"
date: 2007-10-22
forum: Desktop Environments
---

### Post by apfsdsdu on 2007-10-22
I'm using Kubuntu Gutsy and trying to get a dual monitor setup with 19" and 15" panels to work. 
The bigger monitor is attached to an integrated Intel GMA3100 (using the "intel" driver) via DVI and the smaller one uses VGA. With a single monitor, everything "just works", with two, nothing really works.

With xrandr I can get a desktop that uses both monitors at their native resolutions. However, I have to run the xrandr commands manually every time I log in. The strange part is that when the setup sort of works, some programs draw their menus in weird places. In some cases it's enough to restart the program, but in others the menus are still in the wrong place. It looks as if they think the screen resolution is smaller than it really is. On the bigger, 1280 pixel-wide screen, drop-down menus stay within the leftmost 1024 pixels, even when the actual button (like the search box in Firefox) is beyond the 1024 pixel mark.


I also tried the KDE display configuration tool. It manages to configure X in a way that needs a hard reboot to the recovery mode and manual reconfiguration of X to recover.

---

### Post by britishbulldog on 2007-10-29
If you use xrandr to define the screen space you will need to run that command each time, the way around that is to modify your /etc/X11/xorg.conf 

I use two monitors most of the time but now and then don't have access to the second monitor, I created a one line script that has xrandr --off VGA-0 to switch off the second screen when necessary. If I don't do that, some items will start in the second screen space even if it's not there.

---

### Post by apfsdsdu on 2007-11-01
I wrote a script that does the xrandr stuff. The menus still show up in the wrong places. It's like the placement algorithm doesn't know the correct resolution. Otherwise it works well enough.

---


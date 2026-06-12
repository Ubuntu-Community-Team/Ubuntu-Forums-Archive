---
title: "Xfce: Mount devices applet shows only dvd drive"
date: 2008-02-12
forum: Desktop Environments
---

### Post by chochem on 2008-02-12
I've added the 'Mount devices' applet in my new Xubuntu install, being used to the snazzy Disk Mounter applet in Gnome. However, when I click it, only the dvd drive shows up in the dropdown list despite there also being a windows partition and an external hd attached, both of which show up on the desktop (the 'File/launcher' icons). 

Whether the partitions/drives are mounted or not doesn't seem to matter and thinking that maybe it was an ownership/permissions issue I checked the /media folder. They're all (DVD and drives) owned by root and I've got read permissions to all plus write execute to the hard drives). The options ('Properties' of 'Mount device' applet) don't seem to be much help - I'm not excluding any filesystems and the network thingy doesn't make any difference.

BTW - I know it's a different issue but the 'File/laucnher' icons under Desktop settings/preferences have some options, i.e. 'Show icons for: Home | Trash | File system | Removable devices'. Nothing I tick or untick there seems to make any difference. All icons still show. Any ideas?
EDIT: Figured out that last one - apparently you need to untick 'Allow Xfce to manage desktop' and then reselect it

---

### Post by Spookster on 2008-02-13
I'm having exactly the same issue - switched from gnome to xfce yesterday and I'd like to find a way to mount/unmount my various removable hard drives.

I suspect that this applet is working correctly and is only meant to show cdrom/floppy drives, but I'm not much of an expert. Does anybody know if it's possible to get the Gnome disk mounter applet in XFCE?

As for your second problem, I had that also and fixed it exactly the same way. It seems a bit clunky to be honest.

---

### Post by chochem on 2008-02-13
I've been hard at work at it, so there are actually several options open (getting Mount devices to work as we'd expect it to is not one, sadly) . Xfce panel applet 'Places' does pertty much what I need - it lists all the usual directories and devices, mounted or not,  and if you click on one that isn't mounted, you get the options 'mount'. Right-click mounted for unmount option.

As for GNOME applets, I believe I came across something that did just that... Here ya go: [http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin)
Guess you're supposed to install GNOME applets through apt/synaptic and then they will be available to the xfce4-applet.

Mind you I didn't pursue it, seeing as I'm loath to install GNOME stuff with hundreds of GNOME specific depencies....

Good luck with the switch and post them if you come across any gems of Xfce wisdom ;)

---


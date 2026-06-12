---
title: "Missing panel volume control"
date: 2009-11-30
forum: Desktop Environments
---

### Post by t616 on 2009-11-30
Ubuntu 9.19 Using Gnome Desktop
 
Problem: Newby messing around. Gnome-volume-control-applet missing from panel.  

Added functions from lower panel to top panel then deleted the lower panel. The volume control icon vanished somewhere during all this.

If I do an alt-f2 and run "gnome-volume-control-applet". The icon re-appears on the upper panel and functions as it did. Sound is good and volume control works. 

If I right click on the panel and try to add "volume control", it brings up the "add to panel" list but the "volume control" is not one of the listed programs.

I found the program in 2 locations:/ect/xdg/autostart, /usr/share/autostart.  

But the icon is gone again after a re-boot.
 
 
 How can I solve this? Thanks!

---

### Post by jacobs444 on 2009-11-30
9.19 desktop, wow are you from the future? No j/k really though, when doing as you have done I accidently covered the volume icon once, so something may be covering it, other than that you cancreate a custom launcher for it, or you could put it in startup applications.

system>preferences>startup applications

---

### Post by t616 on 2009-12-01
Sorry about missing the zero key. I checked the "startup applications" menu and "gnome-volume-control-applet" entry has it's box checked to run at startup but it doesn't run when the system boots. If I do an alt-F2 and bring up the run applications screen the gnome-volume-control-applet will run from there and shows up on the panel and works correctly.
Also the volume control is missing from the "add to panel" screen. I would hate to have to re-install Ubuntu just to get the icon back on the panel

---

### Post by garvinrick4 on 2009-12-01
Work around:  Go to Preferences and the to keyboard shortcuts and then give the volume
contols something like F12 to raise volume and F11 to lower volume and it works even better than applet for me Do not have to move pointer. You can even give music playing
device start-up key and skip to next song key, go back a song key. ect, ect ect.
  Simple but effective.

---

### Post by t616 on 2009-12-03
Gave up.....going to try some other  linux version

---

### Post by ItalOz on 2009-12-04
try looking [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8438998#post8438998")

---

### Post by pjstegmaier on 2009-12-19
> **t616 said:**
> Sorry about missing the zero key. I checked the "startup applications" menu and "gnome-volume-control-applet" entry has it's box checked to run at startup but it doesn't run when the system boots. If I do an alt-F2 and bring up the run applications screen the gnome-volume-control-applet will run from there and shows up on the panel and works correctly.
Also the volume control is missing from the "add to panel" screen. I would hate to have to re-install Ubuntu just to get the icon back on the panel

Have you tried Applications - Ubuntu Software Center - search volume control and download.

---

### Post by carsonrose on 2009-12-20
> **pjstegmaier said:**
> Have you tried Applications - Ubuntu Software Center - search volume control and download.

add to panel --> notification area.

---

### Post by citybird on 2009-12-30
add to panel notification area!! that was it!! 
didn't know it included the volume control.

EDIT:
one strange thing is the network connect icon sometimes changes into the volume control icon. why is that?

---

### Post by Green_Bean on 2010-02-13
Thanks so much, this worked for my missing network connection applet too.

---


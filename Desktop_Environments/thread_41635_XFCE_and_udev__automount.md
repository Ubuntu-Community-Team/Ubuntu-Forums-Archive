---
title: "XFCE and udev / automount"
date: 2005-06-14
forum: Desktop Environments
---

### Post by ghostrifle on 2005-06-14
Hey people,

I've installed XFCE from the repos on my hoary and I'm very pleased with it. The only thing I'm missing so far is the automount feature of gnome (udev).

When I plugged in my usbstick, a window with it's mount point appeared on the desktop when running gnome. But it's not the case for XFCE. Is there a way to create a smiliar behaviour ??

Or at least automounting to /media/whatever ??

regards,

Alex

---

### Post by cutOff on 2005-06-14
Open up a terminal, run [COLOR=Blue]gnome-volume-manager &[/COLOR] and save your session when you have to log out.

Hope this helps.

---

### Post by tristan on 2005-06-14
Beat me to it cutOff!

Actually I haven't worked out a way to make Xfce open a Rox filer window of newly inserted USB media, but you can get close. HEre's how I do it...

sudo gedit /usr/bin/startxfce4 and add **gnome-volume-manager & ** to the end of the file.

This will start gnome-volume-manager each time you start xfce, and cause an entry to be added to /media when a USB disk is plugged in.

All you need to do is create a menu entry **rox /media** or a rox bookmark to /media

Any USB devices you plug in or remove will appear/disappear from this window as usbdisk0, usbdisk1 etc.

---

### Post by ghostrifle on 2005-06-14
Thanx a lot !!! Having the usbX entries in /media is enough !   :grin:

---

### Post by nocturn on 2005-06-14
The  problem with this solution (I have it too) is that you cannot cleanly unmount the drives.

---


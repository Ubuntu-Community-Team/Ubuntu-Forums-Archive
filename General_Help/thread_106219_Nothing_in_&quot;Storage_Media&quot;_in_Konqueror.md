---
title: "Nothing in &quot;Storage Media&quot; in Konqueror"
date: 2005-12-20
forum: General Help
---

### Post by bigblop on 2005-12-20
I have added the button "Storage Media" to a menu i konqueror. But when I press it nothing happens. I have edited my /etc/fstab file to mount my external HDD and my winXP partiton. If I manually go to /media/winxp I get the contents of my winXP partition but it does not work when I "Storage Media" from the menu. Any ideas?

---

### Post by ad noiseam on 2005-12-20
I think this is a known bug with Kubuntu Breezy. However, you can very simply solve it. Create a new "link / shortcut to a device" (by right clicking) and link there the various hard drives or devices that should be in "storage media". It takes a minute and works perfectly.

---

### Post by bigblop on 2005-12-20
I am not sure what you mean. Should I just right click after I have pressed the "Storage Media" buttuon?

---

### Post by bigblop on 2005-12-20
Ok I think I figured it out. But for some reason it opens the disk in a new tab! How do I just make it open the content of the disk in the same window??

---

### Post by Adrian on 2005-12-20
[QUOTE=bigblop]I have added the button "Storage Media" to a menu i konqueror. But when I press it nothing happens. I have edited my /etc/fstab file to mount my external HDD and my winXP partiton. If I manually go to /media/winxp I get the contents of my winXP partition but it does not work when I "Storage Media" from the menu. Any ideas?[/QUOTE]

Here is an older thread on this subject:
[http://www.ubuntuforums.org/showthread.php?t=79204](http://www.ubuntuforums.org/showthread.php?t=79204)

---

### Post by ad noiseam on 2005-12-20
[QUOTE=bigblop]Ok I think I figured it out. But for some reason it opens the disk in a new tab! How do I just make it open the content of the disk in the same window??[/QUOTE]

I am not in front of my Kubuntu installation right now, but I think that if you right click anywhere (on the desktop or in any folder), you have an option to add a link to a device. If you click on this, a list of device will appear. You can use this to "place" your hard drives in the storage folder (or anywhere else).

Nicolas

---


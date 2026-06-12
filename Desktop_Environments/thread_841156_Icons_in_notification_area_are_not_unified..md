---
title: "Icons in notification area are not unified."
date: 2008-06-26
forum: Desktop Environments
---

### Post by pencilcheck on 2008-06-26
As you can see in the attachment, the icons for rhythmbox and network connectivity are not resized correctly.

Although in my current theme, it has 16x16 icon for rhythmbox icon, but it's not used.

I don't know where to find the icon for the network, but apparently it's not resized either.

Is there a solution to this?

---

### Post by ericesque on 2008-07-21
(kinda bump)  I too am trying to figure out how to change the notification area icons.

---

### Post by ericesque on 2008-07-21
found this thread: [http://ubuntuforums.org/showthread.php?t=865208](http://ubuntuforums.org/showthread.php?t=865208)

@pencilcheck, your paths may be different than the instructions that follow because it looks like you aren't using a default icon for rhythmbox.  Yours is probably coming from an icon theme you installed.  Look in ~/.icon and find your current icon set. If you find your rhythmbox icon and want to swap it out, make sure to back up the original in case you want to revert back to the old one-- or if you accidentally modify the wrong icon!   


I managed to modify my rhythmbox icon by replacing the two icons as follow: 

while playing:
/usr/share/icons/hicolor/16x16/apps/rhythmbox.png

when not playing:
/usr/share/rhythmbox/icons/hicolor/16x16/status/rhythmbox-notplaying.png

once the files were in place, I issued a  ```
killall gnome-panel
``` in order to restart the panels--which updates the icons.

---


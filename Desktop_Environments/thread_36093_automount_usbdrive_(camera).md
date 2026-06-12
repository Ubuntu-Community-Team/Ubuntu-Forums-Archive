---
title: "automount usbdrive (camera)"
date: 2005-05-21
forum: Desktop Environments
---

### Post by crash369 on 2005-05-21
hello.  the other day, i connected my camera (nikon) to a usb port and turned it on.  to my pleasure, the camera was automounted as /media/usbdrive.

however, during an attempt to copy files from the camera to my home (both by "copy" +"paste" and by dragging in nautilus, the files were erased off my camera  :mad: and they never made it to my home dir.

in any case, i would like to know how to make sure that when my camera is automounted, it is read-only by default.  any ideas?

---

### Post by GTvulse on 2005-05-21
[QUOTE=crash369]hello.  the other day, i connected my camera (nikon) to a usb port and turned it on.  to my pleasure, the camera was automounted as /media/usbdrive.

however, during an attempt to copy files from the camera to my home (both by "copy" +"paste" and by dragging in nautilus, the files were erased off my camera  :mad: and they never made it to my home dir.

in any case, i would like to know how to make sure that when my camera is automounted, it is read-only by default.  any ideas?[/QUOTE]

 There should be an entry in /etc/fstab pointing to /media/usbdrive. Check the fourth column ("options") and make sure that it includes the option "ro". Observe the options for your CD/DVD drive  mount point, that's a good guildeline, Ahh! And read the fstab manual page as well, type "man fstab" at the command line of a terminal emulator.

---

### Post by crash369 on 2005-05-22
that's the first place i looked... no entry for usbdrive

---

### Post by cwaldbieser on 2005-05-22
Maybe the pmount command is being used to mount the camera under the hood.  According to the man entry for that, you don't need an fstab entry to use it.

Not sure how Gnome links into that.  Maybe with the /etc/hotplug system?  I'm not really sure, though, as I mostly use KDE.

---

### Post by GTvulse on 2005-05-22
[QUOTE=crash369]that's the first place i looked... no entry for usbdrive[/QUOTE]

Hmmm.... Not even when you have the camera plugged in? Even if not, you can type mount in a terminal window and obtain the actual mount settings. With that information, you can build an fstab line for /media/usbdrive  that would be obeyed by the system the next time you mounted the camera.

---

### Post by crash369 on 2005-05-22
[QUOTE=dradul]Hmmm.... Not even when you have the camera plugged in? Even if not, you can type mount in a terminal window and obtain the actual mount settings. With that information, you can build an fstab line for /media/usbdrive  that would be obeyed by the system the next time you mounted the camera.[/QUOTE]
haven't thought of that. i'll try it :)

---


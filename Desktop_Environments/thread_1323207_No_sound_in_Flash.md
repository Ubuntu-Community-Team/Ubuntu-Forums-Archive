---
title: "No sound in Flash"
date: 2009-11-11
forum: Desktop Environments
---

### Post by Melcar on 2009-11-11
I'm having problems with flash sound in Kubuntu.  Flash videos have no sound in Firefox and in any of the standalone flash players I have tried (swfdec and gnash).  However, Konqueror does play sound in flash movies.  Yes, I do have sound system wide and my sound card is configured correctly, and have the flash plugins installed.

---

### Post by klemes on 2009-11-11
Try to install padevchooser ( I am assuming you are running pulseaudio here)
and run it.Then choose Volume control from the taskbar icon and see if the streams from firefox are muted for some weird reason.Just A long shot but worth trying I think.

---

### Post by Islington on 2009-11-11
this is a known bug. I installed flashplugin-nonfree-extrasound, as this was previously uninstalled. I restarted firefox, and sound is back. This is on Karmic Kubuntu, with the flash being installed from the medibuntu repos (using this guide:[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)).


[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/396558](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/396558)

---

### Post by Melcar on 2009-11-11
Kubuntu doesn't have PA installed by default, and although I have no reservations against PA, I rather not install extra stuff of that nature.  Will try installing the extra flash plugin and see if that works.

---

### Post by Melcar on 2009-11-11
Now Konqueror has no sound :-x.  Only way I could get everything to work nice was installing PA.  Everything works now.

---


---
title: "composited desktop-environment error??"
date: 2010-09-29
forum: Desktop Environments
---

### Post by TheDexter1111 on 2010-09-29
For some reason when i booted up today i got the message:

"You are not running under a composited desktop-environment. The Desktop Art Plugin cannot work without one."

Any Idea what this means or how I can fix it? it has stuffed around with my conky positioning too for some reason...

Im running Ubuntu Lucid 10.04 with Gnome DE

when i do a screenfetch is says - 'Finding desktop environment...found as 'GNOME'

I've tried this [http://ubuntuforums.org/showthread.php?t=1522654](http://ubuntuforums.org/showthread.php?t=1522654)
but didn't work for me unfortunately...

any help much appreciated :D

---

### Post by roggenschrotbrot on 2010-09-29
either activate desktop-effects or use gconf-editor to set "/apps/metacity/general/compositing_manager" to true

---

### Post by TheDexter1111 on 2010-09-29
> **roggenschrotbrot said:**
> either activate desktop-effects or use gconf-editor to set "/apps/metacity/general/compositing_manager" to true

didn't work unfortunately... and funny thing is now, i took rhythmbox off startup apps altogether, and although i no longer get the error message, my conky config is still being affected (which i have to kill and re-launch to fix) and same with my adeskbar... its just annoying now.

the rhythmbox desktop art works fin when i launch rhythmbox, but just want to sort out the glitch when i boot.

edit: error message still coming up

---

### Post by frogotronic on 2011-10-04
Fix posted here: [http://ubuntuforums.org/showpost.php?p=11311106&postcount=6](http://ubuntuforums.org/showpost.php?p=11311106&postcount=6)

- CH

---


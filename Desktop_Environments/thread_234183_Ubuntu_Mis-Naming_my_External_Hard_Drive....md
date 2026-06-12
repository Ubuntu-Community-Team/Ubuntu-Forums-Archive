---
title: "Ubuntu Mis-Naming my External Hard Drive..."
date: 2006-08-11
forum: Desktop Environments
---

### Post by dragoonmac on 2006-08-11
OK, I'm not sure if this is the right forum for this, but I'm having a bizaare problem I can't work out on my own. I recently reinstalled Ubuntu 6.06 (I mucked up my last version while playing with KDE...) upon first install it detected my external HD (an 80 gig drive in a case enclosure, USB 2.0, FAT 32 partition). Upon first reading it it read its label (and subsequent mount point) of "data" just fine. After a reboot it got wierd. It labelled (and mounted) the drive as "e is to it!" .
After looking around in the forums and on google I can't figure it out. I dual boot Windows XP and windows reads (and can change its label of "data") just fine. I searched for the text string and found four files (3 txt 1 html) that contain that string of text. The only one that I could even think might affect a label like that is a copy of the GnuGPL from a japanese translator sitting in a structure /programs/jpreader/gnugpl.txt
Does anyone know what causes this/how to fix it? It's not a major issue, it's just annoying.
P.S. I cant rename it in Linux...

---

### Post by orb9220 on 2006-08-11
in xp does the actual label have e:data or just data as it is not a good  idea to use a : in the actual label name.

All I can think of. Sorry

---

### Post by dragoonmac on 2006-08-11
Nope, in XP it Maps as F, but it's label is simply "data"

---

### Post by orb9220 on 2006-08-11
Ok well the only other thing to try if you havn't already is reboot with it still plugged in. And check then unplug reboot then plug back in and see if it stays the same. 

If it is the same under both then there is a file somewhere to be modified  or deleted.

Anybody else have info where ubuntu stores the info for usb devices?

---


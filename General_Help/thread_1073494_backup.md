---
title: "backup"
date: 2009-02-18
forum: General Help
---

### Post by steeler on 2009-02-18
hi i'm looking for a backup utility..basically i have 2 equal capacity hard drives 1 internal and 1 external..i want to use the external for backup.. so what i'd like it to do is copy the changes made to internal drive to the external one so both drives are identical (mirrors)..and i'd like to do this on demand..not automatically using deamons.thanks.

---

### Post by Slim Odds on 2009-02-18
rsync

---

### Post by mikewu on 2009-02-18
Definitely rsync. You'll have to do one full backup, but after that rsync only copys the differences. 

If you have 2 drives, you might want to consider making a RAID 1 set up. The linux kernel can handle it and it will handle everything automatically and mirror the drive. 

Here's a link for rsync:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)
and of course the man page.

Here's a link for RAID:
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

---

### Post by Slim Odds on 2009-02-18
> **mikewu said:**
> If you have 2 drives, you might want to consider making a RAID 1 set up. The linux kernel can handle it and it will handle everything automatically and mirror the drive. 

Not if one is an external drive!

---

### Post by jerrrys on 2009-02-18
and if you like gui

[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)

---

### Post by steeler on 2009-02-18
thanks..last question..when i delete a file from the internal drive is it possible the file to be deleted from the external drive too? so that both drives are exact mirrors? and so i don't have any free space issues?

---

### Post by Lars Stokholm on 2009-02-18
man rsync :) Have a look at --delete.

---

### Post by binbash on 2009-02-18
+1 for Grsync, good app

---

### Post by haddog on 2009-02-18
Very nice. I'll have to try this.

---

### Post by steeler on 2009-02-18
thanks :D

---

### Post by haddog on 2010-04-02
Still haven't tried Grsync. Stuck on clonezilla. It works great.

---

### Post by Cracauer on 2010-04-02
> **steeler said:**
> hi i'm looking for a backup utility..basically i have 2 equal capacity hard drives 1 internal and 1 external..i want to use the external for backup.. so what i'd like it to do is copy the changes made to internal drive to the external one so both drives are identical (mirrors)..and i'd like to do this on demand..not automatically using deamons.thanks.

This isn't really a backup. If you have silent corruption on your primary drive, or fatfinger something without noticing, your backup will usually have the previous good state long overwritten by the time you notice the bad data.

Also, I wouldn't trust USB with any kind of real data storage.

---


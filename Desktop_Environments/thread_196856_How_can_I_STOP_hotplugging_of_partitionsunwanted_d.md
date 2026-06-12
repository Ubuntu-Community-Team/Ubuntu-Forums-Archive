---
title: "How can I STOP hotplugging of partitions/unwanted drives?"
date: 2006-06-14
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2006-06-14
Sorry if I didnt get the terminology right but I want to STOP this new "feature" (so Ive read). If I comment out NTFS/Ext3 partitions in my FSTAB they still show up. I get 2 "Filesystem" or "root" partition entries. I also want to stop the card readers in my Dell2405 from showing up via USB.

---

### Post by MetalMusicAddict on 2006-06-17
Hello world. :)

---

### Post by MetalMusicAddict on 2006-06-19
Well it looks like after this last round of major updates the duplicate entries are gone (on all 4 of my Ubuntu PCs). :) Problem solved.

---

### Post by cotcot on 2006-06-19
--> System --> Preferences --> Removable media and stations :
Uncheck the options for automount.

---

### Post by MetalMusicAddict on 2006-06-19
It wasnt a "Automount" problem. Drives that were completely commented out of the fstab were still being mounted and there were duplicate entries for OS drives. It meda "Computer" have almost twice as many drives listed as needed.

---


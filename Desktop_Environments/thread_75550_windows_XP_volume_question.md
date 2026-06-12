---
title: "windows XP volume question"
date: 2005-10-13
forum: Desktop Environments
---

### Post by thrust on 2005-10-13
i mounted my windows XP partition using the commands i found on ubuntuguide.org. i've noticed that there are commands to make fat volumes Read/Write, i was wondering if there was a way to make ntfs volumes read/write not just read i would really appriciate it if i got some feed back

Matthew

---

### Post by aysiu on 2005-10-13
I haven't tried it, but you could look into 

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

I just resized my NTFS partition and made a big, fat FAT one.

---

### Post by dcarpenter on 2005-10-13
I would actually avoid ever trying to make an NTFS writeable in a linux distro just because there is a chance that this will render your partition unreadable.  It is still in the experimental stages so I wouldnt mess with it just yet.

---

### Post by drogoh on 2005-10-13
[QUOTE=thrust]i mounted my windows XP partition using the commands i found on ubuntuguide.org. i've noticed that there are commands to make fat volumes Read/Write, i was wondering if there was a way to make ntfs volumes read/write not just read i would really appriciate it if i got some feed back

Matthew[/QUOTE]

The kernel option is disabled by default.  Do a search on the forums for the terms "ntfs write" and you'll see a lot of threads on this and why writing to NTFS should be avoided.  Now if it were FAT32 on the other hand.....

---

### Post by thrust on 2005-10-13
thanks alot ppls i guess i'm not sure what i'll do

---

### Post by Elv13 on 2005-10-13
what are you taliking about, linux-ntfs can write on ntfs, this is on their website

---


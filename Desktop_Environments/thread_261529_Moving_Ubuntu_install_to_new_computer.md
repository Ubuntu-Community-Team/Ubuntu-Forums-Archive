---
title: "Moving Ubuntu install to new computer"
date: 2006-09-20
forum: Desktop Environments
---

### Post by bradsucks on 2006-09-20
If I were to take my Ubuntu install out of my current server and throw it in a different computer, would things still work? Windows XP hates it so I'm hesitant to try. I'd really rather not reinstall everything.

---

### Post by nullmind on 2006-09-20
Well, if the hardware is different, you will likely need to configure it. Also if the disk devices are different (eg; /dev/hda3 instead of /dev/hda1 or even /dev/sda instead of /dev/hda) you will need to update those paths or else it wont be able to mount things (edit your fstab)

No real way to know except to try I suppose.

---


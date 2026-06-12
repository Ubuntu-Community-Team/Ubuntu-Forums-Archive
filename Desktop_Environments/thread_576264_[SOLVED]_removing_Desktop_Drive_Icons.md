---
title: "[SOLVED] removing Desktop Drive Icons"
date: 2007-10-15
forum: Desktop Environments
---

### Post by kshane on 2007-10-15
Hi all.

I am trying to remove the desktop icons for the other partitions, etc.  I fired up gconf-editor and unchecked the boxes under Apps>>Nautilus>>Desktop and they are _still_ there.

In my searches I saw a suggestion to change the mount point in fstab to /mnt from /media.  When I did that the drives did not mount at all.

Honest!  I have searched over and over and have not come up with anything else.

Can some one help?

Kevin

---

### Post by Caffeine_Junky on 2007-10-15
hey there...
The following code will do the job... and you can toggle "true" or "false" if you change your mind...

```
gconftool-2 -s /apps/nautilus/desktop/volumes_visible --type=bool false
```

Edit:

The following link will show how this is done using a GUI:   [http://ubuntuforums.org/showthread.php?t=598245](http://ubuntuforums.org/showthread.php?t=598245)    ...posts #3 & #4

---

### Post by kshane on 2007-10-15
> **Caffeine_Junky said:**
> hey there...
The following code will do the job... and you can toggle "true" or "false" if you change your mind...

```
gconftool-2 -s /apps/nautilus/desktop/volumes_visible --type=bool false
```

OMG!  ***_Thank you, thank you, thank you! _*** I have been searching that one for days!  Just could NOT find anything else!

Thanks one last time!!!

Kevin

---

### Post by Caffeine_Junky on 2007-10-15
No problem Kevin!  ..glad I could help :)

---


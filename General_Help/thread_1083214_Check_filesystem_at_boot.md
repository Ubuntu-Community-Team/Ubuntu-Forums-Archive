---
title: "Check filesystem at boot"
date: 2009-02-28
forum: General Help
---

### Post by DPic on 2009-02-28
fsck runs every 30 mounts but how can i tell it to run at the next boot?

---

### Post by DPic on 2009-02-28
gparted can only run on an unmounted filesystem and i can't unmount my root partition. a live CD is an option that i shouldn't have to resort to. 

anybody know how to do this?

---

### Post by bodhi.zazen on 2009-02-28
to run fsck on next boot :

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

I understand your feelings re: fsck and running on an unmounted partition, but I do not know of a fix.

ext4 is supposed to have a defragemntation tool, but I have not seen it in use yet. Perhaps there will be some additional features as well.

---

### Post by oldos2er on 2009-02-28
Boot into recovery mode, when the menu comes up, choose fsck.

---


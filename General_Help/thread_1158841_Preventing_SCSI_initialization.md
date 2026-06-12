---
title: "Preventing SCSI initialization"
date: 2009-05-14
forum: General Help
---

### Post by jasonpp on 2009-05-14
Hello all, I'm trying to prevent the two SCSI drives in my computer from initializing at boot. I can stop them manually by using #sg_start --stop /dev/sdc but would like to know how to stop them spinning up in the first place! I'm using ubuntu 9.

Thanks,
Jason

---

### Post by dandnsmith on 2009-05-14
How about setting your fstab to not checking the filesystems on those drives automatically. The Man pages have, I believe, the necessary data (entries 5,6 for a filesystem?)

---

### Post by jasonpp on 2009-05-14
Thanks for the idea Derek... tried it but to no avail - even removing the disks from fstab makes no difference - indeed, one of the two drives I never even defined in the first place!

Thanks,
Jason

---


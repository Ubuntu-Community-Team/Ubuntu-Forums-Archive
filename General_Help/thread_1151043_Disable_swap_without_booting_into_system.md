---
title: "Disable swap without booting into system?"
date: 2009-05-06
forum: General Help
---

### Post by juxtaposed on 2009-05-06
I have an install with an unencrypted /boot, an encrypted root and encrypted swap. My swap got corrupted but I could still boot, only without the use of the swap. I tried to fix it but I would up breaking it more, so that now I can't booth up at all. It hangs on enabling crypto disks.

Is there a way I can disable the swap or that encrypted partition without being able to boot the system? The only live cd I have is an old 7.04 one. It can edit files on the /boot partition, but it doesn't have cryptsetup by default (so I can't load the root partition to change anything) and the repositories for 7.04 don't exist anymore to download it, and I can't find it anywhere else.

EDIT: Booting it again, it worked. Still without swap, but I think I can fix that.

---


---
title: "dm-crypt and migration - Encrypted file system"
date: 2005-10-17
forum: Desktop Environments
---

### Post by anthro398 on 2005-10-17
I plan to migrate in-place several 5.04 Hoary machines to 5.10.  Has anyone had experience migrating systems with encrypted usr and swap partitions (ala [https://wiki.ubuntu.com//EncryptedFilesystemHowto]("https://wiki.ubuntu.com//EncryptedFilesystemHowto")?

Of course I'd love to back up but I don't have anywhere to temporarily park ~300GB of data.  I'd just like to know that the /dev/mapper scheme is more mobile than cryptoloop prior to migration.

---

### Post by docomo on 2005-10-17
I have upgraded a hoary system with encrypted root and swap using dm-crypt. The encrypted root did not work 'out of the box', i.e. the system would not start with the breezy kernel, so I had to run mkinitrd using the new kernel to create an initrd that would work. The encrypted swap worked fine.

I also have another encrypted partition that still works fine.

---


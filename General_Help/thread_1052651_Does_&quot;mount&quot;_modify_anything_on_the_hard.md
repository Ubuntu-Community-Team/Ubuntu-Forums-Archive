---
title: "Does &quot;mount&quot; modify anything on the hard drive itself?"
date: 2009-01-27
forum: General Help
---

### Post by fducros on 2009-01-27
Hi, 

I have the famous GRUB error 17, after erasing an Ubuntu partition from my work laptop, to put it on my home desktop with Easeus Partition Manager.

I would like to try and force mount the ntfs partition, but I am afraid it would modify something on the hard drive and make it unrepairable.

Thoughts?

---

### Post by dhughes on 2009-01-28
I'm not sure but I often will put an old hard drive (which may have stuff on it but I'm not sure) into a system and boot it up with a Linux LiveCD so I can check the contents on the hard drive and copy it to a USB key.

---

### Post by blazemore on 2009-01-28
Well, it probably won't modify the hard-drive, but it can bugger the filesystem, if you force mount an unclean one. Especially NTFS.

I have had experience with mount screwing hard drives though: During installation, I accidentally "used" my Windows partition as fat32.... that broke Windows boot (funny, that!).

---


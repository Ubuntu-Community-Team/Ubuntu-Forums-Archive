---
title: "DOSEMU Permisions Problem.."
date: 2009-03-25
forum: General Help
---

### Post by tito_pt on 2009-03-25
From a Long time i have been using DOSEMU with no problem, recently I intaled ver 8.10 and instaled DOSEMU.. 

In fstab I created all my network Drives and with lRedir use Drive Leteres for those network drives, with "Nautilus" I can browse, erase, view, create files on those drives, with DOSEMU on Windows shares I have full acess, create, erase, modify, on SAMBA shares I can erase, but can't open or modify the files. What might be the problem?

---

### Post by anezch on 2009-04-29
I'm facing the same problem and I almost giving up on this, maybe I should contact ubuntu developers for this. I think it's because the mmap_min_addr. Because dosemu won't work on hardy without setting it to 0. And I suspected it affect the way dosemu access the filesystem.

This force me to fallback to 7.10 where dosemu+samba works great.

---

### Post by tito_pt on 2009-04-30
> **anezch said:**
> I'm facing the same problem and I almost giving up on this, maybe I should contact ubuntu developers for this. I think it's because the mmap_min_addr. Because dosemu won't work on hardy without setting it to 0. And I suspected it affect the way dosemu access the filesystem.

This force me to fallback to 7.10 where dosemu+samba works great.

And it's possible to contact them? for what I see when you have a problem, either the users know how to solve it, or you end up in a "Dead End".

---

### Post by tito_pt on 2009-05-04
> **anezch said:**
> I'm facing the same problem and I almost giving up on this, maybe I should contact ubuntu developers for this. I think it's because the mmap_min_addr. Because dosemu won't work on hardy without setting it to 0. And I suspected it affect the way dosemu access the filesystem.

This force me to fallback to 7.10 where dosemu+samba works great.

It seams someone heard us, just update your Ubuntu to version 9.05 e now it works..

---

### Post by anezch on 2009-05-22
> **tito_pt said:**
> It seams someone heard us, just update your Ubuntu to version 9.05 e now it works..

wow, that's good. I haven't tried it but that's a good news. I think Hardy has some serious problems, regarding it's an LTS.

---


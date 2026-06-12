---
title: "itunes for windows under VM cant burn cd"
date: 2009-01-06
forum: General Help
---

### Post by Kain000 on 2009-01-06
Hey everyone,
Just wanted to ask if anyone has used itunes under a virtural machine and if so if they have had any trouble burning a disk form a playlist.

I installed itunes for windows in virtural box so I could gain access to the store, I've bought one album and just want to burn it and be rid of itunes all together, but when I tell it to burn a disk the message bar at the top tells me that "disk burner or software not found"  

DOes this mean it hasnt mounted my Cd Dirve?

---

### Post by b0b138 on 2009-01-06
"Using the host drive normally provides a read-only drive to the guest. As an ex-
perimental feature (which currently works for data only, audio is not supported), it is
possible to give the guest access to the CD/DVD writing features of the host drive (if
available)."

---

### Post by Kain000 on 2009-01-06
alright I saw that I cannot burn audio cd's but I should still be able to burn data cd's correct?   I cannot even mount the drive in the guest, or see the cd in it

---

### Post by b0b138 on 2009-01-07
Check that "mount cd/dvd drive" is checked under the vm settings and that host is selected and not image file. If you have more than one cd/dvd drive make sure the one you want to use is selected. And also select "enable passthrough"

---


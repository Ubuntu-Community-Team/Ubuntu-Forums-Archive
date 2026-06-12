---
title: "Amarok doesn't see external hard-drives--can't add music to collection"
date: 2009-05-17
forum: General Help
---

### Post by KWhistle on 2009-05-17
Well, the title pretty much says it all.  I'm trying to configure my music collection, part of which is on my windows partition, the other is on an external hard drive.  Amarok doesn't see either.  Any way to fix it?

K

PS  I'm far from an advanced user, so simple instructions would be appreciated.

---

### Post by sieve on 2009-08-18
I had the same problem until I figured out that the external hard drive was mounted in /media/*drivename* even though it shows up on the desktop, so try directing Amarok there.  I did and it works fine now.

---


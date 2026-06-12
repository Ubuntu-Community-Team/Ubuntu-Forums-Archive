---
title: "cp -r Locks Up Computer Completely"
date: 2009-06-06
forum: General Help
---

### Post by Shames0 on 2009-06-06
I've been having this issue for a while now. The first time it happened I was trying to copy some music files from the windows side of my partition to my linux side, and the whole system Just froze up. I had to do a hard shutdown and run a manual fsck after it booted back up to get things operational again. This was done just with copy and paste

I recently re-installed ubuntu 9.04 on my system, and I decided to try the runing:

 cp /media/disk -r Desktop/

from the windows partition to my desktop in ubuntu. It looks like it copied 11GB out of the 12 that it was supposed to copy when the whole thing locked up again. I had to do the same process as before to get up and running again. 

My last attempt I decided to try to just update the files on my Ubuntu side using:

cp /media/disk -r -u Desktop/

Still same result.

Any Ideas Suggestions Are GREATLY appreciated. 

Thanks in Advance.

---

### Post by colau on 2009-06-06
> **Shames0 said:**
> I've been having this issue for a while now. The first time it happened I was trying to copy some music files from the windows side of my partition to my linux side, and the whole system Just froze up. I had to do a hard shutdown and run a manual fsck after it booted back up to get things operational again. This was done just with copy and paste

I recently re-installed ubuntu 9.04 on my system, and I decided to try the runing:

 cp /media/disk -r Desktop/

from the windows partition to my desktop in ubuntu. It looks like it copied 11GB out of the 12 that it was supposed to copy when the whole thing locked up again. I had to do the same process as before to get up and running again. 

My last attempt I decided to try to just update the files on my Ubuntu side using:

cp /media/disk -r -u Desktop/

Still same result.

Any Ideas Suggestions Are GREATLY appreciated. 

Thanks in Advance.
From Places menu above go to the drive and copy whatever you want.

---


---
title: "Rsync - samba mount chgrp"
date: 2008-12-11
forum: General Help
---

### Post by Dusenberg on 2008-12-11
I have a ubuntu laptop which remote mounts a windows pc ntfs filesystem (samba) and I want to rsync backup my ubuntu .evolution directories to a directory on the pc.

I have tried "rsync -av [laptop_dir] [pc dir]" and i get a lot of errors "rsync: chgrp ..... operation not permitted" and a final: rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

I've tried the -ogt options so (i think) rsync doesn't change those fields but same result.  Anybody know how to get a clean rsync?? Cheers

---

### Post by Titan8990 on 2008-12-11
Download and install Delta Copy Server on the Windows machine. This will allow you to use rsh to send the rsync files from Ubuntu to Windows. The end syntax will be something like this:

rsync -av [laptop_dir] [pc_ipaddy]:[delta copy server module name]

---

### Post by Dusenberg on 2008-12-12
> **Titan8990 said:**
> Download and install Delta Copy Server on the Windows machine. This will allow you to use rsh to send the rsync files from Ubuntu to Windows. The end syntax will be something like this:

rsync -av [laptop_dir] [pc_ipaddy]:[delta copy server module name]

Thanks - I'll give that a try later today:p

---


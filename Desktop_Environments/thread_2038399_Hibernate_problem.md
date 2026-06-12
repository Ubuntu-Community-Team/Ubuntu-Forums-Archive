---
title: "Hibernate problem"
date: 2012-08-06
forum: Desktop Environments
---

### Post by rdhddad on 2012-08-06
[http://paste.ubuntu.com/1132806](http://paste.ubuntu.com/1132806)

Get the following error message when I attempt to boot up into 12.04:

"resume: libgcrypt version: 1.5.0
resume: Could not sat the resume device file '/dev/dm-2' Please type in the full path name to try again or press ENTER to boot the system'

The system won't boot. I think my swap has disappeared.

Nothing I've researched seems to work. Boot-repair didn't work.

Please advise!

Thanks,

Jim

---

### Post by Toz on 2012-08-10
Try booting with the kernel parameter **noresume**. This will restore the swap space back to swap deleting the hibernate image and allow for a fresh boot of the system.

---


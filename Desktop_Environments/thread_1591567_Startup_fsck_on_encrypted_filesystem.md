---
title: "Startup fsck on encrypted filesystem"
date: 2010-10-09
forum: Desktop Environments
---

### Post by treacl on 2010-10-09
I'm running Ubuntu 10.04 (amd64) with an encrypted filesystem, and the startup fsck seems only to check one of my two volumes:

/boot - ext2, not encrypted, seems to get checked
/ - ext4, dmcrypt/luks encrypted, seems NOT to get checked

I say "seems," because when the check runs it does one of two things: Either it says "Checking disk 1 of 1" or somesuch, or it says "Checking disk 1 of 2." In either case, the check takes only a few (~5) seconds, and it never goes on to say "Checking disk 2 of 2."

Is there any way to confirm which volumes exactly fsck is checking? /var/log/fsck/checkfs and /var/log/fsck/checkroot just say "(Nothing has been logged yet.)"

Thanks,
treacl

---


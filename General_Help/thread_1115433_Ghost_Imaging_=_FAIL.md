---
title: "Ghost Imaging = FAIL"
date: 2009-04-03
forum: General Help
---

### Post by Ubie-Nubie on 2009-04-03
Using Ghost 11.5 "Disk-To Image" to backup and then later "Disk-From Image" to restore. After Ghost recovers the disk, I can boot the system and everything seems fine. Eventually, the "mount count" is exceeded causing an automatic fsck. If I allow the fsck to complete, it trashes the root filesystem so bad the system won't boot, forcing me to restore the disk from the backup again.

No errors from ghost during backup or restore.

fsck is the (-C) "===========" one that runs at boot time (checkroot.sh.) Seems ok until about 6?% then the screen fills with scrolling errors (and system fails to boot after that.)

More Info.
After remembering ctrl-S (to stop the scrolling of the fsck errors) I was able to determine what (at least some of) the errors are:

/dev/sdg1: Setting file type for entry '<file>' in /var/cache/<path> (<some number>) to <some number>.

I also noticed an error about a count being wrong on "inode 8" (fixed.) This happens early in the fsck process, and may be involved...

For now, I'll just use "tune2fs -c 0" to avoid the check, but that's not really a long-term solution ;)

Any help?

---

### Post by Ubie-Nubie on 2009-04-05
Anyone? Anyone? Bueller?
:)

Really? Has someone at least seen this behavior?

---


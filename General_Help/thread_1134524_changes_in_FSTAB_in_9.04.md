---
title: "changes in FSTAB in 9.04?"
date: 2009-04-23
forum: General Help
---

### Post by szarywilq on 2009-04-23
Hello,

I have just made a new installation of OS - I have formated 8.10 and installed 9.04.

Before that I have copied few lines from intrepid from FSTAB which mounted windows partitions at boot:
> # UUID=38A4C8F2A4C8B422	/media/Magazyn	ntfs-3g	defaults,dmask=000,fmask=111	0	0
# UUID=2EFE95AEFE956EB9	/media/Multimedia	ntfs-3g	defaults,dmask=000,fmask=111	0	0
# UUID=8E48F75048F73595	/media/WindowsXP	ntfs-3g	defaults,dmask=000,fmask=111	0	0

Now, in 9.04 they do not work - they do not mount at boot and I can't even mount them manually. ATM I removed them and I can mount partitions manually after system boots.

So what I need to change to make them working in 9.04??

---

### Post by miegiel on 2009-04-23
Posting /etc/fstab and the output of ```
sudo mount -a
``` could help :D

# in front of a line in fstab means it's a note and won't be "processed".

---

### Post by oldos2er on 2009-04-23
Run
```
sudo blkid
```
to see if the UUIDs have changed.

---

### Post by szarywilq on 2009-04-23
Thanks for help, problem is solved.

But it was not caused by UUID - it stayed the same.

I just had to install ntfs-3g:)

---


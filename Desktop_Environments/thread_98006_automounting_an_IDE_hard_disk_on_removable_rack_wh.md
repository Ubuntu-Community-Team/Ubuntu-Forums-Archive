---
title: "automounting an IDE hard disk on removable rack when present"
date: 2005-12-02
forum: Desktop Environments
---

### Post by megamania on 2005-12-02
I have a backup hard disk on an IDE removable rack.

If I put it in /etc/fstab, it mounts correctly when it is inserted, but when it is not the boot process stops on the "mount error" and I have to enter control+d for the boot to continue.

I can remove it from fstab and mount it manually of course, but is there a way to have the disk mounted only when it is present, or to have the error message automatically skipped?

I was thinking of having a small script run on login, but is that the best way to do it? And if that's the case, I don't need help with the script itself, but with the procedure to have it executed on login (is cronjob to be used?).

---


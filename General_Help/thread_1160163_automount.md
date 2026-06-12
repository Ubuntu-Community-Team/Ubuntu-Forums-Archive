---
title: "automount"
date: 2009-05-15
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-05-15
I recently add a mount line to my fstab "/dev/sdc9 /media/storage vfat iocharset=utf8,umask=000 0 0" All was well. Rebooted a few times and no problems,(wallpapers and music are on that drive) mounted just fine, till this morning, tried to manually mount and got "do not have the permissions" I then tried "sudo mount /dev/sdc9" error was "/media/storage does not exist" (was very confused) decided to remove that mount line from fstab. I was then able to manually mount the drive. I then rebooted again and somehow it was auto-mounted on boot up (no mount line in fstab for it) This seems very strange!

---


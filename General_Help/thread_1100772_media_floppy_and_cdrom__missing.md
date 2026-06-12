---
title: "/media floppy and cdrom  missing"
date: 2009-03-19
forum: General Help
---

### Post by rsteinmetz70112 on 2009-03-19
I have a problem with the /media directory for removable media. All of the mount points seem to have been deleted. It started when I connected a USB hard drive, It came up normally but after removing the hard drive there was an unremovable directory. Rebooting the system to force a fsck of the root drive seems to have fixed that directory but the ./cdrom ./floppy and the links to ./cdrom0 and ./floppy0 entries are now missing.

How can I restore them properly?

---

### Post by dcstar on 2009-03-19
> **rsteinmetz70112 said:**
> I have a problem with the /media directory for removable media. All of the mount points seem to have been deleted. It started when I connected a USB hard drive, It came up normally but after removing the hard drive there was an unremovable directory. Rebooting the system to force a fsck of the root drive seems to have fixed that directory but the ./cdrom ./floppy and the links to ./cdrom0 and ./floppy0 entries are now missing.

How can I restore them properly?

Try:

```

cd /media
sudo mkdir cdrom
sudo chown root cdrom
sudo chgrp root cdrom
sudo chmod 755 cdrom
sudo ln -s cdrom cdrom0
```

If that works do the same with the "floppy" name.

---


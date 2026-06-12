---
title: "Unable to unmount with nautilus script"
date: 2008-07-12
forum: Desktop Environments
---

### Post by ucal on 2008-07-12
I downloaded and used this script:

[http://mundogeek.net/nautilus-scripts/#nautilus-mount-image](http://mundogeek.net/nautilus-scripts/#nautilus-mount-image)

However, I am unable to unmount anything mounted with it.  I get this error:

umount: /media/example.iso is not in the fstab (and you are not root)

Is there a way to use SUDO to do this?  Or a way to fix the script so I can enable administrative privileges upon unmounting an iso?

---

### Post by youthforlinux on 2008-07-12
You could use the terminal and run the script as root or use gksudo.

---

### Post by ucal on 2008-07-12
The odd thing is that the script asked for the password to perform administrative tasks when I was mounting the volume, but it didn't when unmounting.  So I'll figure out what the script is called and use sudo with it for now, but I'd really like a fix that means I don't have to use the terminal.

---


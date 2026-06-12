---
title: "Will reinstall affect my dual boot?"
date: 2009-05-16
forum: General Help
---

### Post by zorocke on 2009-05-16
I run a dual boot with Windows XP and Ubuntu with the Grub boot loader. I'm planning on running a clean install of windows XP because it has become bogged down. Will this have any affect on my Ubuntu system or grub loader that I should take into consideration before the reinstall?

---

### Post by Locutus_of_Borg on 2009-05-16
yes

windows will overwrite grub

you just have to boot from a live cd, open a terminal, and issue the following commands to restore it
```

sudo -i
mount /dev/sda# /mnt (mount your linux root partition on /mnt)
grub-install --no-floppy --root-directory=/mnt /dev/sda
reboot

```

should fix it

---

### Post by Rocket2DMn on 2009-05-16
For more details, you can check out [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp].  There is a lot of information there and alternative options.

The upshot of the whole thing is that you have to reinstall grub into the bootloader.  It's not as complicated as it looks.

---

### Post by Locutus_of_Borg on 2009-05-16
> **Rocket2DMn said:**
> For more details, you can check out [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp].  There is a lot of information there and alternative options.

The upshot of the whole thing is that you have to reinstall grub into the bootloader.  It's not as complicated as it looks.
isnt that a lot of extra unnecessary steps?

---

### Post by Rocket2DMn on 2009-05-16
> **Locutus_of_Borg said:**
> isnt that a lot of extra unnecessary steps?

There are a lot of different methods for going about restoring grub.  I often support using the Super Grub Disk if the user wants to take the time for it, since less needs to be known about the system.  That page just outlines in more details what is being done during the grub reinstall, and how to check things.

---

### Post by Locutus_of_Borg on 2009-05-16
super grub disk complicates things in my opinion

but then again, who am i to talk using lilo to chainload grub.... :p

---


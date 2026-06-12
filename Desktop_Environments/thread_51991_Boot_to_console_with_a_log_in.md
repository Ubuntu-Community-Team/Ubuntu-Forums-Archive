---
title: "Boot to console with a log in"
date: 2005-07-26
forum: Desktop Environments
---

### Post by duncanm on 2005-07-26
Nightmare situation....

Finally got fglrx.ko to load and now the system boots to a blank screen.

so I think.. no biggy, I'll boot to a command line and fix it.

Boot into recovery mode and all I can do is try to log on as root...

and i don't have root setup... so I can't log in.

how can i get to a normal command line login so I can fix it?

---

### Post by nemin on 2005-07-26
[QUOTE=duncanm]Nightmare situation....

Finally got fglrx.ko to load and now the system boots to a blank screen.

so I think.. no biggy, I'll boot to a command line and fix it.

Boot into recovery mode and all I can do is try to log on as root...

and i don't have root setup... so I can't log in.

how can i get to a normal command line login so I can fix it?[/QUOTE]
I'm sure there must be a more "clean" way to do this, but booting with the live-cd, mounting the target filesystem, chroot-ing into it and fixing the problem is usually very effective :)

---

### Post by wvslkr on 2005-07-26
You should be able to just hit ctl,alt,f1 to drop to console. Alt,F7 brings you back to gui.
 GL :)

---

### Post by duncanm on 2005-07-26
Nope and nope.... :(

It appears it's crashing the machine since ctrl, alt, f1 does nothing.

Only got the install CD, not a live one.

Did try getting advanced mode up ( Busybox? ) and running but despite claiming to mount my hard drives at /target, there's no /target

Surely there's a command I can add to grub to get around this?

Edit:
LOL well seeing as I didn't have any other ideas I downloaded ext2fs for windows and mounted the drive.
Didn't like the idea of risking it but was desperate... so backed up my data and then deleted fglrx.ko and I'm back

Still would like an answer on what I can do though seeing as I may want to try and get 3d up and running again... and risking my partition table is scary

Edit ( Again ):
I'm a prat... sudo passwd root. At least now I have a root account sorted

---


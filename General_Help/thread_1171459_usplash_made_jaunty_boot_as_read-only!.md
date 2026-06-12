---
title: "usplash made jaunty boot as read-only!"
date: 2009-05-27
forum: General Help
---

### Post by googlegot on 2009-05-27
I was trying to change my boot screen, and I played around with splashy for a while.  Splashy wasnt as great as everyone touted it to be so I reinstalled usplash.

After I reinstalled usplash I went into startupmanager and changed the splash screen to a custom one, and rebooted to see if it worked.

Well, it didnt, and now my file system is mounted as read only, and I keep getting an error saying "24: Illegal Number blah blah blah"

I have booted into the live cd, fsck'd all my partitions, and checked /etc/fstab (no problems)

I then chrooted into my ubuntu partition and did the following:

Uninstalled usplash, cleared my package cache, reinstalled usplash

ran startupmanager and restored default settings, and restored the original boot splash

ran update-initramfs -u (redundant, I know)

reinstalled grub


I have run out of ideas, and the error still continues to happen, does anyone have any ideas?

---

### Post by Legace on 2009-05-27
Post /boot/grub/menu.lst here

---

### Post by Bender2k14 on 2009-05-27
You do not need a splash screen at all, right?  Try uninstalling all splash screens and see what happens.

---

### Post by Legace on 2009-05-27
> **Bender2k14 said:**
> You do not need a splash screen at all, right?  Try uninstalling all splash screens and see what happens.

Yeah, but then you should remove **quiet** and **splash** from menu.lst

---

### Post by googlegot on 2009-05-27
I have tried uninstalling all splash screens and booting without the splash and quiet boot options as well, all without effect.

---

### Post by Bender2k14 on 2009-05-27
The end of my /boot/grub/menu.lst file looks like this:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b78d1e14-5100-40a6-9f82-ae169a9ad0f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b78d1e14-5100-40a6-9f82-ae169a9ad0f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b78d1e14-5100-40a6-9f82-ae169a9ad0f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b78d1e14-5100-40a6-9f82-ae169a9ad0f2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b78d1e14-5100-40a6-9f82-ae169a9ad0f2
kernel		/boot/memtest86+.bin
quiet

```

I have uuid lines and don't have root lines for each entry.  Would that make a difference?

---

### Post by Legace on 2009-05-27
Type this into Terminal (note, it will reboot pc. If it fails to reboot, boot it manually):

```
shutdown -Fr now
```

---

### Post by googlegot on 2009-05-27
> **Bender2k14 said:**
> The end of my /boot/grub/menu.lst file looks like this:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b78d1e14-5100-40a6-9f82-ae169a9ad0f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b78d1e14-5100-40a6-9f82-ae169a9ad0f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b78d1e14-5100-40a6-9f82-ae169a9ad0f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b78d1e14-5100-40a6-9f82-ae169a9ad0f2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b78d1e14-5100-40a6-9f82-ae169a9ad0f2
kernel		/boot/memtest86+.bin
quiet

```

I have uuid lines for each entry.  Would that make a difference?

good point, trying now with the uuid from my fstab

---

### Post by Bender2k14 on 2009-05-27
> **Legace said:**
> 
```
shutdown -Fr now
```

I do not see the capital F option in the man pages for shutdown.  Does it really exist?  What does it do?

---

### Post by Legace on 2009-05-27
> **Bender2k14 said:**
> I do not see the capital F option in the man pages for shutdown.  Does it really exist?  What does it do?

fschk for / on boot.

---

### Post by philinux on 2009-05-27
> **googlegot said:**
> good point, trying now with the uuid from my fstab

You should have a backup of menu.lst you could use if fstab entries are wrong. Try using blkid to check in a terminal.

---

### Post by googlegot on 2009-05-27
I have made a few backups of my menu.lst previously, and looking through them, none have the uuid listed, and all of them booted perfectly.

Oh, and putting the uuid string in there did not work at all

---

### Post by Bender2k14 on 2009-05-27
> **googlegot said:**
> I have made a few backups of my menu.lst previously, and looking through them, none have the uuid listed, and all of them booted perfectly.

Oh, and putting the uuid string in there did not work at all

I edited my previous post about the uuids to also say that each of your entries includes a line beginning with root but mine do not.  Do your "good copies" of the menu.lst also include those lines?

---

### Post by googlegot on 2009-05-27
> **Bender2k14 said:**
> I edited my previous post about the uuids to also say that each of your entries includes a line beginning with root but mine do not.  Do your "good copies" of the menu.lst also include those lines?

my previous backups are exactly the same, and none of them work, which makes me think the problem is not with grub but somewhere else.

my fstab had not been touched before today, could it be my kernel image?

---

### Post by googlegot on 2009-05-27
> **Legace said:**
> Type this into Terminal (note, it will reboot pc. If it fails to reboot, boot it manually):

```
shutdown -Fr now
```

ran it, but it did basically nothing, just like my other fscks

---


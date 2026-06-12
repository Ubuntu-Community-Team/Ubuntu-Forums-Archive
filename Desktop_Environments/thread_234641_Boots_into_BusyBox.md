---
title: "Boots into BusyBox"
date: 2006-08-11
forum: Desktop Environments
---

### Post by jwcmonkey on 2006-08-11
When I boot Ubuntu it boots into BusyBox and says:

/bin/sh: can't access tty: job control turned off

I noticed before it Uncompresses the Linux kernel it says root=/dev/hda3. Linux is on hda1, how can I change this back, and is this the problem?

Thanks

---

### Post by mlind on 2006-08-11
> **jwcmonkey said:**
> When I boot Ubuntu it boots into BusyBox and says:

/bin/sh: can't access tty: job control turned off

I noticed before it Uncompresses the Linux kernel it says root=/dev/hda3. Linux is on hda1, how can I change this back, and is this the problem?

Thanks

GRUB (bootloader) is probably booting from wrong partition. Boot process fallbacks to busybox when root partition is not found. Try editing GRUB menu before system boots to Ubuntu by hitting ESC -key and replace /dev/hda3 with /dev/hda1 on kernel line. You may need to correct root to (0,2)

Then you should edit /boot/grub/menu.lst and correct **groot** and **kopt** settings to point right partition(s). groot value is probably (0,2). After editing, save the file and execute *sudo update-grub*.

---

### Post by jwcmonkey on 2006-08-11
I edited GRUB to /dev/hda1 and verified root was (0,2) and I am still getting the same thing. That is where I have Ubuntu installed so I don't know what is going on.

---

### Post by mlind on 2006-08-11
> **jwcmonkey said:**
> I edited GRUB to /dev/hda1 and verified root was (0,2) and I am still getting the same thing. That is where I have Ubuntu installed so I don't know what is going on.

Do you mean you edited while on GRUB boot menu?
Did you find out what kernel(s) you have installed using grub interactive shell?

If you're not familiar with grub shell, it's probably easiest to recover this by using Ubuntu install cd.

---

### Post by jwcmonkey on 2006-08-11
> **mlind said:**
> Do you mean you edited while on GRUB boot menu?
Did you find out what kernel(s) you have installed using grub interactive shell?

If you're not familiar with grub shell, it's probably easiest to recover this by using Ubuntu install cd.

Yes, thats what I meant, I edited while on the GRUB boot menu. 

The current kernels I have are 2.6.15-25-386, 2.6.15-23-386, 2.6.12-10-386, 2.6.12-9-386. 

How do I and what does the ubuntu install cd recover?

---

### Post by mlind on 2006-08-12
> **jwcmonkey said:**
> Yes, thats what I meant, I edited while on the GRUB boot menu. 

The current kernels I have are 2.6.15-25-386, 2.6.15-23-386, 2.6.12-10-386, 2.6.12-9-386. 

How do I and what does the ubuntu install cd recover?

Okay, try booting using the interactive shell (is is 'c' to enter the shell on grub menu?)

You can use TAB to autocomplete root device, kernel and initrd image.
```

root (hd0,2)
kernel /vmlinuz-2.6.15-25-386 root=/dev/hda3 ro nosplash
initrd /initrd.img-2.6.15-25-386

```
After you've typed root *(hd0,* press TAB to see what partitions are available and choose one that's a Linux partition. Make sure you use same partition on root=/dev/xxx



If you want to recover using ubuntu install cd, boot into livecd environment and open a terminal
```

sudo mount /dev/hda3 /mnt
sudo chroot /mnt /bin/bash
*(edit /boot/grub/menu.lst on chroot environment)*
update-grub
*(then boot)*

```
If root (/) partition is not /dev/hda3, use **sudo fdisk -l** to list all available partitions.

---

### Post by jwcmonkey on 2006-08-12
> **mlind said:**
> Okay, try booting using the interactive shell (is is 'c' to enter the shell on grub menu?)

You can use TAB to autocomplete root device, kernel and initrd image.
```

root (hd0,2)
kernel /vmlinuz-2.6.15-25-386 root=/dev/hda3 ro nosplash
initrd /initrd.img-2.6.15-25-386

```
After you've typed root *(hd0,* press TAB to see what partitions are available and choose one that's a Linux partition. Make sure you use same partition on root=/dev/xxx



If you want to recover using ubuntu install cd, boot into livecd environment and open a terminal
```

sudo mount /dev/hda3 /mnt
sudo chroot /mnt /bin/bash
*(edit /boot/grub/menu.lst on chroot environment)*
update-grub
*(then boot)*

```
If root (/) partition is not /dev/hda3, use **sudo fdisk -l** to list all available partitions.

I went the live cd route. hda3 was where ubuntu was installed. I opened up /boot/grub/menu.lst and everything was correct. I saved that and rebooted and ubuntu booted for me! I don't know what fixed it but all is well now.

Thanks

---


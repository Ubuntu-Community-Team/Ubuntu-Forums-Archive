---
title: "Can I change a USB sector size? Need an 'expert' with fdisk"
date: 2009-01-20
forum: General Help
---

### Post by kesre on 2009-01-20
Hey,
I recently resurrected an ipod that had been in the wash, and I want to use it as a persistent Ubuntu live usb. I went through the process, and got stuck at the last step,
```
sudo syslinux -f /dev/sdb1 
```

my problem is sector size
according to fdisk -l, it is 4096 and syslinux can only handle 512...


I assume that this is because it is an apple product...

still, can I change the sector size? (or make the computer think it has a smaller sector size?)

```

sudo fdisk /dev/sdb
x
```

looked promising to me. but I don't trust myself with changing sectors per track, number of cylinders, number of heads, and so on...

Help?

---

### Post by caljohnsmith on 2009-01-20
With fdisk you can change the number of bytes/sector for how fdisk reads the drive, but that doesn't actually change the bytes/sector of the drive as far as I know; I know that the bytes/sector number is not stored anywhere in the MBR (Master Boot Record), so I would assume that fdisk, syslinux, and other commands get that information from the device itself. In other words, I don't think you can change it. As a workaround though, you might try:
```
sudo syslinux -sf /dev/sdb1
```
In the syslinux man page, it talks about using the "s" option when installing to a CD-ROM, which also uses 2048 bytes/sector. So you might give that a try and see if it works, and let me know how that goes.

---

### Post by dcstar on 2009-01-20
> **kesre said:**
> 
........
still, can I change the sector size? (or make the computer think it has a smaller sector size?)
........

Only by reformatting.

---

### Post by kesre on 2009-01-20
Ok,
I have already tried the -sf option, and got the same message.

dcstar, could you give an example / step process for the code to set the sector size? - I don't mind reformatting

---

### Post by dcstar on 2009-01-20
> **kesre said:**
> 
........
dcstar, could you give an example / step process for the code to set the sector size? - I don't mind reformatting

Just use the partition editor and whatever options it gives you for the particular filetype you select.

---


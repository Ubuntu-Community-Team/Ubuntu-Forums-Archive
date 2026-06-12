---
title: "dapper doesn't detect second hd"
date: 2006-08-20
forum: Desktop Environments
---

### Post by mcbain on 2006-08-20
Hi,

I got a problem with my second hd, called hdc. Dapper doesn't seem to detect it. With Debian its no problem. I run the server version of Dapper Drake with xubuntu.

```
sudo mount -t vfat /dev/hdc /mnt/
mount: /dev/hdc already mounted or /mnt/ busy
```

"Mount" shows no hdc. 

```
sudo cfdisk /dev/hdc
hdc1                    Primary   W95 FAT32 (LBA)                  30968,18
hdc2                    Primary   W95 FAT32 (LBA)                  30959,96
hdc3                    Primary   W95 FAT32 (LBA)                  30968,18
hdc5                    Logical   W95 FAT32 (LBA)                  30038,73
```

Any idea?

Thanks
McBain

---

### Post by mcbain on 2006-08-20
Wow,

that was fast, I remembered suddenly I had the exact same problem before. Solution is to turn off DMA by giving ```
ide=nodma
``` as a boot parameter in ```
/boot/grub/menu.lst
```

Stupid me :rolleyes: 

Now I have only to solve my burning problem, then everything will run fine.

cu
mcbain

---


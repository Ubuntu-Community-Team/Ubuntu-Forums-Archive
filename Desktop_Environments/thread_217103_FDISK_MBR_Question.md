---
title: "FDISK /MBR Question"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Moyerman on 2006-07-16
Hello, I seem to have MBR issues. After searching posts and reading "Help Please! Ubuntu install messed up computer and now I can't install Windows. Help" Thread I'm pretty sure I need to use FDISK with the /MBR switch. My question is- has any one done this? According to Microsoft there can be issues when multi-boot machines are involved. GRUB is a boot mananger (right?)so I am 
kinda worried.

---

### Post by Jagot on 2006-07-16
GRUB is a boot manager.

To get rid of GRUB and restore your MBR, boot with your Windows disk and get to the recovery console.  At the prompt type:

```
fixmbr
```

Alternatively, if you don't have your Windows disk to hand you can also use a FreeDOS boot disk from here:

[http://www.freedos.org/](http://www.freedos.org/)

The command is slightly different though:

```
fdisk /mbr
```

I have used both of these methods and they work fine.

---

### Post by patrickfromspain on 2006-07-16
If you're installing windows, it shouldn't be necessary. I have windows on SDA1, FAT32 on SDA5, swap on SDA6 and ubuntu on SDA7. Everytime I have re-installed windows, it has taken over my MBR and I had to reinstall grub. There's nothing wrong with grub, but perhaps with your hardware or windows cd.

---


---
title: "Sound on a Compaq"
date: 2005-05-17
forum: Desktop Environments
---

### Post by GNULinuxGeek on 2005-05-17
Anyone know of the tool or app to use to get a ESS-1889 sound chip to work under Hoary 5.04?  Compaq tends to take these chips, put them on their motherboard, and proceed to booger up the I/O addresses or the default interrupt used.

Found this on many other distros too.  Loving Ubuntu with KDE added.  Have it on all but one computer at home.

Thanks

GNULinuxGeek

---

### Post by stepore on 2005-05-17
[QUOTE=GNULinuxGeek]Anyone know of the tool or app to use to get a ESS-1889 sound chip to work under Hoary 5.04?  Compaq tends to take these chips, put them on their motherboard, and proceed to booger up the I/O addresses or the default interrupt used.

Found this on many other distros too.  Loving Ubuntu with KDE added.  Have it on all but one computer at home.

Thanks

GNULinuxGeek[/QUOTE]
 try adding this to your /etc/modules.

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0
snd-es18xx

worked for mine. YMMV.

---


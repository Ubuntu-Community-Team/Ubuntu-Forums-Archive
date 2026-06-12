---
title: "DMA for ide drives"
date: 2006-03-05
forum: Desktop Environments
---

### Post by hise0001 on 2006-03-05
I was looking for howto's on speeding up cd ripping and encoding.  It seemed all I could find was to enable SCSI emulation for the IDE drive.   Well, that didn't work for me at all.

I later found turning on DMA for the CD-ROM drive to be the ticket.  I guess I had assumed that DMA was already turned on, as I could find no property setting on the drives to affect this.

Anyway I found the command is....

hdparm -d1 <devicename> (in my case... /dev/hdc)

My question now is, how to I get this to happen at startup (and don't want to have to enter a sudo password).

Thanks for your help.

--Hise

---

### Post by noigeaR on 2006-03-05
open /etc/hdparm.conf with administrator privileges with your favorite editor
(for example sudo nano /etc/hdparm.conf)

add the following to the end of hdparm.conf

/dev/hdc {
dma = on
}

save the file, reboot, done
check with hdparm -d /dev/hdc if dma mode is enabled after rebooting

---

### Post by John.Michael.Kane on 2006-03-05
[http://www.die.net/doc/linux/man/man8/hdparm.8.html](http://www.die.net/doc/linux/man/man8/hdparm.8.html)
use this as a guide adding what comands you need to start on boot... remove these #<--- when finshed
Edit or use the command listed by the above poster.

---

### Post by Ramses de Norre on 2006-03-05
Should all my hard disks have dma enabled too? Because one has but the other hasn't it enabled I guess.
This is what I get: ```
ramses@icarus:~$ sudo hdparm -d /dev/sda

/dev/sda:

```
The others say dma is enabled.

---

### Post by Parkotron on 2006-03-09
[QUOTE=Ramses de Norre]Should all my hard disks have dma enabled too?```
ramses@icarus:~$ sudo hdparm -d /dev/sda
```[/QUOTE]
I don't think hdparm applies for SATA/SCSI drives, but I could be wrong. Someone with more information feel free to expand/correct.

---

### Post by RAOF on 2006-03-10
hdparm won't work correctly for SATA drives, at least.  And you don't need to enable DMA on SATA drives, anyway.  Hdparm is very much tied to IDE/PATA drives.

---


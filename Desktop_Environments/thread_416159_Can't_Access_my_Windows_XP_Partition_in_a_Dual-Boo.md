---
title: "Can't Access my Windows XP Partition in a Dual-Boot"
date: 2007-04-20
forum: Desktop Environments
---

### Post by thegoodsteer on 2007-04-20
Hi. I installed the new feisty 7.04 yesterday, and did a clean install over my old Ubuntu Partition that was a bit messed up (X server would crash alot, PCI-E Slot would not be picked up most of the time). 
When doing this, I just chose my ubuntu partition, and clicked "format" and set it as "/".

So now, feisty works, but in Grub, my Windows XP partition does not show up. 
I have a recovery partition for XP (D:\), and that shows up in Grub. My XP Partition (C:\) shows up in my disks in Ubuntu, but I can't boot?

I wasn't sure what to do, so I tried loading up the live disc, going into gnome partition editor and selecting my ntsf partition as "/". I am not sure if it really saved or not, but when I re-booted, the problem didn't go away.

---

### Post by krolls on 2007-04-21
Hi

This link may help you..:biggrin: 

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html)

---

### Post by thegoodsteer on 2007-04-22
> **krolls said:**
> Hi

This link may help you..:biggrin: 

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/partitions-booting.html)

I'm not using 6.10, i'm using 7.04

---

### Post by Landser on 2007-04-22
> **thegoodsteer said:**
> Hi. I installed the new feisty 7.04 yesterday, and did a clean install over my old Ubuntu Partition that was a bit messed up (X server would crash alot, PCI-E Slot would not be picked up most of the time). 
When doing this, I just chose my ubuntu partition, and clicked "format" and set it as "/".

So now, feisty works, but in Grub, my Windows XP partition does not show up. 
I have a recovery partition for XP (D:\), and that shows up in Grub. My XP Partition (C:\) shows up in my disks in Ubuntu, but I can't boot?

I wasn't sure what to do, so I tried loading up the live disc, going into gnome partition editor and selecting my ntsf partition as "/". I am not sure if it really saved or not, but when I re-booted, the problem didn't go away.

Ok listen, first of all - you need to figure out what's your XP partition (/dev/hda#)

Then add this to the end of your /boot/grub/menu.lst:

```
title		Microsoft Windows XP
root		(hd0,#)     [COLOR="Red"]<------- Replace # with your Windows partition number[/COLOR]
savedefault
makeactive
chainloader	+1
```

---


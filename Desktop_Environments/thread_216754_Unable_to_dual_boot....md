---
title: "Unable to dual boot..."
date: 2006-07-16
forum: Desktop Environments
---

### Post by Miki01 on 2006-07-16
Well I've just installed Windows XP Pro to a partition in my hard drive, then, problems start appearing, like being unable to connect to the internet and sound not working properly in games... (lousy microsoft). So I've fixed GRUB so that I can boot into dapper again. The problem is, that I can't boot into XP anymore. When I reboot my PC, it just automatically goes to GRUB, then the dapper bootscreen... Does anyone have a fix on this?

btw, I'm using an amd64 system if that info is needed. Please help. I don't want $177.99 on that XP install CD to go to waste...

Thanks in advance for your replies.

---

### Post by [S|G] on 2006-07-16
Do this:
```

sudo gedit /boot/grub/menu.lst

```

At the end of the file paste the following lines:
```

title           Microsoft Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

If your windows is not installed on the first partition of your hard drive (/dev/hda1) then change the line that reads "root (hd0,0)". Here is a quick table for you to understand what to put on it:
```

Place                                                     Linux Name          Grub Name
1st partition on primary master disk       /dev/hda1           (hd0,0)
2nd partition on primary master disk       /dev/hda2           (hd0,1)
1st partition on primary slave disk        /dev/hdb1           (hd1,0)
2nd partition on primary slave disk        /dev/hdb2           (hd1,1)
1st partition on secondary master disk     /dev/hdc1           (hd2,0)
2nd partition on secondary master disk     /dev/hdc2           (hd2,1)
1st partition on secondary slave disk      /dev/hdd1           (hd3,0)
2nd partition on secondary slave disk      /dev/hdd2           (hd3,1)

```

---

### Post by Miki01 on 2006-07-16
Okay, I pasted this:

> title           Microsoft Windows XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Being that XP is in the second partition and dapper being on the first. When I save the text editor and reboot the PC it boots from dapper still. After my PC POST's it goes straight to GRUB.

---

### Post by [S|G] on 2006-07-16
So you want to set boot into XP as the default option? If so, there is a line like this:
```
#default                0
```
Uncomment it (remove the #) and set the number that you want to boot. 0 is the first OS in the list, 1 is second and so on. You'll need to see how many OSes are in the list to determine your Windows's number.

If it is confusing, paste your menu.lst here so we can take a look and help with that.

---


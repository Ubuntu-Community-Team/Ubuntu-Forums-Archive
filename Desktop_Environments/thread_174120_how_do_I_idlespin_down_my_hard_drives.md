---
title: "how do I idle/spin down my hard drives"
date: 2006-05-11
forum: Desktop Environments
---

### Post by pillypoon on 2006-05-11
Hello All,

I noticed my hard drives dont idle down after a lond period of non activity.. I searched and searched but cannot find a way to do so.  Is there a way to do so or is it not implemented yet.  :confused: 

Thanks in advance,
Pilly

---

### Post by cyracks on 2006-05-11
To check in which power mode is you disk use

```

sudo hdparm -C /dev/hda

```

To force disk to go in standby mode after 10min
```

sudo hdparm -S 120 /dev/hda

```

for futher information see
```
man hdparm
```

---

### Post by newbieforever on 2008-03-17
thank you very much, that was exactly what i was searching for...
hard disk or hdd drive idle or sleep is very important to me... 
i often leave the calculator wihous using it for a couple of hours (my wife is guilty for that! :-)

everyone should know that, and im surpriseed that
- the default parameters dont set that to some default value
- gnome seems (im not sure, obviously) not to offer that option in the power management panel..

but i have a question: i use the same ubuntu configuration on 2 calculators
in the first no problem
in the second i use ubuntu from an external usb hdd: when i try the command "sudo hdparm -S 120 /dev/hda" i get the following "beep"

sudo hdparm -S 120 /dev/sda
/dev/sda:
 setting standby to 120 (10 minutes)
 HDIO_DRIVE_CMD(setidle1) failed: Invalid argument

could you help about that?
i would be graceful to you if you could

thanks again anyway...

newbie forever

---

### Post by st1100pilot on 2008-03-30
Glad to find this thread. When I use the following command: sudo hdparm -S 120 /media/EXT-HDD2, I get the message that /media/EXT_HDD2 is a directory. Should I use a -R somewhere in the command?

---

### Post by sillygit on 2008-03-30
> **st1100pilot said:**
> Glad to find this thread. When I use the following command: sudo hdparm -S 120 /media/EXT-HDD2, I get the message that /media/EXT_HDD2 is a directory. Should I use a -R somewhere in the command?

hdparm expects the specified device to be a physical disk and not a mount point (directory)...

To find out which physical disk the "/media/EXT_HDD2" directory points to, use:
> mount | grep /media/EXT_HDD2

When you issue the above command you'll see something like (important part is bolded):
> **/dev/hdb**1 on /media/EXT_HDD2 type ext3

So using the above example, you'll need to issue:
> hdparm -S 120 **/dev/hdb**

It's worth noting that when you restart your computer you'll have to re-issue the command.

Hope that helps...

---

### Post by Tu13erhead on 2008-04-03
> **newbieforever said:**
> when i try the command "sudo hdparm -S 120 /dev/hda" i get the following "beep"

sudo hdparm -S 120 /dev/sda
/dev/sda:
 setting standby to 120 (10 minutes)
 HDIO_DRIVE_CMD(setidle1) failed: Invalid argument


I get the same when trying this on either of my external drives.  Also, trying to enable or disable DMA seems to have no result.

Any ideas?

---

### Post by Tu13erhead on 2008-04-03
> **Tu13erhead said:**
> I get the same when trying this on either of my external drives.  Also, trying to enable or disable DMA seems to have no result.

Any ideas?

So it seems this will not work because the drives are sdx instead of hdx.

Gr..

---

### Post by antechinus on 2008-06-26
Use 
```
df -h
```

first to find out what drive you want to spin down. Then use hdparm as shown above.

---

### Post by antechinus on 2008-06-26
This does not work for my machine:

```
sudo hdparm -S 120 /dev/sda1
```

I get the following reply:
```
/dev/sda1:
 setting standby to 120 (10 minutes)
```

But the hard drive is still whirrring away after 10 minutes and beyond.

What could the possible problems be, so I may diagnose?

---

### Post by sillygit on 2008-06-27
> **antechinus said:**
> This does not work for my machine:

```
sudo hdparm -S 120 /dev/sda1
```

I get the following reply:
```
/dev/sda1:
 setting standby to 120 (10 minutes)
```

But the hard drive is still whirrring away after 10 minutes and beyond.

What could the possible problems be, so I may diagnose?

/dev/sda**1** implies a partition on the disk, you could maybe try /dev/sda instead... 

Also, if it's the only drive in your system there may be other processes writing to it (e.g. logging messages).  So that another thing to check for...

---


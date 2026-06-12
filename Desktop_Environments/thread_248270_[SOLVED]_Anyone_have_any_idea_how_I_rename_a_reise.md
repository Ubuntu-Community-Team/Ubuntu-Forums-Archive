---
title: "[SOLVED] Anyone have any idea how I rename a reiser partition?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by mtn on 2006-08-31
Anyone have any idea how I rename a reiser partition?

Basically I have a few partitions, some FAT, EXT3 and Reiser (not how I would have planned it but stuck with it for the moment). After a new install of Dapper they were all showing up on my desktop as hda2, hda3, hdb1 etc etc. I want nice names like Store and Media etc. I have managed to change the name of the FAT and EXT3 partitions (see below) but cannot figure out how to change the Reiser partitions. I have had a good search round but with no joy. Any suggestion would be great.


**Rename EXT3 Partition**
From: [URL="http://www.ubuntuforums.org/showthread.php?t=155676&highlight=mlabel"]http://www.ubuntuforums.org/showthread.php?t=155676&highlight=mlabel
[/URL]
To rename the EXT3 partitions this worked, replacing “newname for the name I wanted for the partition /dev/hda6 etc.

```
tune2fs -L newname /dev/hda6
```


**Rename FAT Partitions**
From: [http://ubuntuforums.org/showthread.php?t=65830]("http://ubuntuforums.org/showthread.php?t=65830")

1) Install mtools:
```
sudo apt-get install mtools
```

2) After the usb mount is automounted after plugging in, find out the device
descriptor using:
```
mount
```
and Note down where it says "sda1" or similar

3) copy the mtools.conf to ~/.mtoolsrc
```
cp /etc/mtools.conf ~/.mtoolsrc
```

4) Edit ~/.mtoolsrc to add one line at the very end:
```
drive i: file="/dev/sda2"
```
--you may have to change sda2 to something else depending on what you got in
step 2 above.

5) Change to the "drive" i:
```
mcd i:
```

6) Check what the label for the drive is currently:
```
sudo mlabel -s i:
```

7) Change the label to something pretty:
```
sudo mlabel i:magnus
```
Yes, I named my ipod after the gallant man who showed me the way!

Check if the label has changed:
```
sudo mlabel -s i:
```
I got the following output --
**Volume label is MAGNUS**

---

### Post by mtn on 2006-09-08
I came across this program, **reiserfstune,** that sounded like it should do the job. So I tried a few things like below but had no joy. Any idea if this would do it? and if so how?

```
sudo reiserfstune -l /media/hda7 Store105mb
```

---

### Post by zbrox on 2006-11-03
> **mtn said:**
> 
```
sudo reiserfstune -l /media/hda7 Store105mb
```

The problem is that you're trying to use the mountpoint to address the partition. You should use the device node. For example /dev/sda1 or whatever the device node is.
Also to use this command you should unmount the usb device, otherwise the command won't be executed.

Hope that helps.
Cheers!

---

### Post by mtn on 2006-11-13
hey, thanks for that, you were right. I had the name and dev the wrong way round as well, so should be...

```
sudo reiserfstune -l Store105m /dev/hda7
```

where Store105m is the label for the partition. It is a partition on the hard disk! I have little partitions in a couple of places left over from when I didn't have a clue what I was doing (still don't) and was dual booting. those days only last a few weeks but too much stuff on the disk to sort it all out now. that is really why I want to have nice labels a I'm not the sparkliest tool in the sack and was getting confused with them all. I have since decided just to unmount the tiny partition and be done with them.

anyway, thanks. his has taken me a while to get back to but has brightened an other wise dull monday.

cheers

---


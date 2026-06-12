---
title: "Dual booting Ubuntu 8.10 and XP on eeepc..."
date: 2009-04-15
forum: General Help
---

### Post by Epidemic_HardyBoy on 2009-04-15
Using Adam's stuff...

I have a 64gb partition open for it and I want to dual boot with windows, but it is saying that it cannot install on the 64g partition because

"No root file system is defined.

Please correct this from the partitioning menu."

The menu looks like this

Edit a Partition
New partition size in megabytes 65711 (64g)
use as "Do not use the partition." (I tried changing it to ntfs.. No dice)
Format the partition "Unchecked Box" (I can't check either way.)
Mount Point "None" (/dos and /windows are the choices)

I am booting the live install off of a 1gb SD card using unetbootin

HELPPPP

ALSO: MOVE THIS IF IT IS IN THE WRONG AREA

---

### Post by mikewhatever on 2009-04-15
The problem is in the mount point section. Selecting **[SIZE="3"]/[/SIZE]** from the drop down menu will define that partition to be a root one.

---

### Post by Epidemic_HardyBoy on 2009-04-15
seriously? OH GOD. Ill go retry

---

### Post by Epidemic_HardyBoy on 2009-04-15
Great, now I can't boot from the SD card

"Cannot load DOS, press any key to retry"

---

### Post by Epidemic_HardyBoy on 2009-04-15
do i use ext2 or ntfs?

---

### Post by mikewhatever on 2009-04-15
I was under the impression that once you set the mount point to /, the file system and format the partition box are autoset. If that's not the case, ext3/ext2 is the way to go. NTFS is not good because it is a Windows only file system.

---

### Post by Epidemic_HardyBoy on 2009-04-15
ok, now if i am installing, i need a swap right?
should I pull like 2g-4g for it?

---

### Post by mikewhatever on 2009-04-16
That's way too much. The most amount you'll ever need is about 1GB.

---


---
title: "Grub Error and cannot boot, please help"
date: 2006-09-26
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-09-26
My hard drive got 134 bad sectors and now when i boot the grub halts while booting and shows error number 17. I looked on the internet around and many ppl have given different suggestions. I know for sure that my hard drive has bad sectors because i removed it and tried to make it usb2 drive using the setup i have. but tht also wont detect the partitions. My main task at this time is to take the bak up.

How can i get into the system and take backup. right i am downloading knoppix  live CD to get into it although results are still awaited.

every help is appreciated.

PS: i have dual boot with win xp and ubuntu dapper.

---

### Post by krypto_wizard on 2006-09-26
Can anybody even help me to get to widows and take some back up. I am stuck up at grub.

I am thking of possible alernatives.

1. Knoppix detects my win partition but wont let me write the win partition data on my external HDD. i dont know why ?

2. I could reinstall grub ...but i am 200% sure that my linux ext3 parition is screwed.

3. I could reinstall win or write on MBR win address. Can somebody help me for this one.

Thanks

Every help is appreciated.

---

### Post by rogier.de.groot on 2006-09-26
Hmm... for the Win partition recovery, what filesystem is on the disk? Knoppix can't write NTFS, so use FAT32 instead. If that's not the problem, try running nautilus as root (when recovering data over the network at work with a Ubuntu liveCD I alway open a console, do "sudo nautilus &" twice, and use the two windows to copy things - using a single sudo'ed nautilus window doesn't work as it won't copy to a regular nautilus window, because it's another user).

EDIT: Or you could boot a windows install cd into recovery console mode and do "fixboot c:" & "fixmbr" with should restore the windows boot loader.

---

### Post by krypto_wizard on 2006-09-26
Thanks, Knoppix helped me to get the data out of windows partition to my external hdd which was fat32.

>.EDIT: Or you could boot a windows install cd into recovery console mode and >do "fixboot c:" & "fixmbr" with should restore the windows boot >loader.[/QUOTE]

When do we get this console. Is it after putting in the install CD you get console. Please confirm..I will do this option.

thanks

---

### Post by krypto_wizard on 2006-09-26
Thanks it worked for me.

> **rogier.de.groot said:**
> Hmm... for the Win partition recovery, what filesystem is on the disk? Knoppix can't write NTFS, so use FAT32 instead. If that's not the problem, try running nautilus as root (when recovering data over the network at work with a Ubuntu liveCD I alway open a console, do "sudo nautilus &" twice, and use the two windows to copy things - using a single sudo'ed nautilus window doesn't work as it won't copy to a regular nautilus window, because it's another user).

EDIT: Or you could boot a windows install cd into recovery console mode and do "fixboot c:" & "fixmbr" with should restore the windows boot loader.

---


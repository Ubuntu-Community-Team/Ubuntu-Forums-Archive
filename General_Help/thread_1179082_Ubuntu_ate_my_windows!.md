---
title: "Ubuntu ate my windows!"
date: 2009-06-05
forum: General Help
---

### Post by theProdiKalson on 2009-06-05
So I installed windows on this computer with the intention of installing ubuntu and figuring out how to work my way around linux.  When I installed windows I partitioned my drive in to 3 partitions, but later learned when installing uBuntu that all partitions are not created equal.  The C: drive was the "system" drive or a primary partition and the other two were Extentions i believe.  I am uber new at all this.  Anyway this is the first time i am posting to any forum for help i usually just read others, but I am so lost at this point.

I can only boot into ubuntu and when I do I see the file system where windows is located, but have had no luck trying to add it to the GRUB bootloader.  I was messing with some menu.lst file, but cant seen to add a menu item that maps correctly to my windows install.
Any help would be TRULY appriciated!.

---

### Post by s.fox on 2009-06-05
Hi and welcome to the forums,

Can you post more information on the locations of the partitions?

You will need to add something like the following,  but will probably need to be changed.   
```

title Windows XP 
root (hd0,0)
savedefault
makeactive
chainloader +1
```Can you also tell us the version of windows.

-Ash R

---

### Post by rcayea on 2009-06-05
Did you repartiton during the Ubuntu install? What were the file systems for your three partitions?

---

### Post by Legace on 2009-06-05
Post output of (in Applications -> Accessories -> Terminal)

```
sudo fdisk -l
```

---

### Post by theProdiKalson on 2009-06-05
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2   *          18         990     7815622+  83  Linux
/dev/sda3             991        9729    70196017+   f  W95 Ext'd (LBA)
/dev/sda5            1293        3842    20482843+   7  HPFS/NTFS
/dev/sda6            3843        9729    47287296    7  HPFS/NTFS
/dev/sda7             991        1292     2425752   82  Linux swap / Solaris

Partition table entries are not in disk order

im the type of guy that puts a bed set together without reading the instrustions...

/dev/sda6 is the partition with my windows install
sda5 is a partition for all my media

im guessing 5 thru 7 are extended and not primary partitions right?

---

### Post by theProdiKalson on 2009-06-05
i added that thiney to the menu.lst file and saved it but i tried clicking on it when i booted and it gave me an error... 

i tried changing it around and got frustrated after reading other posts in forums that didnt apply to me and finally joined my first forum...

---

### Post by theProdiKalson on 2009-06-05
im not sure the file systems for the ubuntu install i know i deleted the primary partition i believe (the C drive)... it was empty.. i then made two partitions out of it one for swap area...no idea what the hell a swap it and another with ext i think... really unsure with the linux stuff i just guessed...did i do it right.. why is linux so demanding of my hdd and needing a swap area?

---

### Post by Bearly Able on 2009-06-05
In reply to post 6: Thread tools (at the top right-hand side) and Subscribe to this thread.

---

### Post by theProdiKalson on 2009-06-05
> **Lesley Lutomski said:**
> In reply to post 6: Thread tools (at the top right-hand side) and Subscribe to this thread.
kool sorry for asking simple questions lol

---

### Post by theProdiKalson on 2009-06-05
> **Ash R said:**
> Hi and welcome to the forums,

Can you post more information on the locations of the partitions?

You will need to add something like the following,  but will probably need to be changed.   
```

title Windows XP 
root (hd0,0)
savedefault
makeactive
chainloader +1
```Can you also tell us the version of windows.

-Ash R
o yea its win xp pro

---

### Post by Legace on 2009-06-05
What? I don't undestand a crap :P

Where is Windows installed? in sda5 or sda6?

---

### Post by theProdiKalson on 2009-06-05
> **Legace said:**
> What? I don't undestand a crap :P

Where is Windows installed? in sda5 or sda6?
windows install is /dev sda6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2   *          18         990     7815622+  83  Linux
/dev/sda3             991        9729    70196017+   f  W95 Ext'd (LBA)
/dev/sda5            1293        3842    20482843+   7  HPFS/NTFS
/dev/sda6            3843        9729    47287296    7  HPFS/NTFS
/dev/sda7             991        1292     2425752   82  Linux swap / Solaris

Partition table entries are not in disk order

windows install is /dev sda6

---

### Post by Bearly Able on 2009-06-05
I don't know enough to solve your problem, but when I couldn't get XP to boot from a dual-boot set-up, I was given the following advice:> In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
Code:

sudo bash ~/Desktop/boot_info_script*.sh

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.You might want to try this, to get as much information as possible for anyone who can help you fix it.

---

### Post by Legace on 2009-06-06
Post contents of **/boot/grub/menu.lst**

---

### Post by merlinus on 2009-06-06
IMFFHO, often it is better to bite the bullet, so to speak, and start over.

Back up important data, and this time install windows in a primary partition that is first on the disk.  Then create an extended partition for all remaining space, and install ubuntu into logical partitions within that.

OTOH, you can continue to tear your hair out and gnash your teeth in hopes of learning something in the process.

---


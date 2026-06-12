---
title: "Grub Error 17  PLEASE HELP"
date: 2009-06-14
forum: General Help
---

### Post by Geir Chaos on 2009-06-14
I have had duel operating systems ubuntu, and vista on my system for about 3 weeks and I wanted to put more space on the ubuntu partition; so I downloaded partition manager, and removed roughly 5 GB from a Recovery drive (which was practically empty) and moved it next to the ubuntu partition, which required a reboot.  When I rebooted my laptop it gave me the Grub Error 17!


I did quite a bit of research  and found out that 

Grub Error 17 means that Grub was unable to load selected partition
It is possible to load ubuntu with a "Live CD"


I was hopping someone could help guide me through fixing this problem, and tell me where I can get a link to download a live cd.



Any input is appreciated and THANKS in advanced

---

### Post by merlinus on 2009-06-14
Your partition numbering may have changed.  Boot from the live cd, open a terminal and enter:

```

sudo fdisk -l

```

and post results here.

---

### Post by Geir Chaos on 2009-06-14
Is there a place on the internet that I can download the iso image for the live  CD, so I can burn it then boot my computer?

---

### Post by merlinus on 2009-06-14
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Geir Chaos on 2009-06-14
Thanks, I'm downloading it now

---

### Post by Geir Chaos on 2009-06-14
```

Disk /dev/sda: 120.0 GB,     120034123776 bytes
233 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

Device Boot	Start	End	   Blocks           	    Id	             System
/dev/sda1	640	     640 	56227+	             6	             FAT16
/dev/sda2	647  	1313	5353085	     7 	     HPFS/NTFS
/dev/sda3	1313	14007	101961727+     7	             HPFS/NTFS
/dev/sda4	14008	14594	4708069+	     F	     W95 Ext&#8217;d (LBA)
/dev/sda5	14008	14310	2433816	     83	     Linux
/dev/sda6	14311	14332	176683+	    82	     Linux swap / Solaris
/dev/sda7	14333	14594	2096128	    dd	    Unknown

```


I hope you can understand this, I tried my best to make it neat.

---

### Post by MaxIBoy on 2009-06-14
Go into the live CD. Mount the partition where you installed Ubuntu. It should have a list of directories like "etc," "bin," "sbin," "usr," "var," "opt," "lib," "home," and so on. Go to the directory called "boot." Within that directory, there will be a directory called "grub," and in there will be a file called "menu.list." Please copy and paste the file into a post so we can look at it.

---

### Post by Geir Chaos on 2009-06-14
> **Geir Chaos said:**
> ```

Disk /dev/sda: 120.0 GB,     120034123776 bytes
233 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

Device Boot	Start	End	   Blocks           	    Id	             System
/dev/sda1	640	     640 	56227+	             6	             FAT16
/dev/sda2	647  	1313	5353085	     7 	                     HPFS/NTFS
/dev/sda3	1313	14007	101961727+     7	             HPFS/NTFS
/dev/sda4	14008	14594	4708069+	     F	     W95 Ext’d (LBA)
/dev/sda5	14008	14310	2433816	     83	     Linux
/dev/sda6	14311	14332	176683+	    82	     Linux swap / Solaris
/dev/sda7	14333	14594	2096128	    dd	    Unknown

```


I hope you can understand this, I tried my best to make it neat.

(I attached a word document with the results maybe it will be easier to read)

---

### Post by Geir Chaos on 2009-06-14
I looked for the file name menu.list in the grub directory, but i was unable to find the grub directory in the boot directory.

The places I was able to find the grub file was in my vista partition under the install directory.
and the live cd

---


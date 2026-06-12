---
title: "Grub Error 17... need help"
date: 2009-06-15
forum: General Help
---

### Post by Geir Chaos on 2009-06-15
I have had duel operating systems ubuntu, and vista on my system for about 3 weeks and I wanted to put more space on the ubuntu partition; so I used partition manager, and removed roughly 5 GB from a recovery drive and moved it next to the ubuntu partition, which required a reboot.  When I rebooted my laptop it gave me the Grub Error 17!

I know that Grub Error 1 means that Grub as unable to load selected partition.


This is is the results for fdisk -l 

```

Disk /dev/sda: 120.0 GB,     120034123776 bytes
233 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000


Device Boot	Start	End	   Blocks           	    Id	             System
/dev/sda1	640	     640 	56227+	             6	             FAT16
/dev/sda2	647  	1313	5353085	     7 	     HPFS/NTFS
/dev/sda3	1313	14007	101961727+     7	             HPFS/NTFS
/dev/sda4	14008	14594	4708069+	     F	     W95 Ext’d (LBA)
/dev/sda5	14008	14310	2433816	     83	     Linux
/dev/sda6	14311	14332	176683+	    82	     Linux swap / Solaris
/dev/sda7	14333	14594	2096128	    dd	    Unknown

```


Can someone help me fix this error

---

### Post by louieb on 2009-06-15
Are you getting the grub error 17 before or after you see the grub menu?

What partition manager? 

Do you have a Ubuntu live CD?

---

### Post by Geir Chaos on 2009-06-15
I see the Grub error right after the Dell loading screen finishes

To answer your question I see the Grub error before I see the Grub screen

Yes I do have a live CD

---

### Post by Geir Chaos on 2009-06-15
do you think if I re installed Grub it would fix the problem, and if so could you tell me how to do it either with terminal commands or another way?

---

### Post by louieb on 2009-06-15
Looks like Ubuntu is on sda5. or in grub speak (hd0,4) 

Boot to the live CD , open Applications>Accessories>Terminal

```
sudo grub
``` 

this will give you the **grub>** prompt

```
root (hd0,4)
setup (hd0)
quit
```

That should work. Let us know.

---

### Post by Geir Chaos on 2009-06-15
I'm trying it right now

---

### Post by Geir Chaos on 2009-06-15
WOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


thats all I needed to do, thanks a lot!

could you tell me what each of the code did, and how you knew to use it

---

### Post by noob5000 on 2009-07-18
i have a similar problem: grub error 17 after installing ubuntu in addition to an existing windows xp system.

first i installed xp (it worked and booting was no problem). then i created 3 more primary partitions.  (no other harddisc is connected to the mainboard btw)
 on the third partition i then installed ubuntu 9.04 using a live-cd.
when rebooting, i got the grub error 17 (without seeing the grub menu first).

with the live-cd i tried to execute the procedure suggested by louieb two posts above without success. upon "setup (hd0)" i got this error which leaves me baffled:  "Error 17: Cannot mount selected partition"

i have no experience with the terminal nor linux at all, and i hoped one of the more advanced users might have an idea what i could do now, in order to overcome this obsticle on my way to a functioning dual boot system... please help!


fdisk -l brings this:
```
[FONT=-moz-fixed]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       17848   133122622+   7  HPFS/NTFS
/dev/sda3           17849       19064     9767520   83  Linux
/dev/sda4           19065       19457     3156772+  82  Linux swap / Solaris
[/FONT]
```[FONT=-moz-fixed]
[/FONT]

---

### Post by merlinus on 2009-07-18
Try this:

```
sudo grub
root (hd0,2)
setup (hd0)
quit
```

---

### Post by noob5000 on 2009-07-18
i did that, and it looked like having worked succesfully.

but when rebooting, still the error 17 grins at me with his bony face...


[IMG]http://icanhascheezburger.files.wordpress.com/2007/06/halp.jpg[/IMG]

---

### Post by master_kernel on 2009-07-18
> **Geir Chaos said:**
> WOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


thats all I needed to do, thanks a lot!

could you tell me what each of the code did, and how you knew to use it

*sudo grub* opens the GRUB prompt, or the GRUB language system.
*root (hd0,4)* says "we want to get the list of systems from the configuration file on this device"
*setup (hd0)* says "install GRUB on the main hard drive master boot record"

---

### Post by merlinus on 2009-07-18
Try supergrub to boot linux:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by merlinus on 2009-07-18
Grub error 17 often occurs when something is wrong with the filesystem, and it is not recognized.

You might try this whilst running from the live cd:

```
sudo e2fsck -C0 -p -f -v /dev/sda3 
```

Copy and paste the command into a terminal.

It will try to fix any errors, but will not harm anything.

---

### Post by noob5000 on 2009-07-19
ok thanks, i will try that.

also, would it be possible to just do the windows "fixmbr" routine (re-writing the boot record, which means automatically deleting grub / overwriting it with the windows boot program, right?) and after that re-install grub?

---

### Post by merlinus on 2009-07-19
You can certainly fixmbr and fixboot, but if your linux filesystem is corrupt, reinstalling grub will obviously not fix it.

---


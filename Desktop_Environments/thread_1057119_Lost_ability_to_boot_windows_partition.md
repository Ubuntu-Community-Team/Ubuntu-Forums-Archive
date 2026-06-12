---
title: "Lost ability to boot windows partition"
date: 2009-02-01
forum: Desktop Environments
---

### Post by chocomoojuice on 2009-02-01
I had a 32-bit version of Ubuntu 8.10 installed, but realised my cpu was 64-bit, so I decided to do a fresh reinstall and upgrade.  Ubuntu boots and runs perfectly fine, but now when I try to boot Windows XP from grub, I am prompted with the error:
```
Error 13: invalid or unsupported executable format
```

I've tried browsing other threads with this issue, but I haven't been able to find a solution.  Here are my hard disk specs:
```
james@james-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005e98d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81400d71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   240284204   120142071    7  HPFS/NTFS
/dev/sdb2       244188000   488392064   122102032+  83  Linux
/dev/sdb3       240284205   244187999     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
Where /dev/sdb2 is my Ubuntu 8.10 partition, /dev/sdb1 is my Windows XP partition, and /dev/sda1 is an ext3 formatted disk used only as storage.

Here is my menu.lst file (starting just after the end of the default options):
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		13a40d67-885d-4acc-802e-d78289a15ab6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=13a40d67-885d-4acc-802e-d78289a15ab6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		13a40d67-885d-4acc-802e-d78289a15ab6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=13a40d67-885d-4acc-802e-d78289a15ab6 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		13a40d67-885d-4acc-802e-d78289a15ab6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=13a40d67-885d-4acc-802e-d78289a15ab6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		13a40d67-885d-4acc-802e-d78289a15ab6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=13a40d67-885d-4acc-802e-d78289a15ab6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		13a40d67-885d-4acc-802e-d78289a15ab6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

N.B.
I am unsure whether my Ubuntu installation being 64-bit (and my windows installation being 32-bit [I think...]) is at all the cause of my problem.  Thus, I've neglected to put this thread inside the x86-64 section.

Thanks in advance,
James

---

### Post by caljohnsmith on 2009-02-01
How about trying this entry for Windows:
```
title Windows XP
root (hd0,0)
chainloader +1
```
If that doesn't work, let me know what error you get, and also how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by chocomoojuice on 2009-02-04
> **caljohnsmith said:**
> How about trying this entry for Windows:
```
title Windows XP
root (hd0,0)
chainloader +1
```


Wow, I love how simple a solution it was.  Thank you so much for your help, I can now use windows again (but only to play games of course).
The strange thing is, I tried exactly what you suggested, except with a slight variation: 

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

i.e. I didn't remove the savedefault and makeactive statements, as I was unsure of their meaning.  Might you enlighten me as to what these statements are for, and why you saw it appropriate to remove them?  If you're too busy to respond, no worries, I'm just curious.

All in all, thanks again, things are working just fine again.
- James

---

### Post by caljohnsmith on 2009-02-04
> **chocomoojuice said:**
> 
The strange thing is, I tried exactly what you suggested, except with a slight variation: 

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

i.e. I didn't remove the savedefault and makeactive statements, as I was unsure of their meaning.  Might you enlighten me as to what these statements are for, and why you saw it appropriate to remove them? 
"**Makeactive**" means to set the boot flag on the partition, yet Grub can boot a partition regardless of whether it has the boot flag set or not; the boot flag is mainly relevant for a Windows-type MBR (Master Boot Record), because all a Windows MBR does is boot whichever primary partition has the boot flag set. Also, once you set the boot flag on a partition, you don't have to keep setting it every time you boot that partition. Thus using "makeactive" in the menu.lst is entirely superfluous under normal circumstances, and I never use it in the menu.lst since there is no reason to do so under normal circumstances. 

"**Savedefault**" makes Grub remember when you boot that OS, so if you set up your menu.lst accordingly, you could have Grub automatically use the last booted OS as its default entry the next time you boot. So again, it is not necessary, but "savedefault" is useful if you like that feature. 

Glad you can boot Windows OK; cheers and have fun gaming in Windows and enjoy your Ubuntu install. :)

---


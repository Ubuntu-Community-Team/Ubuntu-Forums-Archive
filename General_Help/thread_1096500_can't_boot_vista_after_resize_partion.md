---
title: "can't boot vista after resize partion"
date: 2009-03-15
forum: General Help
---

### Post by terpdan on 2009-03-15
shrank my vista partition and grew my ubuntu partition using gparted live cd. now i can't boot vista. I ran boot_info_script and it looks like some confusion over where the boot sector is. any suggestions?

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000abf88

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   625,137,344   461,290,410   5 Extended
/dev/sda5         163,846,998   619,900,154   456,053,157  83 Linux
/dev/sda6         619,900,218   625,137,344     5,237,127  82 Linux swap / Solaris

---

### Post by meierfra. on 2009-03-15
Check out this link

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

---

### Post by renkinjutsu on 2009-03-15
i had this same problem, but i didn't think it was worth my trouble to fix, so i just stretched my ubuntu partition over my vista partition =D

only thing now is.. i can't play certain games anymore, but it's fine
and i can always use photoshop on my sister's mac if i need to

---

### Post by adult swim on 2009-03-15
what is the output of ```
sudo blkid

cat /boot/grub/menu.lst
```

---

### Post by terpdan on 2009-03-15
here is the output

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f0990563-a458-4925-a642-69beada642ab
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f0990563-a458-4925-a642-69beada642ab
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		f0990563-a458-4925-a642-69beada642ab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f0990563-a458-4925-a642-69beada642ab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f0990563-a458-4925-a642-69beada642ab
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f0990563-a458-4925-a642-69beada642ab
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f0990563-a458-4925-a642-69beada642ab
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by terpdan on 2009-03-15
and the sudo blkid

/dev/sda1: UUID="826C547A6C546B45" TYPE="ntfs" 
/dev/sda5: UUID="f0990563-a458-4925-a642-69beada642ab" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="950e52eb-9722-4294-a5fc-c6e18b8235df"

---

### Post by khelben1979 on 2009-03-15
Shrinking or growing partitions with GParted seems a bit dangerous.

I wonder if commercial software which handles these types of things are able to produce better quality with this? What do you think?

A few years ago I saw software which could shrink or grow partitions but the partitions needed to be reformatted everytime after the change had occured.

---

### Post by terpdan on 2009-03-15
The procedure in the link above didn't work for me, worth a try..

I ended up reinstalling vista, no biggee other than the time, it was barely used since install. 

used quick start option at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to get grub working again

i only keep windows for two things: go-to-meeting and tax software

thanks for help

---

### Post by meierfra. on 2009-03-15
Glad you got your problems resolved.


> The procedure in the link above didn't work for me,

Strange. It usually does the job.  Just for the benefit of others who have the same problem: 
  What happened after  you chose "Repair Computer"? 
Did you get the "Windows found problems with your computer's startup option" dialog box?
Did  Windows repair your computer, but it did not help?

---

### Post by jimmyhacker on 2009-03-15
> **meierfra. said:**
> Check out this link

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

Lol!in that article say`s if you don`t want to see "recovered" text at boot download VistaBootPro!hahahaha.You can modify C:/boot.ini instead of downlading a stupi Visual Basic script renamed as .exe

---

### Post by meierfra. on 2009-03-15
> You can modify C:/boot.ini instead of downlading a stupi Visual Basic script renamed as .exe 

That works for XP. But Vista does not even  have a "boot.ini"

---


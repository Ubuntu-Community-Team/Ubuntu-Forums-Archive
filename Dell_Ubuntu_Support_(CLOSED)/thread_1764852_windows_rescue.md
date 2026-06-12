---
title: "windows rescue"
date: 2011-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pranav.grd on 2011-05-22
this is my boot info script
> 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    86,018,047    85,811,200   7 NTFS / exFAT / HPFS
/dev/sda3          86,018,048   290,818,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda4         290,820,094   625,139,711   334,319,618   f W95 Extended (LBA)
/dev/sda5         374,790,144   625,139,711   250,349,568   7 NTFS / exFAT / HPFS
/dev/sda6         290,820,096   308,396,031    17,575,936  82 Linux swap / Solaris
/dev/sda7         308,398,080   374,777,855    66,379,776  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        58FAB7FCFAB7D48A                       ntfs       System Reserved
/dev/sda3        F87640447640063A                       ntfs       Entertainment
/dev/sda5        EEAEAA29AEA9E9F3                       ntfs       Documents
/dev/sda6        1bdc6bd2-310f-4556-94ac-030f2d08e076   swap       
/dev/sda7        102761e5-adad-4e2d-9e88-47e7062e86c3   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

/home/pranav/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")



---

### Post by Rubi1200 on 2011-05-22
Hi and welcome to the forums :-)

What exactly is your question please?

---

### Post by pranav.grd on 2011-05-24
i have lost access to my window 7 OS...i have pasted the output of the boot info script...can u plzz help me get access to my window partition

---

### Post by Rubi1200 on 2011-05-24
Firstly, unless there is some problem you are not telling us about, this is not the whole content of the script.

Where are the Linux entries?

What distro are you running and what version?

If you just want the fix to restore the Windows bootloader that is fine, but then you will be unable to boot your Linux install.

Is that what you want?

---

### Post by tgguadarrama on 2011-05-26
Hi:
 

 I'm Tom.
 

 I already installed, ubuntu 11.04 in my LapTop (Dell 14R with windows 7 Home Premium 64-bit), using ”ubuntu junto windows 7”, option to install. When I chose boot from windows 7 in the Grab menu, this menu refresh every time I selected. I would like to work in windows too. How can I solve this inconvenient?


Ubuntu is working well

---

### Post by Elfy on 2011-05-26
@ tgguadarrama - please do not hijack threads - you'll notice it doesn't always work - _even if you do it twice_ - please start your own thread - here's a nice easy link to do so - [http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)

---

### Post by dyem1 on 2011-05-26
You might open a terminal (alt+F2 and put gnome-terminal) and enter the code ```
sudo update-grub
```this will ask you your password and will re-scan partitions and look after OS that can be booted. That might help. Then reset and try to enter to your windows partition. If it doesn't help, use the terminal and post here the output of ```
sudo fdisk -l 
```

---

### Post by Gert Hulselmans on 2011-05-31
@ pranav.grd

Can you copy the grldr file on sda1 to your home directory?

Then run:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null |  hexdump -v -e '/1 "%02x"' | grep -b -o  'b0021ace000000000000000000000000'
```If it produces any output, post  it.

Else, try:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null |  hexdump -v -e '/1 "%02x"' | less
```(press 'q' to quit)

If this showed, you a lot of hexadecimal characters, try the following:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null |  hexdump -v -e '/1 "%02x"' | grep -b -o '47524c4452'
```And post the  output.

---


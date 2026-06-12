---
title: "usb disk mount problem"
date: 2024-05-13
forum: Desktop Environments
---

### Post by okkadiroglu on 2024-05-13
Hi,

I am using Kubuhtu 22.04LTS 6.5.0-28-generic (64bit) and KDE Plasma 5.2.4.7. I have a 3TB USB disk that I store movies in which I connect to Philips Android TV. For a very long time, I did not have any problems with this set up. Recently, Philips updated its software and playing .avi files became impossible. I decided to convert all .avi files to .mkv file. When I connected my USB disk to my computer, I was able to see what is in the USB disk.  I was able to change few files and checked them on the TV set to see if they work. When I tried to connect USB disk to the computer again, I got an error message: An error occurred while accessing 'Elements', the system responded: The requested operation has failed: Error mounting /dev/sdd1 at /media/oyo/Elements: Unknown error when mounting /dev/sdd1. I tried to mount the disk manually, but I was not successful. The output of fdisk -l for this USB disk is: Disk /dev/sdd: 2.73 TiB, 3000558944256 bayt, 5860466688 sektör
Disk model: Elements 25A1   
Birimler: sektör'i 1 * 512 = 512 bayt&#305;n
Sektör boyutu (mont&#305;ksal/fiziksel): 512 bayt / 4096 bayt
G/Ç boyutu (en dü&#351;ük/en uygun): 4096 bayt / 4096 bayt
Disketikeri tipi: gpt
Disk belirleyicisi: AA83D11B-614D-43FD-8A82-CF7FBCD316D1
 Sorry for some reason unknown to me, some of my software speaks Turkish.

How can mount this disk?

Many thanks, and best regards

---

### Post by TheFu on 2024-05-13
[https://askubuntu.com/questions/113733/how-to-mount-a-ntfs-partition-in-etc-fstab](https://askubuntu.com/questions/113733/how-to-mount-a-ntfs-partition-in-etc-fstab)

There are multiple ways.  I'm assuming the partition is NOT broken and using NTFS.  You can use the UUID, LABEL or correct device filename (/dev/sdd1?) to mount using the fstab or manually with the **sudo mount .... ** command (providing the correct options.  Here's the way I manually mount a USB drive with NTFS that gets moved between devices:  
```

sudo mount -t ntfs LABEL=Recordings /misc/Recordings \
      -o nodev,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002
```
The LABEL was set on the file system using **gparted**.  LABELs are easier for us humans than device files or UUIDs.  The uid/gid values are for my username on the computer. The first user starts at 1000.  Use the **id** command so see the numbers of the uid and gid for your username. It is a coincidence that they are both 1000. They are two separate numbers.  The fmask and dmask set Linux permissions in a safe way for NTFS.

I don't read Turkish, but the **fdisk** output doesn't show any partition, so I fear the drive is failing and needs to be replaced. You should create a mirror bit-by-bit copy of the HDD onto a new HDD as the first thing you do.  Sometimes disks fail.  Sometimes disk controllers fail.  Sometimes just specific sectors on the disk fail, but when that starts happening, it is usually a sign that the whole drive will fail in a few hours or days.  If you set the LANG environment variable to a different language just before running the program from the same shell window, then the output should be in the language specified if those language files are available.

```
LANG=en_US.UTF-8 sudo fdisk -l /dev/sdd 
```

GB, AU, CA, can be used instead of US, if you like. Another handy command is this:
```
LANG=en_US.UTF-8  lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

This will help people here provide better help. So will using _forum code-tags_, like I've done.  In the advanced editor, use the # button. Best to use that for all terminal output so the spacing and formatting is maintained when posted here.  Bad spacing makes it hard to read.

To see how bad things are, use **smartctl** to run a smart test. After the test finishes, run a smart report to see the output.  If you post the output here, we can help interpret it.  Some USB disk controllers won't allow SMART testing and SMART needs to be enabled in the motherboard BIOS before it can be used.  [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) explains.  There are also a number of examples in these forums for using smartctl, showing the output and interpreting it.

But the first thing you need to do is create a full mirror of that disk. I'd use **ddrescue** and do it ASAP.

---

### Post by okkadiroglu on 2024-05-17
Thank you very much for your help. I tried Windows and run chkdsk /f as proposed by my system and it worked.

Best Regards

---


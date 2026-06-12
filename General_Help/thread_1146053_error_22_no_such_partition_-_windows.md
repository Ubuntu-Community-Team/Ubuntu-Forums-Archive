---
title: "error 22: no such partition - windows"
date: 2009-05-02
forum: General Help
---

### Post by AceCraft on 2009-05-02
Hi! 
Recently I was messing up in /dev/sdb disk (usb) and when I restarted my computer (dual boot: windows and ubuntu) to run windows I received error 22: no such partition. I suspect I had inattentively changed / removed windows partition. Please take a look on fdisk output:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb439d36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        5230       30401   202194090    7  HPFS/NTFS
/dev/sda3            2491        5229    22001017+   5  Extended
/dev/sda5            2491        2733     1951866   82  Linux swap / Solaris
/dev/sda6            2734        5229    20049088+  83  Linux

Partition table entries are not in disk order

```

As far I can remember Windows partition was more or less of the size of Linux one (sda6 here). But when I changed booting place in KGRUBEditor for (hd0,2) I received another error 12: invalid device. I am not sure if changing file system will not wipe out data on the partition. Can somebody help me to solve this problem? Have I removed Windows or just changed file system?

EDIT:

I ran boot_info_scritp032.sh and received:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb439d36

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *     84,003,885   488,392,064   404,388,180   7 HPFS/NTFS
/dev/sda3          40,001,850    84,003,884    44,002,035   5 Extended
/dev/sda5          40,001,913    43,905,644     3,903,732  82 Linux swap / Solaris
/dev/sda6          43,905,708    84,003,884    40,098,177  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="5808097308095204" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="78ee882f-d71b-478d-846b-30400ae62945" 
/dev/sda6: UUID="4c3b340f-def9-4e28-9cac-6bc578e98664" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /mnt/drive_d type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michal)

```

So according to this there should be Windows on sda2, but there isn't? Can it be, GRUB cannot locate it?

---

### Post by Woody1987 on 2009-05-02
can you copy the contents of /boot/grub/menu.lst

---

### Post by AceCraft on 2009-05-02
sure, here you go:
```

default 4
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4c3b340f-def9-4e28-9cac-6bc578e98664 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4c3b340f-def9-4e28-9cac-6bc578e98664

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4c3b340f-def9-4e28-9cac-6bc578e98664 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4c3b340f-def9-4e28-9cac-6bc578e98664 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault
makeactive

```

any clues? I am not an expert, but this look for me ok.

---

### Post by Woody1987 on 2009-05-02
This might work, in menu.lst, change the root(hd0,1) to root (hd0,2) for the windows entry.

EDIT, ignore that, it wont work, just realised.

---

### Post by AceCraft on 2009-05-02
just noticed: shouldn't there be in "Operating System" mentioned Windows XP?

```

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   


```

like in ubuntu:
```

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab


```

How to change this? MEaby thats the problem?


EDIT:

I have changed /boot/grub/menu.lst file by commenting #Other Operating system and #root:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

#title Other operating systems:
#root

title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault
makeactive

```

Now I receive error: lack of NTLDR file... Wow, it makes a diffrence :P so I suppose I need to install this NTLDR again on my windows partition in order to use it again?

---

### Post by caljohnsmith on 2009-05-02
Did your original Grub menu.lst entry for Windows use (hd0,0)? That would explain your Grub error 22, because sda1 no longer exists. In fact, you have ~20 GB of unused space at the beginning of the HDD, so did you maybe accidentally delete your sda1 partition? According to the Boot Info Script, sda2 does not have Windows XP, so sda2 is probably a data partition. If you did indeed unintentionally delete sda1 and would like help recovering it, let me know, and I can give you specific directions of how to use "testdisk" to recover that partition. 

Regards,
John

---

### Post by AceCraft on 2009-05-02
Yes, I will need your help! Indeed just recently I discovered that I've deleted Windows partition.

Unfortunately while trying to fix that and recover files I have also deleted GRUB (or at least I suppose so -> used Windows XP bootable cd). Now I cannot boot neither Windows nor Ubuntu -> "The partition doesn't have an operating system" so I'm writing right now from second laptop. If you could help me solving this mess I've created please write me what to do.

P.S. I have created a new partition from that free space (its sda1 now), but didn't formated it, just gave file system as NTFS (via fdisk from kubuntu live cd). Is the situation hopeless or can still recover data from it?

Thank you for your help!

---

### Post by caljohnsmith on 2009-05-02
OK, how about doing:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "No Log", select the sda HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. We can work from there.

John

---

### Post by AceCraft on 2009-05-02
Right, for deep scan I received:

```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  2489 254 63   40001787
D Linux                 2490   0  1  4979 254 63   40001850
D Linux Swap            2490   1  1  2732 254 63    3903732
D Linux                 2733   1  1  5228 254 63   40098177
D Linux                 3966   2  1  6462 254 63   40114179
D HPFS - NTFS           5229   0  1 30400 254 63  404388180
D Linux Swap           29645   1  1 30400 254 63   12145077

```

and for specific NTFS partitions:  nothing for now, because i accidental exited the program...

EDIT: Actually I didn't. The program receive segmentation fault every time i try to list files of NTFS file system. But when i do the same to Linux partition it writes:

```

   * Linux                 2490   0  1  4979 254 63   40001850
Use Right arrow to change directory, q to quit
Directory /

No file found, filesystem seems damaged.

```

```

   D Linux                 2733   1  1  5228 254 63   40098177
Use Right arrow to change directory, q to quit
Directory /

drwxr-xr-x     0     0      4096 29-Jan-2009 17:34 .
drwxr-xr-x     0     0      4096 29-Jan-2009 17:34 ..
drwx------     0     0     16384  7-Nov-2008 22:24 lost+found
drwxr-xr-x     0     0      4096 29-Oct-2008 23:12 var
drwxr-xr-x     0     0     12288  2-May-2009 15:55 etc
drwxr-xr-x     0     0      4096  2-May-2009 15:44 media
lrwxrwxrwx     0     0        11  7-Nov-2008 22:24 cdrom
drwxr-xr-x     0     0      4096 25-Apr-2009 08:29 bin
drwxr-xr-x     0     0      4096 25-Apr-2009 08:32 boot
drwxr-xr-x     0     0      4096 29-Oct-2008 23:04 dev
drwxr-xr-x     0     0      4096  7-Nov-2008 22:34 home
drwxr-xr-x     0     0     12288 25-Apr-2009 08:29 lib
drwxr-xr-x     0     0      4096  2-May-2009 11:27 mnt
drwxr-xr-x     0     0      4096 29-Oct-2008 22:53 opt
drwxr-xr-x     0     0      4096 20-Oct-2008 12:27 proc
drwxr-xr-x     0     0      4096  2-May-2009 15:45 root

```

So basicaly I have Ubuntu installed on sda and as I can remember the first NTFS partition is with Windows.

---

### Post by JK3mp on 2009-05-02
+1 on johncalsmith, it does appear that you have no sda1, BIG problem. I know windows vista at least , there is an sda1 partition (Unknown), and sda2, NTFS. And you probably deleted the sda1 partition where it stores your related files for Windows Vista, just follow cal's i've had to use testdisk b4 on a freinds laptop and its VERY useful.

---

### Post by AceCraft on 2009-05-02
yeah, but on my comp testdisk makes an Segmentation fault while trying to read NTFS partition [look my previous post]

---

### Post by caljohnsmith on 2009-05-02
> **AceCraft said:**
> yeah, but on my comp testdisk makes an Segmentation fault while trying to read NTFS partition [look my previous post]
Are you using Ubuntu 9.04? I assumed you were using 9.04 (which I shouldn't have and which must not be true) because if you are using 9.04 you would have downloaded testdisk version 6.10 from the repos, whereas previous Ubuntu versions download testdisk 6.09 or earlier. The problem is that testdisk versions prior to 6.10 always crash when doing a directory listing on an NTFS partition, so its not your fault; the fault is mine for assuming you were using Ubuntu 9.04. 
> **AceCraft said:**
> Right, for deep scan I received:

```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0   1  1  2489 254 63   40001787
[COLOR="Red"]D[/COLOR] Linux                 2490   0  1  4979 254 63   40001850
[COLOR="Red"]L[/COLOR] Linux Swap            2490   1  1  2732 254 63    3903732
[COLOR="Red"]L[/COLOR] Linux                 2733   1  1  5228 254 63   40098177
[COLOR="Red"]D[/COLOR] Linux                 3966   2  1  6462 254 63   40114179
[COLOR="Red"]P[/COLOR] HPFS - NTFS           5229   0  1 30400 254 63  404388180
[COLOR="Red"]D[/COLOR] Linux Swap           29645   1  1 30400 254 63   12145077

```

OK, how about using your up/down arrow keys to select each partition, and then use your right/left arrow keys to mark each partition as I've shown highlighted in red above. Once you're sure the partitions are marked exactly as shown above, press enter to get the next screen, and there you can write the new partition table. Once you've written the new partition table, reboot, and once you get back into Ubuntu, please post the output of the **Boot Info Script** again so I can check that everything went as planned, and whether you will need to do anything booting-wise. 

John

---

### Post by AceCraft on 2009-05-03
Ok, I have received following output after writing new partition table:

```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  2489 254 63   40001787

Boot sector
Status: Bad

Backup boot sector
Status: OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

so I presume the new partition table wasn't created, so I just quit (other options were: [  Quit  ]  [  List  ]  [Backup BS] [Rebuild BS][  Dump  ] )

---

### Post by caljohnsmith on 2009-05-03
Before we allow testdisk to fix your NTFS partition boot sector, it would help to see the output of the Boot Info Script, because that will give us a better a idea if you need to use the "Backup BS" or the "Rebuild BS" option in testdisk, or possibly both. Please go ahead and run the Boot Info Script and post the results. We can work from there.

John

---

### Post by AceCraft on 2009-05-03
Ok, the output is:

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:
    Boot sector type:  -
    Boot sector info:
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb439d36

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,001,849    40,001,787   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs"

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

```

there were more partitions than just sda1...

---

### Post by caljohnsmith on 2009-05-03
It looks like you need to go through the testdisk procedure again and write the new partition table to your HDD. When testdisk prompts you again about fixing the NTFS partition boot sector, choose the "Rebuild BS" option. Then quit testdisk and do:
```
sudo fdisk -lu
```
Make sure that command shows all your partitions as they should be, and if it does, rerun the Boot Info Script and please post the output. We can work from there.

John

---


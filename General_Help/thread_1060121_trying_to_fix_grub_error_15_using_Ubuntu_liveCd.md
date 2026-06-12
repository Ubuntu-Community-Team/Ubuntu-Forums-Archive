---
title: "trying to fix grub error 15 using Ubuntu liveCd"
date: 2009-02-04
forum: General Help
---

### Post by thugpoet22 on 2009-02-04
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf746f746

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12029    96622911    7  HPFS/NTFS
/dev/sda2           12030       30401   147573090    f  W95 Ext'd (LBA)
/dev/sda5           22753       30401    61440561    7  HPFS/NTFS
/dev/sda6           12030       14970    23623519+  83  Linux
/dev/sda7           14971       15103     1068291   82  Linux swap / Solaris
/dev/sda8           15104       15129      208782   83  Linux
/dev/sda9           15130       22752    61231716   8e  Linux LVM

```

This is my Sudo Fdisk-l. I figured i should start with that. I figured out how to get windows to boot again. but for what ever reason the grub boot loader does not recognize any of these linux partitions. Now truthfully I'm not even sure which is used to boot into Linux.

I got it to work up to this point by using knoppix and thought i restored the MBR but now it reads Fedora and Other (Other bring the windows partition)

But when i click on Fedora i get the error 15. I don't understand why its Fedora. I have not used that distro in a while. 

My current issue is getting the linux that i have on that drive to be recognized by the grub boot loader. 

I think in order for me to work with those linux partition getting them mounted is the first step. Please if there is any more info that i can impart  that's not already stated. Who ever takes time to help me i just want to thank you in advance.

---

### Post by caljohnsmith on 2009-02-04
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your Grub error 15 might be.

---

### Post by cariboo on 2009-02-04
I would suggest you boot from the the LiveCD,  once you are at the desktop, open a Applications-->Accessories-->Terminal and type:

```
sudo grub
```

this will start the grub editor, next wee need to find which partition grub is installed on:

```
find /boot/grub/stage1
```

It should echo back something like this:

```
(hd0,5)
```

In your case it may be different, now that you have found where /boot/grub is installed type:

```
root (hd0,5)
```

This will set where /boot/grub is located, then

```
setup (hd0)
```

this will write grub to the MBR and finally type:

```
quit
```

You should now be ready to reboot, and the grub menu should show at startup.

Jim

---

### Post by thugpoet22 on 2009-02-04
Here is the information that you requested. I hope it helps.


```


 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda9: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf746f746

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   193,245,884   193,245,822   7 HPFS/NTFS
/dev/sda2         193,245,885   488,392,064   295,146,180   f W95 Ext d (LBA)
/dev/sda5         365,510,943   488,392,064   122,881,122   7 HPFS/NTFS
/dev/sda6         193,246,011   240,493,049    47,247,039  83 Linux
/dev/sda7         240,493,113   242,629,694     2,136,582  82 Linux swap / Solaris
/dev/sda8         242,629,821   243,047,384       417,564  83 Linux
/dev/sda9         243,047,448   365,510,879   122,463,432  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="80B0EFA3B0EF9DC2" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=8

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="MS WINDOWS XP SP2/SP3 UWin Installer Edition" /noexecute=optin /fastdetect


=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda7


Unknown BootLoader  on sda8


Unknown BootLoader  on sda9



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sda8: No such file or directory
hexdump: /dev/sda8: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sda9: No such file or directory
hexdump: /dev/sda9: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
```

---

### Post by caljohnsmith on 2009-02-04
Neither your sda6 nor sda8 linux partitions could be mounted, and blkid was not even able to detect their file system types. Are sda6 and sda8 LVM or encrypted? Do you have any idea what would have happened to those partitions? How about posting:
```
sudo vol_id --probe-all /dev/sda6
sudo vol_id --probe-all /dev/sda8
```

---

### Post by thugpoet22 on 2009-02-04
Im pretty sure that they are LVM (dont even know what that is) 

Here is the read out for the latest codes 

ubuntu@ubuntu:~$ sudo vol_id --probe-all /dev/sda6
/dev/sda6: error opening volume
ubuntu@ubuntu:~$ sudo vol_id --probe-all /dev/sda8
/dev/sda8: error opening volume
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2009-02-04
I have very little experience with LVM, but you could try:
```
sudo apt-get install lvm2
sudo vgdisplay
sudo lvdisplay
```
And please post the output.

---

### Post by thugpoet22 on 2009-02-04
```
ubuntu@ubuntu:~$ sudo vol_id --probe-all /dev/sda6
/dev/sda6: error opening volume
ubuntu@ubuntu:~$ sudo vol_id --probe-all /dev/sda8
/dev/sda8: error opening volume
ubuntu@ubuntu:~$ sudo apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  lvm2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 325kB of archives.
After this operation, 918kB of additional disk space will be used.
0% [Working]
Get:1 http://archive.ubuntu.com hardy/main lvm2 2.02.26-1ubuntu9 [325kB]
Fetched 325kB in 1s (315kB/s)
Selecting previously deselected package lvm2.
(Reading database ... 98223 files and directories currently installed.)
Unpacking lvm2 (from .../lvm2_2.02.26-1ubuntu9_i386.deb) ...
Setting up lvm2 (2.02.26-1ubuntu9) ...
Backing up any LVM2 metadata that may exist...done.
update-initramfs is disabled since running on a live CD

ubuntu@ubuntu:~$ sudo vgdisplay
  No volume groups found
ubuntu@ubuntu:~$ sudo lvdisplay
  No volume groups found

```

Nothing was found but when i do a sudo fdisk -l i get what was in the first post 
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf746f746

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12029    96622911    7  HPFS/NTFS
/dev/sda2           12030       30401   147573090    f  W95 Ext'd (LBA)
/dev/sda5           22753       30401    61440561    7  HPFS/NTFS
/dev/sda6           12030       14970    23623519+  83  Linux
/dev/sda7           14971       15103     1068291   82  Linux swap / Solaris
/dev/sda8           15104       15129      208782   83  Linux
/dev/sda9           15130       22752    61231716   8e  Linux LVM


```

That last partition sda9 shows that it is LVM

---

### Post by caljohnsmith on 2009-02-04
I don't know what else to suggest, because none of your linux partitions are mountable, readable, or even recognizable as having a valid file system. Do you have any idea what you might have done that would have caused that to happen? When was the last time you could access those partitions?

---

### Post by thugpoet22 on 2009-02-04
The last thing i remember doing was asking my linux system to hybernate so that i would have to go through the whole boot up process. And Then i booted into windows and with in MY computer i clicked on my individual drives and under properties i put in descriptive lables. I thought that this would make it easier to organize information. But i think that small change might have messes up the profile of those partitions and now when grub boots its looking for something specific that has been changed in some way. I think my last course of action is going to be to reinstall my ubuntu. I really did not want to do this. I spent so much time getting to where its at right now.

---

### Post by caljohnsmith on 2009-02-04
> **thugpoet22 said:**
> And Then i booted into windows and with in MY computer i clicked on my individual drives and under properties i put in descriptive lables. 
Unfortunately I think that is probably at least part of the problem. Windows only knows how to apply labels to NTFS and FAT partitions, so I think Windows might have really messed up your linux partitions. Just for future reference, if you want to give your Linux partitions labels, you can do it with gparted for example (the Ubuntu partition editor). But about your partition problem, there is at least some possibility that "testdisk" might be able to read your partitions, and if so you can copy over important files that you want to recover. If you want to try that, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, again use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. Also, if any of the partitions give you a directory listing, you can navigate through them with the arrow keys and use "c" to copy any files you want. Let me know how it goes.

---


---
title: "gparted (and thus qtparted) seeing my hard drive as unformatted"
date: 2006-07-11
forum: Desktop Environments
---

### Post by tedwick on 2006-07-11
preface: i'm brand new to linux and ubuntu. however, i'm getting somewhat comfortable with the terminal. any help or pointers would be very much appreciated.

so, i've got a problem where, when i start gparted (via the live cd installer) or qtparted, it sees my hard drive as unformatted. now, i'm pretty sure that isn't correct, since i can boot into ubuntu as well as boot into windows (i will give ubuntu lots of credit for making it so easy to make a dual boot setup). instead of seeing the multiple partitions on my disk, which ubuntu can mount and read no problem, it just sees /dev/sda as unformatted, and when i click on it in qtparted, it starts some process, tries to initialize it and then gives an error message "Critical error during ped_disk_new!". the terminal gives me 
```
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
```
the terminal repeats this error message twice. upon closing qtparted, it gives me
```
error: Unable to satisfy all constraints on the partition.
A bug has been detected in GNU Parted. Refer to the website of parted http://www.gnu.org/software/parted/parted.html for more informations of what coud be useful for bug submitting! Please email a bug report to bug-parted@gnu.org containing at least the version (1.6.25.1) and the following message: Assertion (disk != NULL) at ../../libparted/disk.c:1074 in function ped_disk_next_partition() failed.
```

some background, if it's helpful. I'm brand new to linux and ubuntu, installed it two days ago. when i first installed it, i formatted the drive into four partitions (two being ones dell preinstalled, one being my windows partition, and the other being a partition with logical partitions within, one ext3, one swap, and one fat32 for data). i got the system working, but tried to install compiz and xgl and screwed everything up. so i reinstalled again, and decided to mess with the size of the partitions again. the partitioner appeared to finish, but hung afterward. i rebooted, and the partitioner in the installer saw all the partitions fine. so i reinstalled, and everything came up fine. except i now have this problem. any way to fix it without wiping the drive, which qtparted seems to want to do?

EDIT: where it says "unformatted", it should read "unallocated". simply forgot, don't know if that makes a difference.

---

### Post by radiazo on 2006-07-11
Hello. What method is using you for launch gparted? is you launching it from console or from the menu. that appears like you don't have complete rights to access sda1.
Please attach a list of your hardware configuration, and lspci.

---

### Post by tedwick on 2006-07-11
i just used
```
sudo qtparted
```
it worked before, on my first installation.

---

### Post by radiazo on 2006-07-11
what is your system configuration? what live cd version is using you? please use dmesg | grep sda for looking for errors.

---

### Post by tedwick on 2006-07-11
running the linux-686-smp kernel, dual core intel. ati video card (which was somewhat difficult to get the correct drivers for). i just have the Dapper Drake 6.06 live cd, downloaded the .iso over the weekend.

i ran "sudo dmesg | grep sda". i'm not sure what the command does, but the output i got didn't seem to indicate any errors.
```
[17179569.184000] Kernel command line: root=/dev/sda7 ro quiet splash
[17179576.136000] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[17179576.136000] SCSI device sda: drive cache: write back
[17179576.136000] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[17179576.136000] SCSI device sda: drive cache: write back
[17179576.136000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[17179576.180000] sd 0:0:0:0: Attached scsi disk sda
[17179587.228000] Adding 2144668k swap on /dev/sda5.  Priority:-1 extents:1 acro ss:2144668k
[17179587.256000] EXT3 FS on sda7, internal journal
```

not sure if there's anything you can see in that. the more i think about it, i think it might have something to do with the partitioner locking up during an attempted install. is there a file that parted reads on the disk that defines where the partitions are that might have been corrupted if the partitioner locked up? because that would mean that all the partitions do exist, and parted just can't see them. and if so, is there anyway to fix that file without data loss? i wish i knew enough to fix this, but i don't. thanks.

---

### Post by radiazo on 2006-07-12
you use dmesg for view the system response during boot. grep only shows the lines that contains sda (as show in your data).
The system shows that you have your disk partitioned and shows the partitions in it. in your case you have 7 partitions. four of it's are primary partitions (sda1 to sda4) and other 4 partitions are secondary and are located in one of your primary partitions. Maybe parted don't found the correct structure in the disk, but you have other tools to modify your partitions. Using fdisk or cfdisk.
But, ¿what exactly you wish to make with your actual instalation? you need to remove your linux instalation or replace them with a fresh instalation? depends of your answer I help you with the process

---

### Post by tedwick on 2006-07-12
well, i wanted to be able to reinstall ubuntu on the partition i have for it instead of erasing the whole drive. i don't really NEED to do it, but i am quite worried about screwing something up and having to reinstall.

anyway, i ran "sudo cfdisk /dev/sda" and it output
"FATAL ERROR: Bad logical partition 7: enlarged logical partitions overlap"

so i think it just told me what the problem is. do you know how to fix it?

---

### Post by radiazo on 2006-07-12
you have a partition problem with your disk. the problem isn't easy fixed. what happen when you try to open it with fdisk?? if its possible, for fast comunication you try to chat with me in msn messenger (ignore the points) neosol._.27[at]hotmail[dot]com

---


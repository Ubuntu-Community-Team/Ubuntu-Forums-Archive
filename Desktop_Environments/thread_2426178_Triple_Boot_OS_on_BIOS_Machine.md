---
title: "Triple Boot OS on BIOS Machine"
date: 2019-09-05
forum: Desktop Environments
---

### Post by Rick St. George on 2019-09-05
Wish: boot to multiple OS on my Laptop. Have 2 installed, want to install a 3rd

Laptop: EliteBook 6930p
BootMode: BIOS
Partitions: 4, 250 GB on 1TB HDD
OSes: Win7 and Xubuntu (dual boot via Grub)

Problems: 

1. Don't know if Grub will work for all 3.
2. Don't know if direct install of OS to Partition 3 will be picked up by Grub or if I can modify the Grub file.
3. Could not find releative help on this subject matter.
4. Found info on ReFIND as Boot Manager, but unsure if it will work with Non-EFI computer/laptop.

Any help / instructions are appreciated for any and all concerned.
Thanks!

---

### Post by oldfred on 2019-09-05
You can only use rEFInd on UEFI systems.
Grub will boot just about anything as long as all installs are in same boot mode, all UEFI or all BIOS.

If BIOS with MBR partitioning, you have the 4 primary partition limit that gpt does not have.
Post this:
sudo parted -l

If multiple Linux installs, I prefer to turn off os-prober and manage my own boot stanza in grub's 40_custom file. With multiple installs, you get the issue of each updating, each wanting control of MBR, but only one system can have MBR unless you have multiple drives each with a MBR. And you want grub in MBR for system you use the most, but an update in other system will require another update in main system to recognize second system's update.

You can install without grub to keep current system in charge. ubiquity -b in the installer's terminal. Or you can re-install grub from main working install after booting into it from new install.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)

---

### Post by Rick St. George on 2019-09-05
> **oldfred said:**
> Y
If BIOS with MBR partitioning, you have the 4 primary partition limit that gpt does not have.
Post this:
sudo parted -l



```

$ sudo parted -l
Model: ATA ST1000LM048-2E71 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  236GB   236GB   primary   ntfs            boot
 2      236GB   472GB   236GB   primary   ext4
 3      472GB   1000GB  528GB   extended
 5      472GB   682GB   210GB   logical   ntfs
 6      682GB   993GB   310GB   logical   ntfs
 7      993GB   1000GB  7591MB  logical   linux-swap(v1)


```

sda # 5 above is what I'll use, not formatted yet. Will make EXT4 to install ZorinOS to see if she likes it.

---

### Post by oldfred on 2019-09-05
I have multiple Ubuntu flavors & versions installed.
But I install each to a 25 or 30GB / (root) partition. 
My main working install including /home (but no data) is 6.5GB, regularly housecleaned on SSD.
```
fred@bionic-z97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
----
/dev/sda7        29G  6.5G   21G  25% /
/dev/sdb4       385G   68G  297G  19% /mnt/data


```

But I have all my data normally in /home in a large data partition on HDD that I mount & link folders into most of my installs, so I have same data in all of them.

---

### Post by Rick St. George on 2019-09-05
That is SMART > **oldfred said:**
>  Post 4 above ... but I don't have separate partitions for installs (didn't think that far ahead). 

Could I back-up the Hime Dir (but I have 2 users), Create several smaller Partitions, Re-Install my existing Xubuntu v18.04 to one of them, and another OS to the other smaller Partition, putting the Home directory in a bigger Partition .. all while keeping Win7 installed in its own Partition ???

---

### Post by overdrank on 2019-09-05
Hi and is a virtual machine a alternative.:)

---

### Post by oldfred on 2019-09-05
It looks like  you have one primary partition left. They do not have to be in order so sda4 could be before sda3. And then you can just shrink sda2 and add sda4. Otherwise you have to shrink sda2 & expand extended partition into unallocated, to be able to create more partitions inside the extended.

I prefer to keep /home with its mostly hidden settings in /, but even some large data files like Firefox & Thunderbird profiles I do also move to data partition. I used to have XP and had a shared NTFS data partition mostly for those profiles, but as I migrated to Ubuntu and eventually shutdown XP, data partitions are now ext4.

Generally you do not want to share /home with other installs as user settings & configurations may overlap and create issues.

I had my first issue with Firefox with my 19.10 install. Since 2006 I have shared profile across XP & many Linux installs. Not all same version, but generally regularly updated. But with 19.10 use, then it  created opening issues in my main working install 18.04. I had a backup that was only a day old, so I just restored that. Some issue about versions and noticed that profile.ini had additional lines in it.

Not tried with two users. May need two data partitions? As each user will have different ownership & permissions. And then you get into shared data between users and group permissions which I only know a little about.

---


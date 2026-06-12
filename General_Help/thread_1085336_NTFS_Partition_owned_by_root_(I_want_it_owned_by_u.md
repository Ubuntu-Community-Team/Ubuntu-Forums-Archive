---
title: "NTFS Partition owned by root (I want it owned by user)"
date: 2009-03-02
forum: General Help
---

### Post by gecko3940 on 2009-03-02
I have a dualboot (xp - hardy - swap partition - NTFS storage partition) setup. The last thing I installed onto the hard drive was hardy and swap, at sda2. 

I've noticed that the NTFS storage partition has root as it's owner, and would like to  change it to my user account. I've trawelled through the forums but to no avail - sudo chown doesnt seem to change it. Neither does changing permissions while browsing as root (they revert immediately back to root as owner). 
By unmounting the partition, I can change owner of the partition's base directory (media/Documents) but even when clicking "Apply permissions to enclosed files" while remounted, the enclosed files/folders are still owned by root. 

The problem with the current setup is I cant save Word documents (in Wine) to the NTFS storage partition, and Unison wont allow synchronizing newer files into it either.

Any ideas?

---

### Post by gecko3940 on 2009-03-05
Any help would be appreciated. As it is NTFS, I was wondering if I can even change permissions at all.... Thanks in advance.

---

### Post by r0g on 2009-08-21
Bump!

---

### Post by matthewbpt on 2009-08-21
On my system all my NTFS partitions are owned by root but I still have complete read write access to them and can mount and unmount them normally too. What version of Ubuntu are you running?

I put an entry into fstab for my NTFS partition to be mounted on boot

```
gksudo gedit /etc/fstab
```
Then added then entry
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
```
Note : you need to change /dev/sda1 to your drive partition, you can find out the value by typing 'sudo fdisk -l' into the terminal. Also /media/windows is the mount point I chose, you need to put your preferred mount point there (run 'sudo mkdir /your/chosen/mountpoint' to create the mount point).

The drive now mounted on boot and gave me complete read write permissions.

---

### Post by r0g on 2009-08-22
Hi Matthew,

Thanks for your reply. I have no trouble reading and writing as a normal user, what I have a problem with is sharing via samba - by default samba won't let you share a folder you don't own and I don't own my ntfs drive.

There is an option in samba to disable this precaution but I actually think it's a good idea security wise. The proper solution is to change the owner of my NTFS drive (actually the proper solution is to reformat the drive as EXT3 but I don't have space or time to back it up right now!).

Apparently you can do this by adding 'user' to it's parameters in fstab but I haven't tried that yet.

---

### Post by onesojourner on 2010-01-11
I need to do the same thing. How can you change the owner of a ntfs partition?

---

### Post by Morbius1 on 2010-01-11
Are you mounting the partition is fstab. If you are then add the following to the list of options: **uid=1000**. 

For example:

[B]LABEL=WinXP /windows/C      ntfs    defaults,nls=utf8,umask=007,gid=46    0    0
[/B]
Would become:

[B]LABEL=WinXP /windows/C      ntfs    defaults,nls=utf8,umask=007,[COLOR=Blue]uid=1000[/COLOR],gid=46    0    0
[/B]
To make sure you are uid=1000 type the following into a terminal: **id**

---


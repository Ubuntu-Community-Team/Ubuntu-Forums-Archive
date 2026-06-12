---
title: "Duplicate in /media"
date: 2012-10-04
forum: Desktop Environments
---

### Post by yayou on 2012-10-04
Hi everybody,

I have a problem accessing my windows partition in /media. Previously in /media I had "Donnees" witch is my windows data partition. Now in /media I have "Donnees" and "Donnees_". Donnees is empty and all my files are now in Donnees_.
In Dolphin, in the left panel (places) I still have the icone Donnees and I can acces my files this way. But some of my applications store files in Donnees and when I start them, they show that they didn't succeed to access the expected files. It's the case for Thunderbird (my profile was in Donnees) and for ktorrent.
Please, tell me how I can solve this very ambarassing problem.

---

### Post by ajgreeny on 2012-10-04
Are you storing files from your ubuntu installation's applications in your windows OS partition?  If so it is not a very good idea and it would be better to use a separate partition from windows, eg another /data partition, which can still be formatted to ntfs to allow file sharing.

Let's see the output of ```
cat /etc/fstab
``` file for a start and then ```
sudo fdisk -l
``` output. Can you also check that all the files you need and expect to be there are actually in the ntfs partition where you say they should be, then it will be easy to put everything right for you by unmounting any folders or partitions mounted at the incorrect point and  deleting the appropriate folder from /media.

---

### Post by yayou on 2012-10-05
No I use a second ntfs partition for my data, not the windows Os partition.

This cat /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=9cd27987-1ea0-4256-9384-372d8a1a3b76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=67b51faf-9a90-438c-afe5-890a3e95030b none            swap    sw              0       0

This is the sudo fdisk -l

255 têtes, 63 secteurs/piste, 14593 cylindres, total 234441648 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets
taille d'E/S (minimale / optimale)*: 512*octets / 512*octets
Identifiant de disque*: 0xd0f4738c

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *          63    41945714    20972826    7  HPFS/NTFS/exFAT
/dev/sda2        41945776   234408447    96231336    f  Étendue W95 (LBA)
/dev/sda5        41945778   181100744    69577483+   7  HPFS/NTFS/exFAT
/dev/sda6       233408448   234408447      500000   82  partition d'échange Linux / Solaris
/dev/sda7       181102592   233406463    26151936   83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque


All the data are still present exept my .thunderbird (and all my e-mail) I erase while deleting a test profile.

Thanx for your help.

---

### Post by ajgreeny on 2012-10-06
OK, now let's see the output of ```
sudo blkid -c /dev/null
ls /media
```
How are you mounting your ntfs partition; it is not in fstab so I assume you are doing it manually.

---

### Post by yayou on 2012-10-08
> **ajgreeny said:**
> OK, now let's see the output of ```
sudo blkid -c /dev/null
ls /media
```
How are you mounting your ntfs partition; it is not in fstab so I assume you are doing it manually.
Yes, just buy clicking on the icone in Places.

This is the first command output:
/dev/sda1: UUID="7CA0476CA0472BC8" TYPE="ntfs" 
/dev/sda5: LABEL="Donnees" UUID="F2F09B1BF09AE55F" TYPE="ntfs" 
/dev/sda6: UUID="67b51faf-9a90-438c-afe5-890a3e95030b" TYPE="swap" 
/dev/sda7: UUID="9cd27987-1ea0-4256-9384-372d8a1a3b76" TYPE="ext4" 
/dev/sr0: LABEL="sysrcd-1.5.8" TYPE="iso9660" 

The ls/ media:
Donnees Donnees_

---

### Post by ajgreeny on 2012-10-08
I think the easiest way for you would probably be to automount the ntfs data partition you have labelled Donnees at boot by editing your /etc/fstab file.

Firstly back up fstab with ```
sudo cp /etc/fstab /etc/fstabbackup
```then edit it with ```
kdesu kwrite /etc/fstab
```and add the line
```
UUID=F2F09B1BF09AE55F /media/Donnees/    ntfs-3g        auto,user,rw 0 0
```The kde text editor may have changed since I last used it so use whatever you now use instead of kwrite in that command.
Check all is well with command ```
sudo mount -a
```which should give no output if no errors occur.

If all this works properly we can then see if it's worth removing the Donnees_ folder from /media.

---

### Post by The Cog on 2012-10-08
I have seen this before. I suspect that it is caused by rebooting while the "removeble" media is mounted. 

This is all supposition:
When mounting removable media, the OS has to create a mount point such as /media/Donnees to mount the drive to. Normally, this folder is deleted again as the drive is unmounted. But a crash+reboot means that the folder is left there. Next time you try to mount the drive, /mnt/Donnees already exists so it can't create that folder - it creates a new one called /etc/Donnees_. 

Anyway, manually deleting the unused Donnees folder should allow the mount scripts to do their thing and recreate it next time. As has been pointed out, you may be better off making a permanent mount by editing /etc/fstab if you use that drive a lot.

---


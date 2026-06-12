---
title: "Helpful suggestion: How to automount removeable drives (Fstab settings)"
date: 2009-01-01
forum: General Help
---

### Post by bobwyajnr on 2009-01-01
Hi

For anyone else who has taken advantage of the crash in HD prices!! It can be pain if these drives aren't automounted or get mounted in the "wrong folder path"!! I am running Unbuntu 8.04.1 so can't comment on earlier versions (probably won't have native NTFS support I guess??)

Use one console window for all these commands and (K)Ubuntu will remember your password:

1) This will give you a UUID universal descriptor of all the drive partitions in your system:
```
/$ sudo blkid
...
/dev/sdm1: UUID="2EA0D96DA0D93C51" LABEL="Samsung (SATA-2)(1)" TYPE="ntfs" 
...
```
 If you have given the drives useful descriptor labels it should be painless to match up the UUID descriptors with your actual drives!!

2) Make a backup of your fstab drive descriptor file:
```
/etc$ sudo cp fstab fstab.bak

```
3) Create mount points for your drives where you want them (e.g. /media or /mnt):
```
...
/media$ sudo mkdir "S 1Tb (1)"
...
```
I make a folder "S 1Tb (1)" to mount the single partition Samsung drive /dev/sdm (partition 1).

4) Edit your fstab file:
```
/etc$ sudo vim fstab
```
Heh, heh just kidding folks!! ...
```
/etc$ sudo scite fstab &
```

5) Here is typical entry for a Desktop/Home Server installation. To mount a Windows XP/Vista NTFS partition to be shared over a LAN with Samba and rw access to all users:
```

# Samsung
UUID=2EA0D96DA0D93C51	/media/S\0401Tb\040(1) ntfs-3g rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096 0 0
```
Corresponding to the mount folder "S 1Tb (1)" created earlier. Note that a space in the mount folder is represented as a \040 (octal).

When you double click on a drive in "Places"->"Removeable Drives" to mount it Unbuntu helpfully puts an entry in your /var/log/syslog file of the command to mount it!! Helpful to determine the fstab entry for other filesystems, etc.!!

Remember that a hosed **fstab** means a hosed system!! So you need to backup the old **fstab** file and be capable of booting in from a live CD or access the partition from a Windows installation (using Ext2fsd) or other installed GNU/Linux version to restore the old **fstab** file.

Hope this wraps together information for other folks as I had to hunt around a bit for it. Especially a lot of Google hits for NTFS automounting are out of date now that Linux has full RW support in the native kernel!! :popcorn:

Bob

---

### Post by 2hot6ft2 on 2009-01-01
Applications>System Tools>NTFS-Configuration Tool

If it's not there then install it in System>Administration>Synaptic Package Manager by searching for ntfs-config and install it.

Make sure the drive you want to auto mount is UNMOUNTED then open up the NTFS-Configuration Tool then select the drive you want and click Apply in the next window select enable write support for which ever it is (internal or external) and click OK. All done

Now it will auto mount with read/write support after you reboot.

---

### Post by cariboo on 2009-01-01
Using spaces in mount point names could also lead to problems accessing the disks from the command line.

I would suggest replacing the spaces with underscores.

Jim

---

### Post by 2hot6ft2 on 2009-01-01
> **bobwyajnr said:**
> 
```

# Samsung
UUID=2EA0D96DA0D93C51	/media/S\0401Tb\040(1) ntfs-3g rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096 0 0
```
Corresponding to the mount folder "S 1Tb (1)" created earlier. Note that a space in the mount folder is represented as a \040 (octal).

The \040 shows up because you have a space in the volume name you should use an underscore instead "_" having a space will cause problems.

Change your volume label to "S_1Tb_(1)" or "S-1Tb-(1)" and it will work fine

---

### Post by bobwyajnr on 2009-01-01
> **cariboo907 said:**
> Using spaces in mount point names could also lead to problems accessing the disks from the command line.

I would suggest replacing the spaces with underscores.

Jim

Spaces work fine on the command line they just get escaped "\ " by the BASH shell... Unix has supported spaces in the path like since forever - so get a life...

Makes me lauf that I try to post a helpful comment and people just pull it part... [-X

No wonder nobody is using GNU/Linux... 	:-({|=

Bob

---

### Post by dcstar on 2009-01-01
> **bobwyajnr said:**
> Hi

For anyone else who has taken advantage of the crash in HD prices!! It can be pain if these drives aren't automounted **or get mounted in the "wrong folder path**"!! I am running Unbuntu 8.04.1 so can't comment on earlier versions (probably won't have native NTFS support I guess??)
........

Or you simply give individual volume labels to any partition on your external drive and they will **always** be mounted using those names without any mucking around with the fstab file.

As far as automounting goes, that should work anyway and if it doesn't, then there is usually a good reason why.

---

### Post by bobwyajnr on 2009-01-02
> **2hot6ft2 said:**
> 
Applications>System Tools>NTFS-Configuration Tool

If it's not there then install it in System>Administration>Synaptic Package Manager by searching for ntfs-config and install it.

Ah yes this seems to work... Thanks for the great suggestion!!

Sorry 'bout my rant yesterday... Just come off a night shift hence not in the best of moods!!

Bob

---


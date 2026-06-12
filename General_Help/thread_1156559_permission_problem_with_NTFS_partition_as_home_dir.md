---
title: "permission problem with NTFS partition as home dir"
date: 2009-05-11
forum: General Help
---

### Post by jt_04 on 2009-05-11
I want to use a NTFS partition as my home directory.  I've mounted the partition into /home and even overcame the annoying terminal color scheme for NTFS ([see here]("http://ubuntuforums.org/showthread.php?p=4779749")).  

my problem is that all the files I copied to the ntfs partition have root permissions instead of my user permissions.  even if i create a file with "touch tmp", the tmp file shows "root root" when I do a ls -l.

will this be a problem for me?  how can i keep my local user permissions?

any help is appreciated!

jt

---

### Post by taurus on 2009-05-11
Are you sure you really want to use ntfs filesystem for your $HOME?  That is a real bad idea.

---

### Post by AnimeFreak on 2009-05-11
i have the same issue but my drive is a secondary 1 its called HotSpot and it says

 "i do not have the privilage of mounting it"

---

### Post by AnimeFreak on 2009-05-11
> **AnimeFreak said:**
> i have the same issue but my drive is a secondary 1 its called HotSpot and it says

 "i do not have the privilage of mounting it"
  


bump

---

### Post by taurus on 2009-05-11
> **AnimeFreak said:**
> i have the same issue but my drive is a secondary 1 its called HotSpot and it says

 "i do not have the privilage of mounting it"

> **AnimeFreak said:**
> bump

Post the outputs of these commands from a terminal then.

```
sudo fdisk -l
df -h
```

---

### Post by AnimeFreak on 2009-05-11
> **taurus said:**
> Post the outputs of these commands from a terminal then.

```
sudo fdisk -l
df -h
```

sorry i am confused i am kinda new to ubuntu  

this is what i get after i type in those 2 lines

```
root@animefreak-desktop:/home/animefreak# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf732f732

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36ed36ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)
root@animefreak-desktop:/home/animefreak# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   34G   34G  51% /
varrun                744M  112K  744M   1% /var/run
varlock               744M     0  744M   0% /var/lock
udev                  744M   84K  744M   1% /dev
devshm                744M   56K  744M   1% /dev/shm
lrm                   744M   40M  704M   6% /lib/modules/2.6.24-24-generic/volatile
/dev/sdc1             150G  148G  1.7G  99% /media/My Book
root@animefreak-desktop:/home/animefreak# 

```

---

### Post by Locutus_of_Borg on 2009-05-11
if i recall correctly, ntfs does not support permissions.  at least not the same as other file systems

also, why on earth would you use an unstable file system to house anything let alone your personal files?

---

### Post by days_of_ruin on 2009-05-11
> **AnimeFreak said:**
> sorry i am confused i am kinda new to ubuntu  

what commands and what is the code for

Applications->Accessories->Terminal

then copy and paste.

But using ntfs seems a like a really bad idea and probably won't even
work with linux.

---

### Post by taurus on 2009-05-11
> **AnimeFreak said:**
> sorry i am confused i am kinda new to ubuntu  

this is what i get after i type in those 2 lines

```
root@animefreak-desktop:/home/animefreak# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf732f732

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36ed36ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)
root@animefreak-desktop:/home/animefreak# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   34G   34G  51% /
varrun                744M  112K  744M   1% /var/run
varlock               744M     0  744M   0% /var/lock
udev                  744M   84K  744M   1% /dev
devshm                744M   56K  744M   1% /dev/shm
lrm                   744M   40M  704M   6% /lib/modules/2.6.24-24-generic/volatile
/dev/sdc1             150G  148G  1.7G  99% /media/My Book
root@animefreak-desktop:/home/animefreak# 

```

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by AnimeFreak on 2009-05-11
> **taurus said:**
> ```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

thank u thank u i have ben messing with this for a month now and it is finally fixed thank u thank u

---

### Post by jt_04 on 2009-05-12
> **taurus said:**
> Are you sure you really want to use ntfs filesystem for your $HOME?  That is a real bad idea.

well it seemed like a good idea at the time...i want to be able to access my files when i boot up in windows.  

i've got 3 partitions -- 2 small ones with windows and ubuntu, with the 3rd partition being 500 GB. i figured i'd mount that as home and that way i can still see my files in windows.

can someone explain to me why ntfs is so bad?  if it's microsoft, i'm sure it is bad, i just don't know why.

---

### Post by jt_04 on 2009-05-13
bump.  anyone?  why is ntfs so bad?

---

### Post by michy99 on 2009-05-13
Ntfs is ok for storing files that you also want to access from Windows. The problem with making your /home partition ntfs is that it doesn't support linux permissions. Your /home partion has a lot of hidden folders containing configuration files and other goodies for the programs you use. Some of these need to have specific permissions set.

The best setup is /home as ext3 (or ext4 if you're adventurous) and have a separate ntfs partition for any files you want to share with Windows.

---

### Post by bodhi.zazen on 2009-05-13
> **michy99 said:**
> Ntfs is ok for storing files that you also want to access from Windows. The problem with making your /home partition ntfs is that it doesn't support linux permissions. Your /home partion has a lot of hidden folders containing configuration files and other goodies for the programs you use. Some of these need to have specific permissions set.

The best setup is /home as ext3 (or ext4 if you're adventurous) and have a separate ntfs partition for any files you want to share with Windows.

+1 

Just because Ubuntu (linux) can read / write NTFS does not mean you  can use it for a /home partition.

The problem is NTFS does not support permissions.

---

### Post by WIGGMPk on 2009-05-13
> **jt_04 said:**
> bump.  anyone?  why is ntfs so bad?

bodhi.zazen & michy99 are correct, not to mention that ntfs-3g (read/write support for NTFS in Linux) is completely reverse engineered due to the fact that NTFS is completely proprietary.

Even though I have never heard of any recent bugs with NTFS-3G it would still NOT be a good idea to use it as a /home directory even if you could.

---

### Post by jt_04 on 2009-05-13
> **michy99 said:**
> Ntfs is ok for storing files that you also want to access from Windows. The problem with making your /home partition ntfs is that it doesn't support linux permissions. Your /home partion has a lot of hidden folders containing configuration files and other goodies for the programs you use. Some of these need to have specific permissions set.

The best setup is /home as ext3 (or ext4 if you're adventurous) and have a separate ntfs partition for any files you want to share with Windows.

makes sense, thanks.

i guess i didn't know much about it, so when i first installed ubuntu i formatted my ubuntu partition as ext2.  should I reformat to ext3?  what are the benefits of ext3 over ext2?

---

### Post by aboud on 2010-01-01
well then ., is there a ext3 driver to access ext3 from windows ?

---

### Post by bodhi.zazen on 2010-01-01
> **aboud said:**
> well then ., is there a ext3 driver to access ext3 from windows ?

Yes, there is:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

To be honest, I suggest you use a shared NTFS partition, no real need to make the shared partition /home =)

---

### Post by airbag on 2010-01-02
i was told that NTFS as problems w/ files over ~4GB. is that true?

---

### Post by HiImTye on 2010-01-02
FAT32 is limited to 4GB file size, NTFS is not

---


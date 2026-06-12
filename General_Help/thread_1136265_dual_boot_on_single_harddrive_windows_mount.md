---
title: "dual boot on single harddrive windows mount?"
date: 2009-04-24
forum: General Help
---

### Post by jblinuser on 2009-04-24
can anyone tell me how to mount my windows file system so that i can access my windows files in ubuntu?:) also i would like to know how to make it so that it automaticaly creates an icon on the desktop so that i have an easy way to access it.

---

### Post by soro2005 on 2009-04-25
Is it not listed under "Places"? Possibly as XYZ GB Media with XYZ being the size of the partition. If it's there, you can make a desktop icon by just dragging the entry onto the Desktop. If not, then you could give a little more detail. Are you trying to mount the Windows system partition? What Windows version? What's the output of
```
sudo fdisk -l
```
What is the output of
```
cat /etc/fstab
```

---

### Post by Dr_Willis on 2009-04-26
When installing, its often easy to over look  on the partition manager tool the mountpoints for existing windows partitions. 
You can easially add new fstab lines for the various windows partitions.  

This has got to be one of the most documented 'things' ive seen for linux. Heres a few example fstab lines for my system,

Lines from my /etc/fstab (windows on first hard drive)


# /media/Storage was on /dev/sda2 during installation
UUID=2253169A33E2F7BF /media/Storage  ntfs    Defaults,nls=utf8,umask=007,gid=46
 0       1
# /media/Windows7 was on /dev/sda1 during installation
UUID=28CD8DAC475B7D8E /media/Windows7 ntfs    defaults,nls=utf8,umask=007,gid=46


 the UUID part is the special UUID (unique ID) number for the partition.  The old fashioned way would be to use /dev/sda1 for example. see 
[https://wiki.ubuntu.com/LibAtaForAtaDisks](https://wiki.ubuntu.com/LibAtaForAtaDisks) for the rationale behind the transition to UUID


You can determine the UUID of your filesystems with the  command

** sudo blkid**

 One thing to rember with NTFS and VFAT  Is that the permissions must be set at mount time. You dont 'chmod' files on ntfs or vfat filesystems

You may also want to use the 'ntfs-3g' filesystem instead of NTFS of you want write permission to ntfs filesystems.

 sudo apt-get install ntfs-config
 gksu ntfs-config (check the 2 check box's to allow writing)

This changes the fstab lines as follows (in my example)
# Entry for /dev/sda2 :
UUID=2253169A33E2F7BF /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda1 :
UUID=28CD8DAC475B7D8E /media/Windows7 ntfs-3g defaults,locale=en_US.UTF-8 0 1


Good Luck! If this is unclear - i think theres several wiki pages on the topic s well.

:popcorn:

---


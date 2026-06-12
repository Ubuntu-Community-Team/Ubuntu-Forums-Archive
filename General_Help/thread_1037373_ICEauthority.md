---
title: "ICEauthority"
date: 2009-01-11
forum: General Help
---

### Post by Neondog82 on 2009-01-11
I get an error "could not update ICEauthority file /home/username/.ICEauthority

I recently moved my /home directory to a FAT32 partition. I don't get any errors except the one above. my FSTAB looks like this: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=95dbdc06-0781-42ac-b602-f7365f642f53 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=e2078a16-4cc8-4173-9628-077a09c14ad1 none            swap    sw              0       0

# /dev/sda6 HOME PARTITION
/dev/sda6 /home vfat uid=1000,gid=1000
```

i have tried to boot into repair droped to root and run these commands:

```
sudo chmod 644 /home/username/.ICEauthority
sudo chown username:username /home/username/.ICEauthority
```

but that does not work. Any help would be much appreciated.

---

### Post by caljohnsmith on 2009-01-11
Unfortunately you can't have your home folder on a FAT partition because the FAT file system does not support permissions and ownership metadata for files. Thus you would get an error exactly like you are experiencing. You could either make your home partition ext3 or some other linux file sytem, or another option is to put your home directory back with your main install, yet put your personal documents folders (Videos, Pictures, Music, etc) on the FAT partition. Then you could use a "symbolic link" to link the those folders back to your home directory. Does that sound like something you would want to try?

---

### Post by Neondog82 on 2009-01-11
Dude, you mean to tell me I spent all day trying to make this work and it can't? That suxs. Thank you for the help. I thought the perfect dual boot setup had a partition for each OS and a shared partition for user specific data? Would NTFS work? I suppose I could try the symbolic link business. Again, thank you for your help

---

### Post by albinootje on 2009-01-11
> **Neondog82 said:**
> Dude, you mean to tell me I spent all day trying to make this work and it can't? That suxs. Thank you for the help. I thought the perfect dual boot setup had a partition for each OS and a shared partition for user specific data? Would NTFS work? I suppose I could try the symbolic link business. Again, thank you for your help

FAT is from the DOS times, it's a single user file system.. 
(Did I say evil ? No, I didn't. Did I say security hazard ? No, I didn't :) )

Using /home with NTFS is likely not gonna be working well too!

Much better is the use ext3 for Linux, and have MS-Windows use software like this to access those :
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

Another option is to only share the *data* on FAT or NTFS.
The thing with /home is that you need real "UNIX" style permissions for at least some of those special hidden files and the configuration files.

GL!

---

### Post by caljohnsmith on 2009-01-11
> **Neondog82 said:**
> Dude, you mean to tell me I spent all day trying to make this work and it can't? That suxs. Thank you for the help. I thought the perfect dual boot setup had a partition for each OS and a shared partition for user specific data? Would NTFS work? I suppose I could try the symbolic link business. Again, thank you for your help
You could use NTFS for your shared data partition, but like I mentioned and albinootje did too, just make sure your actual home folder is located on a partition that uses a Linux file system. If you want to use symbolic links, you can do something like:
```
ln -s /path_to_shared_partition/Videos ~/.
```
That would link the "Videos" folder on your shared partition to your home directory, but you would first have to get rid of the current Videos folder in your home directory. If you would like more specific help, please post the output of the following command once you get your shared partition set up:
```
sudo fdisk -lu
```
And let me know if you have a preference where to mount it and what you want the directory to be called. But good luck and let us know how it goes.

---

### Post by Neondog82 on 2009-01-11
Thank you for the guys. I can't believe I thought that was a viable option. I guess I will just put the data back with the OS or in seperate data partitions. Again, thank you for the help.

---


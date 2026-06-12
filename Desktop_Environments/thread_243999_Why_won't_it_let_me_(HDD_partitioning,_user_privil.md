---
title: "Why won't it let me?? (HDD partitioning, user priviledges issues)"
date: 2006-08-25
forum: Desktop Environments
---

### Post by mozza314 on 2006-08-25
Something recently happened to my X server and it wouldn't start. Didn't really know what to do, so I used an ubuntu live cd to access my HDD and back up my stuff and decided to re-install.

Anyway, I have two 20gig HDDs in my computer, one with Windows, one with Ubuntu. When I decided to re-install, I thought I might use some better partitioning, and use one HDD for storage that could be accessed by both OS's, and put two 10gig partitions on the other HDD, one with Windows, one with Ubuntu.

My computing teacher recommended NTFS, because windows can easily read it etc. The first problem I came across was that when I formatted the hard disk (the one with the broken linux) with NTFS, I couldn't read/write to it. I tried it with the root user, and I could read, but not write, tried editing the permissions, and it said I couldn't change it because it was a read only disk. (I never thought I'd have problems with the root user, my understanding was that the root user has permission to do anything).

So instead I formatted it as fat 32, as windows should be able to handle it since it is it's normal format, and I have been successfully accessing my windows stuff through linux. In fat 32, I could read but not write in the normal user, and could read and write in the root user.

Another problem was that I couldn't resize the windows partition to put ubuntu on that HDD, so I ended up putting ubuntu on the HDD that I just explained about formatting as fat 32. Although I kept a 6gig fat 32 partition on that HDD, in the hope of putting my documents in there from ubuntu so windows could read it.

So here's my current partitioning:

hda:
20gig: Windows (fat 32)

hdb:
6gig: Empty fat 32 (actually it has some backup data on it)
14gig: Ubuntu (re-installed) (Ext 3)


Why did the NTFS partition show up as read-only and not allow even the root user to write to it? How do I stop this?
Why did the fat 32 partition only allow the root user to write, and did not allow the root user to change the permissions so the normal user could write?
How do I resize the the Windows partition? Can this be done without re-installing Windows? (XP Pro)

Ultimately I still want to have two 10gig partitions on one HDD with the operating systems installed, and have the other HDD for all the documents with both OS's able to access them. I intend to do this with NTFS, but if there is an easier format to use to achieve this, I don't mind.

Help!

---

### Post by mssever on 2006-08-25
The important thing to understand about Windows file formats is that they are incompatible with Linux permissions. So setting permissions on a file in a Windows partition will never work, even if you're root. The only way to set permissions on NTFS and FAT32 is through mount options--usually via /etc/fstab.

There are several things to note in the options column (usually contains "defaults" plus possibly other stuff. If it says ro, that means read-only, and noboby--not even root--can write to it until the partition is remounted with differend options. The opposite of ro is rw. uid=1000 (or whatever) and gid= set the effective owner's userid and groupid for the entire partition. umask sets the umask for all the files. For example, umask=022 will give full control to the owner and block write access to everyone else.

As an example, here's a line from my fstab:
```
/dev/hda1       /media/hda1     ntfs            defaults,nls=utf8,umask=007,gid=46,ro   0       1
```
I specifically added the ro because I didn't want to risk data loss in writing to an NTFS filesystem under Linux.

---

### Post by mozza314 on 2006-08-26
Oh ok, that explains a bit, is there any way to do that from "Disks" (the app in System -> Administration -> Disks)?

If not, what exactly would I have to put in terminal to mount it with full permissions to the normal user? (It's the 1st partition on hdb, does that mean it's hdb1?)

atm it is a fat32 partition, would mounting a fat32 partition be the same as mounting an NTFS partition only swapping "NTFS" with "fat32"?

Also, is there any way to make it mount in a specific way on startup?

---

### Post by mozza314 on 2006-08-26
Just re-posting to get the thread back up so people will read it, I really don't know what to do please help.

---

### Post by mssever on 2006-08-26
> **mozza314 said:**
> Oh ok, that explains a bit, is there any way to do that from "Disks" (the app in System -> Administration -> Disks)?Dunno. I find the command line to be easier (and more familiar), so I've never used those tools.

> If not, what exactly would I have to put in terminal to mount it with full permissions to the normal user? (It's the 1st partition on hdb, does that mean it's hdb1?) Something like ```
sudo mount -t vfat -o defaults,utf8,umask=007,gid=46 /dev/hdb1 /media/hdb1
``` but see below for an easier way. Also, note that the mount point (/media/hdb1 in this example) must: exist, be a directory, and be empty.

> atm it is a fat32 partition, would mounting a fat32 partition be the same as mounting an NTFS partition only swapping "NTFS" with "fat32"? Basically, yes. But note that Linux calls FAT32 vfat, and you use ntfs in lowercase. Also, vfat is much better supported in Linux than ntfs.

> Also, is there any way to make it mount in a specific way on startup? You do this by editing /etc/fstab. Each partition that you might want to mount more than once should have a line in this file--which also keeps you from having to type(and remember) long command lines. Do something like this:
```
/dev/hdb1       /media/hdb         vfat    defaults,utf8,umask=007,gid=46 0       1

``` If there is any device that you **don't** want to be mounted at startup, add the noauto option. Otherwise, everything will be automatically mounted.
Use the following commands to manually mount/unmount stuff listed in fstab, where x is either the device name OR the mount point:```
sudo mount x
sudo umount x
```

---

### Post by mozza314 on 2006-08-27
Wow! Thanks sooooooooo much! It worked perfectly! :D

Just a couple of further questions though:

Do you know how I can rename the volume to "Documents" or something? Or better yet to just remove it from my desktop because it doesn't look very nice there called "hdb1".

Also, my earlier question about the Windows partition, do I have to reinstall to get it on a smaller partition or is there an easier way?

---

### Post by mssever on 2006-08-27
If you want to remove the icon from your desktop, you should be able to just delete it. You can name your mount point anything you want (within reason) as long as fstab point to the right place. In fact, you can put it anywhere you want in the filesystem. This is much more flexible then the Windows drive letter system. For example, you could create an empry folder in your home directory (or on your desktop) and point fstab there. Then, your partition will live there, instead of at /media/hdb1.

About your other question: I don't know if there's an easier way. I hope so. I've heard about something called LVM that makes partitions easily resizable, but I don't know how to set that up.

EDIT: If all you want to do is resize your Windows partition, that can be done. The Ubuntu installer did that for me automatically when I didn't ask it to! Seriously, though, I think the tool you want is ntfsresize. Type ```
man ntfsresize
``` for documentation.

---


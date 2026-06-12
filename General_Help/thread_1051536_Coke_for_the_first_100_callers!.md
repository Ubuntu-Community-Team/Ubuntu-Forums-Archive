---
title: "Coke for the first 100 callers!"
date: 2009-01-26
forum: General Help
---

### Post by RemyArgo on 2009-01-26
Hey,

So I'm making the leap from Vista (due to over a year of unawesomeness) to Ubuntu. Need advice.

Right now, my HD is a mess due to neglect and Windows/VAIO "foresight." Anyhow, so I'm planning on doin a reboot to do a clean slate sort of deal, a partition of the primary drive, then a dual boot of Vista and Ubuntu. (I heard that it is useful to have windows somewhere and my vaio didnt come with a backup disk. just a partitioned "recovery" drive. ~8GB in a 120 GB HD) I also wanna make a third (or 4th, technically speaking) partition for common files. 
Anyhow, my questions
 - are partitions mutually exclusive (can i access the common files on partition X from Ubuntu and Vista, and if so, how?)? also, are files writable/rewritable across partitions ? (ie i want to save that HAWT new timberlake song in the common area, but want to play it using iTunes.)
 - How much space should I allocated/partition (basically, is it a good idea to give both OS a little space and have everything done/store in the third partition?)? - I'm tryin to figure out what ratios would be best (ie [and this is purely hypothetical, so don't bite off my head] 10 GB or Vista, 10 GB for Ubuntu, 92 GB for Common)
 - I've made a recovery dvd(s) of the Vista. Any need for that separate partition (backup) anymore? I know its easier on the bios, but I think I'd rather just scribble down the necessary info and use the space.

Thanks!

---

### Post by RemyArgo on 2009-01-26
O, and don't mind my non-techie speak....I'm really green (to all this)
So thanks for putting up with my....uhh....yeah

---

### Post by jerome1232 on 2009-01-26
> **RemyArgo said:**
> Hey,

So I'm making the leap from Vista (due to over a year of unawesomeness) to Ubuntu. Need advice.

Right now, my HD is a mess due to neglect and Windows/VAIO "foresight." Anyhow, so I'm planning on doin a reboot to do a clean slate sort of deal, a partition of the primary drive, then a dual boot of Vista and Ubuntu. (I heard that it is useful to have windows somewhere and my vaio didnt come with a backup disk. just a partitioned "recovery" drive. ~8GB in a 120 GB HD) I also wanna make a third (or 4th, technically speaking) partition for common files. 
Anyhow, my questions
 - are partitions mutually exclusive (can i access the common files on partition X from Ubuntu and Vista, and if so, how?)? also, are files writable/rewritable across partitions ? (ie i want to save that HAWT new timberlake song in the common area, but want to play it using iTunes.)
 - How much space should I allocated/partition (basically, is it a good idea to give both OS a little space and have everything done/store in the third partition?)? - I'm tryin to figure out what ratios would be best (ie [and this is purely hypothetical, so don't bite off my head] 10 GB or Vista, 10 GB for Ubuntu, 92 GB for Common)
 - I've made a recovery dvd(s) of the Vista. Any need for that separate partition (backup) anymore? I know its easier on the bios, but I think I'd rather just scribble down the necessary info and use the space.

Thanks!

First try to use descriptive topic titles, I veiwed this post to report it for spam but it's obviously not spam :), you can report your own post and request a title change to something more descriptive.

Microsoft uses the nt file system and the fat file system. Ubuntu has the ability to read and write to ntfs and fat volumes.

Linux has a multitude of file systems available but the most prevalent by far is the ext3 file system. Windows can use third party drivers to read and write to ext2 (ext3 can be used as ext2, it just means there's no journal so if the computer crashed it's more likly to cause file system corruption)

Most people will have the os's on their separate partitions and create a 3'rd partition as fat or ntfs and store all of their multimedia and other data they would like to share across operating systems there.


I dont' think 10 GB will be enough for vista, I would personally go with at least 20 or 30. Ubuntu will do fine on 10 GB as long as your storing your personal files on another data partition. I would probably still go with 20 GB if you plan on installing alot of programs.

---

### Post by mb_webguy on 2009-01-26
I'm currently dual-booting Vista and Ubuntu.  Vista resides on a 25GB partition, of which I'm using almost 20GB and only have Office, Visual Studio, and a few small applications like Firefox, VLC, and Winamp installed.  Ubuntu is currently installed on a 12GB partition, of which I'm using 6.6GB even though I have a huge amount of software installed.

I think 25GB is a good size for Vista unless you're a gamer, in which case I'd bump it up to 30GB.  An 8 or 10GB partition is sufficient for Ubuntu.  I'd also suggest a small separate /home partition for Ubuntu.  This lets you reinstall Ubuntu if you need to without losing your settings.  I have a 2GB /home partition, of which I'm using 1.5GB mostly because I have Office 2003 installed under Wine.  I also have a swap partition equal in size to my system memory (2GB) so that I can put my computer into hibernation mode if I want.  Some people prefer to use a swap file instead of a swap partition so they don't have to dedicate that hard drive space for swap, but I have two 150GB hard drives in this computer, so I don't really miss that 2GB.

The rest of your drive can be devoted to a shared partition, which should be either ntfs or ext3.  Ubuntu has good native support for ntfs, but if you use ntfs, the entire partition will be mounted with a given owner, group, and set of permissions, and you won't be able to set them for specific files or directories.  Windows, on the other hand, has no native support for ext3, but can use the [ext2ifs]("http://www.fs-driver.org/") driver to read and write to an ext3 partition as ext2 (which, as jerome1232 said, simply means it can't do journaling on the ext3 filesystem).  I don't think Linux can do journaling in ntfs, so it works both ways.  Personally, I think it's better to format the shared partition as ext3 and use the ext2ifs driver in Windows.  File permissions are much more important in Linux than in Windows.

A few more tips...  

Install Windows first.  The Windows bootloader doesn't recognize any non-Windows operating systems, so if you install Ubuntu first and then Windows, you'll have to reinstall the GRUB bootloader to regain access to Ubuntu.  

Also, one nice feature about Vista is that it's extremely easy to move the location of your user folders in the folder properties dialog, so you probably want to move them to the shared partition.   

Likewise, you should delete the folders in your Ubuntu home directory (e.g. Documents, Videos, Pictures, etc.), and add symbolic links to the corresponding directories on the shared partition, since whether or not you use a separate home partition, you're going to have limited space in your home directory.  

And no, you *don't* want to simply use the shared partition as your Ubuntu home directory, since that would expose all of your Ubuntu user configuration files to Windows.  You should expose one operating system to the other as little as possible to avoid accidentally damaging one from the other.  This also means you don't want to mount your Windows partition in Ubuntu, or your Ubuntu partition in Windows.

---

### Post by RemyArgo on 2009-01-27
Thanks for the input! It surprisingly helped

Well, update - I just spent the last 3-4 hours rebooting the Vista via burned recovery disk. An hour of it was spent installing programs that I'm currently in the process of uninstalling. It's been 30 mins since. I don't plan on finishing this task tonight. Love it

---


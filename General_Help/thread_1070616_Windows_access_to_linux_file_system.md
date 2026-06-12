---
title: "Windows access to linux file system"
date: 2009-02-15
forum: General Help
---

### Post by davidself1001 on 2009-02-15
I have tried the ext2ifs driver in Windows but have not been able to get it to work.  I have tried it in XP and in Windows 7 x64.  I was able to add a disk drive letter but when I try to open the disk I get a "needs to be formatted" prompt.  I have tried two different versions of the driver but both give the same result.  The reason given for the format is that the inode size is 256 on the drives and needs to be 128.  I have tried a number of utilities that allow you to explore the linux drives but none of them have worked either.  Anybody have this working and can provide details on how to do so?

---

### Post by Yellow Pasque on 2009-02-15
The better question is: why would you want to do this? If you need to share data across OS's, why not use a commmon NTFS partition for that data?

---

### Post by spiderbatdad on 2009-02-15
Is Putty through ssh what you are looking for? [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
Of just the ability to share files?

---

### Post by davidself1001 on 2009-02-15
Just want to share files.  What I want is to have a data disk that contains my /home dir and have that show up as a D: drive in windows.  How do I do that?

---

### Post by scooper on 2009-02-15
I assume you want to access files on Linux partitions when booted to Windows on the same machine, and that you probably don't have spare partitions to use NTFS or FAT32 for sharing.  I wouldn't use NTFS for an important partition which is used for more than sharing in Linux.  And you can't use SSH if Linux doesn't run in parallel, i.e. on another machine.

For simple individual file copying from an EXT3 partition into Windows I use the Total Commander file manager (totalcmd.net).  It's not free, but it's great and has a plug-in for EXT3 filesystem access.

For larger scale sharing I do use a FAT32 or NTFS partition that both systems can access.  For example, my MP3/OGG files go there so that I can listen to my tunes on either Linux or Windows.  If you have extra space for a sharing partition, I would seriously consider doing this.

I haven't had an issue with the ntfs3g driver in Linux.  It's been working great for both reading and writing.  The only issue is that if you improperly shut down Windows it may refuse to mount in Linux until you let Windows check the filesystem.  That doesn't happen too often.

Another option may be to install colinux or andlinux, which provides a full Linux running a special kernel right inside Windows.  It seems that it can mount physical partitions as long as Windows doesn't give it a drive letter.  You may want to check out the [colinux wiki]("http://colinux.wikia.com/wiki/Main_Page").  You could use Samba to share any mounted EXT3 partitions to make them available to Windows.  Or if you prefer, you could mount shared Windows partitions in colinux and push the files to Windows.  The caveat is that I have tried, but never extensively used colinux/andlinux.  It seems to work, but I haven't ultimately needed it.  It didn't cause any problems and is easy to uninstall.  I keep mentioning andlinux, because it's an easier-to-install Ubuntu distribution of colinux.  I'd look at both.

---

### Post by Sorivenul on 2009-02-15
You may be interested in the [FS-driver project]("http://www.fs-driver.org/").

It should allow what you are looking for as far as accessing information on an ext2 or ext3 partition.

---

### Post by davidself1001 on 2009-02-15
Ok.  I just created an NTFS partition and I can get to it from both Windows and Ubuntu so I am happy.  I was trying to make it too difficult I think.

---

### Post by bodhi.zazen on 2009-02-15
IMO you are best off making a shared (ntfs) data partition. Mount it where you like in windows.

You can not use ntfs as /home, so mount it at say 

/home/user/data

---


---
title: "Unable to change permissions in Ubuntu 22.04 LTS"
date: 2022-10-30
forum: Desktop Environments
---

### Post by tapasray on 2022-10-30
I am unable to change the permission settings of any folder on an NTFS partition. All three -  Owner ("Me"), Group (my name), and Others - are set at "Create and Delete Files". I have restarted the machine in normal mode, and also in recovery mode. Neither has helped. 

This is a security issue and I am concerned. I would really appreciate some help here. 

Thanks in advance.

---

### Post by oldfred on 2022-10-30
You cannot change permissions & ownership of Windows formats like NTFS or FAT32.
You set defaults when you mount those partitions.
You should only use NTFS if you are dual booting with Windows as it will need chkdsk or defrag which only can be done from Windows.
Also Windows turns fast start up which sets a hibernation flag. And it turns it back  on with updates. Then partition will be read only, and default of read/write will not mount.

Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
exfat example - TheFu
[https://ubuntuforums.org/showthread.php?t=2479368&p=14113300#post14113300](https://ubuntuforums.org/showthread.php?t=2479368&p=14113300#post14113300)
ext4 example - TheFu
[https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000, windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by tapasray on 2022-10-30
Thanks you so much for your detailed response, @oldfred. Greatly appreciated. Apologies for the late reply. I was sleeping, as it was night here. 

Indeed, I had set this partition as NTFS as this machine had Windows 10 factory-installed. I had installed Ubuntu in a dual-boot mode and this partition was for data that I needed to read and write in both OSs.

What you have written will take a little time to sink in, but I'm sure I will get it eventually. 

Thanks again.

---

### Post by ActionParsnip on 2022-10-31
NTFS can't hold Linux ACLs. You need to specify the ACL at mount time. You can't chmod / chown on NTFS. It isn't a Linux file system

---


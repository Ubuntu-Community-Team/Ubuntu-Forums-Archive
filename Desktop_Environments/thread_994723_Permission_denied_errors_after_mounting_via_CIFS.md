---
title: "Permission denied errors after mounting via CIFS"
date: 2008-11-27
forum: Desktop Environments
---

### Post by nataku1 on 2008-11-27
My desktop is running Ubuntu 8.10, I'm trying to connect to my D-Link DNS-323 (NAS) that has some shares in Samba.

I can mount and modify files on the DNS-323 from my Windows machines here, but cannot with Ubuntu.

I've tried to mount them manually with
mount -t cifs //DNS323/Volume_1 /home/USER/vol1 -o user=USER,password=PASSWORD

It lets me mount the volume, but I can't read the contents in there.  Permission denied error.

If I access it via:

Places > Network > Windows Shares > DNS323 > Volume_1 > put my username, password, and leave Domain set to WORKGROUP > connect

It works, I can read the contents, copy the data in and out of there.

What is different about mounting the volume and access it via the Places > Network menu?

I've tried specifying the domain in the mount command:
mount -t cifs //DNS323/Volume_1 /home/USER/vol1 -o user=USER,password=PASSWORD,domain=workgroup

That mounts the volume, but when I read the contents, I get a permission denied error.

I've made sure the username and password I've entered is correct, and I have the same thing entered on my NAS.  I can SSH into my NAS using the same username and password, and freely modify the files within there, so it's not a permission problem on the NAS.

No samba logs are being generated at all.

Any ideas on what I'm missing?

Thanks

---

### Post by nataku1 on 2008-11-28
I forgot to comment on the fact that I'm not sure if this is the right place to ask this, if there's a better category for my issue, please let me know

---

### Post by nataku1 on 2008-12-03
any ideas?

---

### Post by jbutler08@embarqmail.com on 2008-12-04
I think I know the Answer Just tring to fix it. If you places and goto network, I can browse my Openfiler Nas and it mounts to the desktop, from the Command line or FS Tab it show on the desktop and says permission denied. When I run This as root at a command line 

mount -t cifs //saint/storage.netstore.Music -o username=user,password=pass /media/music

it works if I browse as root at the command line to the folders, but remember I am root at the command prompt. Once I goto the desktop and click on the the music folder that is mounted it says permission denied.

I know what it is I just have corrected my mount command yet.

It has something to do with uid or gid being added to the command line to allow other users besides root to access the mount point. I hope to figure it out soon. I know now I am on the right track.

---

### Post by cyberbill on 2008-12-10
Hey guys,
  Surprise, I'm actually having a similar problem. I am using a WD World Edition and have successfully mounted and can create and read files, but cannot modify existing files or even the new ones after creation.

My mount command:
```
sudo mount -t cifs -o rw,noperm,user=WORKGROUP/USER%PASS,iocharset=utf8,file_mode=0777,dir_mode=0777 //IP_ADDRESS/PUBLIC /mnt/wdw-1t/public
```

when trying to edit a file, say with nano, I get the following error:
> Error writing test.file: Not a directory

output from "ls -al test.file":
```
-rwxr--r-- 1 www-data www-data 5 2008-12-09 23:53 test.file
```

attempting to chmod file to add write permissions:
> chmod: changing permissions of `test.file': Not a directory


Thoughts?
-cb

---

### Post by cyberbill on 2008-12-10
Following [this thread]("http://ubuntuforums.org/showthread.php?t=288534"), I have gotten my permissions fixed.

After looking around, I found the "not a directory" issue is due to a [samba and kernel bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828") which is being worked on. There will be a "nodfs" option to add to the mount command for those who are unable to upgrade the samba in the NAS. I just got the drive and am not keen on bricking it just yet. ;-)

-cb

---

### Post by nataku1 on 2008-12-12
THANK YOU!  I actually read that thread before, but I didn't notice the first time the section for "Files owned by root. If you can view but not change, delete, or add new files to your Samba share, try this fix:"

After adding the gid, uid, and nounix parameters to my mount options, everything worked!

Prior to this, there was a few smb.conf parameters I needed to change, but it's all working now :)

---

### Post by cyberbill on 2008-12-12
No problem, only took about four hours of searching the forums. ;) 

This thread is the one that popped up right away for me, so hopefully that helps others find the how-to thread.

-cb

---

### Post by jeremy on 2009-05-23
DNS-323 1.08 beta firmware at:

[http://forums.dlink.com/index.php?topic=5485.0](http://forums.dlink.com/index.php?topic=5485.0) 

Lots of fixes and features including NFS support!

---

### Post by nataku1 on 2009-07-11
Wow!  I have been waiting for NFS support on the DNS-323, and as you said there's tons of fixes in here.

Thanks Jeremy!

---


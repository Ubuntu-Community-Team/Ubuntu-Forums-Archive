---
title: "question"
date: 2005-02-17
forum: Desktop Environments
---

### Post by lorap on 2005-02-17
i've mounted some folders from fat32 partition, but can't change ownership from root to myself, regardless using chown -R username /home/username/directory.
why is that?
i'd be very happy if somebody help me solve this trouble.
thanks.
pavel

---

### Post by Wim Sturkenboom on 2005-02-17
Hi Lorap, 

you can not change that (to my knowledge) the way you're trying it. It's defined in /etc/fstab. My line for a fat32 partition ooks like:
```
/dev/hda2  /windata  /vfat  auto,uid=1000,gid=1000,umask=007  0  0
```The uid and gid define the user and group who have the access.

I would suggest that (in future) you use a title that describes your problem when you start a thread instead of using **Question** or **Help**. Most of the time, you will have a question or you will need help when you start a thread.

At the time of writing this, you have two threads running with the title **question** which is confusing.
Further, one now has to open the thread to read it and find out that he/she does not has the answer.

If you can still change the title by editing your post (not sure if that's possible, never looked at it), please do so.
A good title would be something like 'change ownership of fat32 partition'.

---

### Post by rwabel on 2005-02-17
[QUOTE=Wim Sturkenboom]Hi Lorap, 
 
 you can not change that (to my knowledge) the way you're trying it. It's defined in /etc/fstab. My line for a fat32 partition ooks like:
 ```
/dev/hda2 /windata /vfat auto,uid=1000,gid=1000,umask=0007 0 0
```The uid and gid define the user and group who have the access.
 
 I would suggest that (in future) you use a title that describes your problem when you start a thread instead of using **Question** or **Help**. Most of the time, you will have a question or you will need help when you start a thread.
 
 At the time of writing this, you have two threads running with the title **question** which is confusing.
 Further, one now has to open the thread to read it and find out that he/she does not has the answer.
 
 If you can still change the title by editing your post (not sure if that's possible, never looked at it), please do so.
 A good title would be something like 'change ownership of fat32 partition'.[/QUOTE]
 Mine is like that
 /dev/hdb5       /mnt/hdb5       vfat    user,rw,exec,auto,umask=000     0
 
 Does also work fine for me. What's the difference with unmask?
 Well I've rw and exec to be able to read, write and execute. I guess I'm right. I don't know that well. It just worked that way for me. But if there are better ways, let me know

---

### Post by Wim Sturkenboom on 2005-02-17
I'm not sure anymore, but I'm quite sure that it has to do with security. I don't want everybody to be able to mount my FAT32 partition. A user that does not belong to group 1000 can't access it.

---


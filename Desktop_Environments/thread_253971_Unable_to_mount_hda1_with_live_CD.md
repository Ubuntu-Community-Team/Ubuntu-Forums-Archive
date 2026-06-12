---
title: "Unable to mount hda1 with live CD"
date: 2006-09-09
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-09
Hey, I had my machine crashing a few days ago and since I'm unable to boot properly.
I got to the point when I just wanna backup eveything and re-install Ubuntu (or Xubuntu)
So I got me a Xubuntu live CD, booted, and opened a terminal, wanting to burn my */home* to a DVD.
But I seem to be unable to mount my hard disk. It looks like this:
```
ubuntu@ubuntu:~$ sudo mount -t /dev/hda1
ubuntu@ubuntu:~$ cd /dev/hda1
bash: cd: /dev/hda1: Not a directory
```
Why is that?:confused: 
What should I do?](*,) 

Gabriel

---

### Post by Azathoth_ on 2006-09-09
> **GabrielWolff said:**
> Hey, I had my machine crashing a few days ago and since I'm unable to boot properly.
I got to the point when I just wanna backup eveything and re-install Ubuntu (or Xubuntu)
So I got me a Xubuntu live CD, booted, and opened a terminal, wanting to burn my */home* to a DVD.
But I seem to be unable to mount my hard disk. It looks like this:
```
ubuntu@ubuntu:~$ sudo mount -t /dev/hda1
ubuntu@ubuntu:~$ cd /dev/hda1
bash: cd: /dev/hda1: Not a directory
```
Why is that?:confused: 
What should I do?](*,) 

Gabriel

You have to create a directory first to munt it.
```
$ sudo mkdir a
$ sudo mount -t vfat /dev/hda1 a

```
Change vfat for your kind of partition (ntfs, ext3...)
If you aren't sure which is remove -t vfat

---


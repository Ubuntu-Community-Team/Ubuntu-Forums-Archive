---
title: "Can't read NTFS..."
date: 2006-09-23
forum: Desktop Environments
---

### Post by Copernicus on 2006-09-23
I installed XP and Ubuntu on my 80gb...I now plug in my 250gb NTFS...I only want to read from it. When it's plugged in, ubuntu starts up and says "Mounting Root file system" then "waiting for root file system" and stays there.

CAn anyone help? I have videos on the 250gb I want to be able to watch only on ubuntu 6.06.

thanks

- Nicolaus Copernicus

---

### Post by madmetal on 2006-09-23
reading and writing to ntfs from linux is still under development...
you have two options..
1)create a fat32 partition where you will place all the files you want to access from both windows and linux
2)read this guide for ntfs support
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by MetalMusicAddict on 2006-09-23
Heres what one of my FSTAB lines looks like for NTFS drives/partitions.

```
[COLOR="Red"]/dev/hdb1[/COLOR]       [COLOR="Blue"]/media/RipTemp[/COLOR]     **ntfs    nls=utf8,umask=0222 0       0**
```
The pathes are gonna be specific to you but the stuff in **BLACK** should give you read access.

The path in [COLOR="Red"]RED[/COLOR] points to you device. The path in [COLOR="Blue"]BLUE[/COLOR] is where you wanna see it.

---


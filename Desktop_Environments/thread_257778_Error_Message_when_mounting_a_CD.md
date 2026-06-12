---
title: "Error Message when mounting a CD"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Cariboo1938 on 2006-09-15
After installing "udftools" for "packet writing" I want to create a new mount point and mount a CD.

Here is what I do:
```
sudo mkdir -p /media/udf0
```
and then 
```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0
```
After that I get the error message:
> [COLOR="Red"]mount: /dev/pktcdvd/0: can't read superblock[/COLOR]The measures I would have to take where originally posted by dradul [View Post]("http://www.ubuntuforums.org/showpost.php?p=1476368&postcount=14")
> You may need to disable the other, default, entries. The message means that the CD has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.
[COLOR="Blue"]What do I need to do?
Where can/must I  "disable the other, default, entries"? 
Please help, I don't know how to do it.
Any comment is very much appreciated![/COLOR]

---

### Post by Cariboo1938 on 2006-09-18
> [COLOR="Blue"]What do I need to do?
Where can/must I  "disable the other, default, entries"? 
Please help, I don't know how to do it.
Any comment is very much appreciated![/COLOR]
Case closed!:-\" 

I had to mount a CD and not the CD drive, because the CD has the File System on it I wanted to use...UDF.
The solution is:
When executing the command
Code:
*sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0*

the formatted CD has to be inserted in the corresponding drive!

[draduls HowTo works.]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=dradul") Now I can use CD-R/W's like I was used to it in Windows XP!

---


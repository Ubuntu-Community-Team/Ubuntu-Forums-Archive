---
title: "Using Ubuntu 14.04.3 LTS"
date: 2015-08-15
forum: Desktop Environments
---

### Post by First_Aid on 2015-08-15
Hello everyone,

I'm new to these forums and thought I'd ask around for help, so any and all help is appreciated. 

My windows file on my other laptop recently got corrupted and I've tried every method into fixing the corrupt windows file but it everything seemed to fail (system restore, etc..). The computer was last running on windows 8.1, there is no issue with the hard disk but the issue resides within the windows file. I was told by friends to get Ubuntu in order to recover the files, so I got the boot put in my flash drive and ran it without installing it as a partition. I tried to follow guides to get access to the files, but it got me nowhere. If you could please help me, I would **HIGHLY APPRECIATE IT. **I have been trying to solve this issue for quite a while now, my files are important, so please, help me out.

Thank you in advance.
~First Aid

---

### Post by hansdown on 2015-08-16
Welcome to the forum, 
First_Aid.

You will need another thumb drive to transfer your files to, if your live ubuntu is not persistent.

Open a terminal, and type

```
gk sudo nautilus
```

Hit enter. You should be able to navigate to your files, and save them to the thumb drive.

---

### Post by howefield on 2015-08-16
> **First_Aid said:**
> ... I tried to follow guides to get access to the files, but it got me nowhere..

Might help to know where you got to and the point at which you are stuck. Or is this a game of 20 questions ?

---

### Post by grahammechanical on 2015-08-16
Linux has an issue reading Windows 8 partitions because when Windows 8  shuts down it does not actually shut down it goes into hibernation. This  is done to give Windows 8 a faster start up.

The advice given here might help. 

[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

If  the OP cannot load Windows 8 and change the shut down options to stop  hibernation or fast start up then the OP will have to try the suggestion  given in the link to mount the partition from Linux.

A more accurate description of the thread title would also be useful.

Regards.

---


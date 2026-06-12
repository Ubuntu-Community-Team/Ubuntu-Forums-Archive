---
title: "Problem with detecting external hard drive"
date: 2010-05-07
forum: Desktop Environments
---

### Post by jamesgiles on 2010-05-07
Hi, 

I have Ubuntu Studio, and I have all my music on an external hard drive. However i cannot get linux to recognise it. I have searched for advice on the internet but as I am new to Linux I quite easily get lost in all the terminal commands.

Is there any chance someone could give me some help, perhaps walk me through how to mount an external hard drive.

The drive is 400 GB, and i believe is FAT32. It's USB.

cheers 

JG

---

### Post by jamesgiles on 2010-05-08
Can anyone give me some advice on this?

Cheers

---

### Post by arvindbis on 2011-10-19
hey i think you it is ntfs drive as fat32 doesn't support this much larger dirve!! do cross check!
well if it is fat32 and connection is USB then it should be auto detected!! 
Even i'm new to linux but have some knowledge of devices .:P
regards

---

### Post by collisionystm on 2011-10-19
You can format a drive that large with FAT32. I have a 1tb drive at home I formatted with FAT32 using a method I found. I did it so I can use it with PS3.

@OP

Open terminal

type 

fdisk -l

post the output please

---

### Post by dargaud on 2011-10-19
```
sudo fdisk -l
```
as without 'sudo' the command will not return anything. So what's the output. And the last few lines of 'dmesg' a few seconds after you plug the drive in ? And 'mount' ?

---


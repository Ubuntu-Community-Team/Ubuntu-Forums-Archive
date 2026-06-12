---
title: "How can I access my files on my storage drive?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by Evasen on 2006-03-03
It's formatted under the NTFS file system for my XP setup. Thank you kindly for reading this post. It says that I am not the owner of the drive.

---

### Post by Ramses de Norre on 2006-03-03
Have you mounted the drive?```
/dev/hda3       /media/windowsd  ntfs    nls=utf8,umask=0222 0       0

```
There should be a line similar to this one in fstab, then you should be the owner of the files.
Otherwise: use the chown command, type sudo chown -R your_username mountpoint in terminal.

---

### Post by Evasen on 2006-03-03
[QUOTE=Ramses de Norre]Have you mounted the drive?```
/dev/hda3       /media/windowsd  ntfs    nls=utf8,umask=0222 0       0

```
There should be a line similar to this one in fstab, then you should be the owner of the files.
Otherwise: use the chown command, type sudo chown -R your_username mountpoint in terminal.[/QUOTE]

I'm new to Ubuntu and Linux in general. I have typed in the command in the terminal but it doesn't show anything.

---

### Post by Ramses de Norre on 2006-03-03
Do you have such a line in fstab?
The command wont show any output, but the owner of the files should be changed.

---

### Post by Evasen on 2006-03-03
[QUOTE=Ramses de Norre]Do you have such a line in fstab?
The command wont show any output, but the owner of the files should be changed.[/QUOTE]



I'm sorry but could you tell me what fstab is and how I can access it?  Thank you for your time.

---

### Post by Evasen on 2006-03-03
[QUOTE=Evasen]I'm sorry but could you tell me what fstab is and how I can access it?  Thank you for your time.[/QUOTE] I can access it through the Disks Manager utility.

---


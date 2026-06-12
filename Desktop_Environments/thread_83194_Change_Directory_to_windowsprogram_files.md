---
title: "Change Directory to windows/program files"
date: 2005-10-28
forum: Desktop Environments
---

### Post by haniar on 2005-10-28
I have mounted the NTFS

$ sudu su
mount -w -t NTFS /dev/hda1 /media/windows

The XP disk was successfuly mounted but I cannot see it in the File Browser (I get permission denied)

if I use the terminal window, I can see its content using ls which means it has been mounted properly.

I need to get to the program files directory and I get an error when I type
cd program files

Ideally, I would like to use the File Browser. Failing that, can you please le me know how I can do it using the terminal window.

PS: I am assuming that the above will allow me to both read and write files on the XP disk.

Thank you in advance

---

### Post by Ampersand on 2005-10-28
the easiest way would probably be to try

```
sudo nautilus
```

to get a file browser running as root.

---

### Post by haniar on 2005-10-28
That worked, but for some reason my settings are not allowing me to delete a file on the XP disk. 

I mounted the drive with the -w option. What else do I need to be able to delete a file in NTFS

---

### Post by Kirky_D on 2005-10-28
[QUOTE=haniar]That worked, but for some reason my settings are not allowing me to delete a file on the XP disk. 

I mounted the drive with the -w option. What else do I need to be able to delete a file in NTFS[/QUOTE]

In ubuntu you can't write to ntfs partitions, only read them.

---


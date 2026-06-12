---
title: "NTFS Write Support"
date: 2006-01-16
forum: General Help
---

### Post by zappa86 on 2006-01-16
I have compiled a kernel with NTFS write support into it. I check to make sure the drive is mounted with a umask of 000 and it is in rw mode. However, whenever i try to put a file on it, I get a permission is denied. Why does this happen if the support is  compiled in?

---

### Post by jasmuz on 2006-01-16
When you mount it, under is it available to all users or just root, if so...change it to be available to all users.

---

### Post by soulestream on 2006-01-16
> I have compiled a kernel with NTFS write support into i

Now i havent compiled a kernel since 2.6.13, but you may want to go back and read what "NTFS write support" is.

It doesnt allow you to create new files on the system, only modify existing ones as longs as you dont change the filesize at ALL.

If you need to create/put files you may want to look at captive-ntfs driver.

soule

---

### Post by RAOF on 2006-01-16
[QUOTE=soulestream]Now i havent compiled a kernel since 2.6.13, but you may want to go back and read what "NTFS write support" is.

It doesnt allow you to create new files on the system, only modify existing ones as longs as you dont change the filesize at ALL.

If you need to create/put files you may want to look at captive-ntfs driver.

soule[/QUOTE]
Actually, I think that NTFS support in 2.6.15 has improved by leaps & bounds.  IIRC, it's now possible to delete files, and to change the size of existing files!  Possibly even create new files :)

In the arcane language of umask, I'd try adding an additional '0' on the end, so it becomes umask=0000.  I'm not **totally** sure what the difference is, but 000 didn't work for me, and 0000 did.

[rant]And does anyone know why the vfat & ntfs guys (alone, AFAIK) decided to **reverse** the meaning of the octal file permissions?  Everywhere else it's "what permissions to give", vfat & ntfs it's "what permissions to remove".    Aaargh.[/rant]

---

### Post by qferret on 2006-01-17
[QUOTE=RAOF]
[rant]And does anyone know why the vfat & ntfs guys (alone, AFAIK) decided to **reverse** the meaning of the octal file permissions?  Everywhere else it's "what permissions to give", vfat & ntfs it's "what permissions to remove".    Aaargh.[/rant][/QUOTE]

[QUOTE=RAOF]Yup, FAT32 is the devil.  
[/QUOTE]

LOL :razz:

---


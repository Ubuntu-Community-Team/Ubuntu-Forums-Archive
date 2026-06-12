---
title: "directory attribute"
date: 2008-01-03
forum: Desktop Environments
---

### Post by danifodor on 2008-01-03
Hi!

I would like to make a directory that (and maybe its content) can not be deleted but files can be copied into it. The best solution would be chattr +a Directory but it does not work. 

I create the directory (e.g., backup), and type chattr +a backup. It works so far:
```

lsattr -d backup
-----a------------ backup

```
When I try to copy a file into it I get an error message:
```

cp: cannot create regular file `***': Operation not permitted

```
The file is created but its size is 0.
The +u attribute does not work at all, I can delete both directories and files with this attribute.

I also created a directory and changed the ownership to root.user and set the permissions to 770 but user also can delete the directory.

I have ext3 file system and use ubuntu 7.10

Does anyone have a tip?

Cheers

Daniel

---

### Post by kidders on 2008-01-04
Hi there,

> **danifodor said:**
> The best solution would be chattr +a DirectoryThe chattr utility is totally obsolete, and Ext2-specific. Many of the file attributes it sets (including 'u') are not even honoured in modern Ext2/3 implementations, so it's usefulness is pretty limited.

I would suggest setting your directory's sticky bit & making it world writable, much like /tmp is normally configured. It probably makes the most sense to give root ownership of the directory. In that case, anybody could create files in it, but nobody could delete anything they didn't own, including the directory itself. There's a more detailed description in chmod's man page.

---

### Post by danifodor on 2008-01-04
Hi,

thanks, I thought it is some kernel specific problem. I was thinking about compiling a new one. I read the sticky bit but chattr would have been better.

Cheers

Daniel

---


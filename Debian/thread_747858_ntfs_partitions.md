---
title: "ntfs partitions"
date: 2008-04-07
forum: Debian
---

### Post by ntowakbh on 2008-04-07
I'm moving from Ubuntu to Debian(Testing), and so far, I've been able to figure out every issue that I've had, either by man pages for programs I barely touched in Ubuntu, or by a Google search, however this problem is one that I've been tearing my hair out over.

I use one ntfs partition that I put nearly all of my files that I use across OSes on, music, videos, pictures, etc.  So my problem is how to let myself, or any user besides specifically root, read, write, and execute from there.  In my /etc/fstab file, I've got it where I can read, but I don't think I have write or execute permissions.  

I know already it has something to do with umask, but that is something that I am not grasping for some reason.  Could anyone please help me? 

If it helps, here is my current line for the partition in my /etc/fstab
```
/dev/hdb9       /media/hdb9     ntfs    defaults,umask=000,gid=46       0     1
```

Any help with this is greatly appreciated.

---

### Post by jdhore on 2008-04-07
> **ntowakbh said:**
> I'm moving from Ubuntu to Debian(Testing), and so far, I've been able to figure out every issue that I've had, either by man pages for programs I barely touched in Ubuntu, or by a Google search, however this problem is one that I've been tearing my hair out over.

I use one ntfs partition that I put nearly all of my files that I use across OSes on, music, videos, pictures, etc.  So my problem is how to let myself, or any user besides specifically root, read, write, and execute from there.  In my /etc/fstab file, I've got it where I can read, but I don't think I have write or execute permissions.  

I know already it has something to do with umask, but that is something that I am not grasping for some reason.  Could anyone please help me? 

If it helps, here is my current line for the partition in my /etc/fstab
```
/dev/hdb9       /media/hdb9     ntfs    defaults,umask=000,gid=46       0     1
```

Any help with this is greatly appreciated.

the easiest way...is to remove all the umask and gid crap...you should have rwx (i'm lazy) permissions when you boot and it mounts, or you can mount it as your normal user with: ```
mount /media/hdb9
```

as long as /media/hdb9 is in the fstab and it should give you rwx permissions

---

### Post by ntowakbh on 2008-04-07
> **jdhore said:**
> the easiest way...is to remove all the umask and gid crap...you should have rwx (i'm lazy) permissions when you boot and it mounts, or you can mount it as your normal user with: ```
mount /media/hdb9
```

as long as /media/hdb9 is in the fstab and it should give you rwx permissions

I tried it with just defaults and that still didn't work.

EDIT: Just double checked, and it does mount but I don't have permissions, only root does.

---

### Post by SunnyRabbiera on 2008-04-07
you may have to enter it under super user mode, by typing in su, then your root password.

---

### Post by jdhore on 2008-04-07
The other option that i forgot to consider...It's possible that Debian compiles the kernel without NTFS write support...but...I'd use NTFS-3G anyway

---

### Post by odiseo77 on 2008-04-07
Yes, ntfs-3g is what I'm using on Debian in order to write to my NTFS partition. You must install it with apt-get and then, edit your fstab file properly. You might want to add the "locale" option to the fstab line for this partition. I have *locale=es_VE.utf8*, but you obviously have to change the locale value for your real locale (you can know it with the command ***locale -a***).

Greetings.

---

### Post by ntowakbh on 2008-04-07
Thanks a lot, jdhore and odiseo77! Installing ntfs-3g worked perfectly! :guitar:

---


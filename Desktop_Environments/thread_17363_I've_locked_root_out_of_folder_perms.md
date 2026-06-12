---
title: "I've locked root out of folder perms"
date: 2005-02-28
forum: Desktop Environments
---

### Post by RichardA on 2005-02-28
I have a folder used as a Samba mount point. I was trying to change the permissions on the share, and didn't know whether I should change the mounted partition, Samba or the mount point...

I was typing as root but not thinking, and I chmod'ed the mount point to something silly (not sure what). Now 'ls' can't see it, 'rmdir' says I don't have permission or that it can't stat (not sure which, not at own PC currently), 'mkdir' says the folder already exists.

Basically, I've locked root out of the permissions for this folder. I can just ignore it and use a different mount point, but can it be fixed? I didn't know this was even possible. (Using Reiser FS).

---

### Post by MEW on 2005-02-28
Can't you just chmod it back again so that it will work?

(i.e. chmod +rx /home/you/smb4k/ -R)

---

### Post by RichardA on 2005-02-28
[QUOTE=MEW]Can't you just chmod it back again so that it will work?

(i.e. chmod +rx /home/you/smb4k/ -R)[/QUOTE]
 Nope. Chmod, like ls, can't see it..

---

### Post by Wardhog on 2005-02-28
[QUOTE=RichardA]I have a folder used as a Samba mount point. I was trying to change the permissions on the share, and didn't know whether I should change the mounted partition, Samba or the mount point...

I was typing as root but not thinking, and I chmod'ed the mount point to something silly (not sure what). Now 'ls' can't see it, 'rmdir' says I don't have permission or that it can't stat (not sure which, not at own PC currently), 'mkdir' says the folder already exists.

Basically, I've locked root out of the permissions for this folder. I can just ignore it and use a different mount point, but can it be fixed? I didn't know this was even possible. (Using Reiser FS).[/QUOTE]

I thought you couldn't restrict root from doing anything.  When you say ls and rmdir can't see it/remove it, which user are you running those commands as?
Eg.  $ls /path/in/question  <- runs as you
$sudo ls /path/in/question <- runs as root

Does this help you out at all?

---

### Post by RichardA on 2005-02-28
[QUOTE=Wardhog]I thought you couldn't restrict root from doing anything.  When you say ls and rmdir can't see it/remove it, which user are you running those commands as?
Eg.  $ls /path/in/question  <- runs as you
$sudo ls /path/in/question <- runs as root

Does this help you out at all?[/QUOTE]

That was all done as root, but I think I know what this is about. It's something to do with Samba:
```

root@cetri ~ # ls /media/
cdrom  cdrom0  cdrom1  floppy  floppy0  sdd1  shared
root@cetri ~ # mount /media/shared
Anonymous login successful
root@cetri ~ # ls /media/
ls: /media/shared: Permission denied
cdrom  cdrom0  cdrom1  floppy  floppy0  sdd1

```
So I need to learn about Samba permissions!

---

### Post by alastair on 2005-02-28
What about :

ls -l /media

So we can see the permissions.

To change - something along the lines of :

sudo chmod 777 /media/shared

---

### Post by p!=f on 2005-02-28
Also, is /media/shared mentioned in /etc/fstab? Just to check mount parameters.

---

### Post by RichardA on 2005-03-01
```

root@cetri ~ # ls -l /media/
ls: /media/shared: Permission denied
total 9
lrwxrwxrwx    1 root     root            6 2004-09-30 19:08 cdrom -> cdrom0
drwxr-xr-x    2 root     root           48 2004-09-30 19:08 cdrom0
drwxr-xr-x    2 root     root           48 2004-09-30 19:08 cdrom1
lrwxrwxrwx    1 root     root            7 2004-09-30 19:08 floppy -> floppy0
drwxr-xr-x    2 root     root           48 2004-09-30 19:08 floppy0
drwxr-x---    2 root     root           48 2005-02-19 21:54 sdd1
drwxr-xr--  143 richard  richard      5560 2005-01-20 22:29 spare
drwxr--r--    6 root     root         4096 1970-01-01 01:00 spare2
root@cetri ~ # umount /media/shared
root@cetri ~ # ls -l /media/
total 9
lrwxrwxrwx    1 root     root            6 2004-09-30 19:08 cdrom -> cdrom0
drwxr-xr-x    2 root     root           48 2004-09-30 19:08 cdrom0
drwxr-xr-x    2 root     root           48 2004-09-30 19:08 cdrom1
lrwxrwxrwx    1 root     root            7 2004-09-30 19:08 floppy -> floppy0
drwxr-xr-x    2 root     root           48 2004-09-30 19:08 floppy0
drwxr-x---    2 root     root           48 2005-02-19 21:54 sdd1
drwxr-xr-x    2 root     root           48 2005-02-28 21:10 shared
drwxr-xr--  143 richard  richard      5560 2005-01-20 22:29 spare
drwxr--r--    6 root     root         4096 1970-01-01 01:00 spare2

```
I can chmod when the share isn't mounted, so that was the problem.

And yes, the line in fstab is:
```

//dva/shared /media/shared smbfs username=guest,password= 0 0

```

---

### Post by RichardA on 2005-03-01
This is a Samba problem. I'm going to start a new thread.

---


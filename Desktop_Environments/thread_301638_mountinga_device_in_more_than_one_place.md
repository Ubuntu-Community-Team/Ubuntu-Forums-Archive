---
title: "mountinga device in more than one place?"
date: 2006-11-17
forum: Desktop Environments
---

### Post by RunsWithScissors on 2006-11-17
Ok I have a question I need the contents of a drive appear to be in 2 different places in the file system. or install I want the contents of /dev/md0 "raid array" mounted in /media/raid0 and /media/FileServ/Programs

or if there is another way to go about this let me know.

I will need this file structure to be readable from the ewindows file sharing side too. So any links will have to work with samba.

---

### Post by lloyd_b on 2006-11-17
> Ok I have a question I need the contents of a drive appear to be in 2 different places in the file system. or install I want the contents of /dev/md0 "raid array" mounted in /media/raid0 and /media/FileServ/Programs

or if there is another way to go about this let me know.

I will need this file structure to be readable from the ewindows file sharing side too. So any links will have to work with samba.

Try this:

```
**sudo mount --bind /media/raid0 /media/FileServ/Programs**
```

This will work provided that you have a kernel version >= 2.4 

Note: if there are other file systems mounted underneath of /media/raid0, they will NOT be accessible from media/FileServ/Programs.  To have them available, you'll need the following command:

```
**sudo mount --rbind /media/raid0 /media/FileServ/Programs**
```

Lloyd B.

---

### Post by scrooge_74 on 2006-11-17
> **RunsWithScissors said:**
> Ok I have a question I need the contents of a drive appear to be in 2 different places in the file system. or install I want the contents of /dev/md0 "raid array" mounted in /media/raid0 and /media/FileServ/Programs

or if there is another way to go about this let me know.

I will need this file structure to be readable from the ewindows file sharing side too. So any links will have to work with samba.


What about making a link? You can use the ln command

---

### Post by RunsWithScissors on 2006-11-18
> **scrooge_74 said:**
> What about making a link? You can use the ln command

Can you elaborate?

---

### Post by scrooge_74 on 2006-11-18
> **RunsWithScissors said:**
> Can you elaborate?

the link command let you make "links" to files or folders just as the shorcuts in MS

Here you can find more informatoin on commands [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

you can also from a console type man ln so you can know more about it.

---

### Post by lloyd_b on 2006-11-18
The simple syntax for a "symlink" (Symbolic link) is:

```
**ln -s {source} {dest}**
```

Where {source} is an existing file/directory, and {dest} is where you wish to create the link.

"man ln" will give you a lot more info on the subject.

You may find that a symlink will not work with Samba (I'm not familiar with Samba, so I can't tell you for sure either way). 

Try a symlink, and if it works leave it.  If Samba has a problem with it, then use the "mount --bind" solution.  Symlinks are simpler, but there are situations where they simply don't work.  The "mount --bind" trick is guaranteed to work with anything that runs on Linux.

Lloyd B.

---


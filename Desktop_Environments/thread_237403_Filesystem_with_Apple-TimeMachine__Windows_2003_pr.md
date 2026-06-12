---
title: "Filesystem with Apple-TimeMachine / Windows 2003 previous versions support"
date: 2006-08-16
forum: Desktop Environments
---

### Post by [flax] on 2006-08-16
Lately both Apple and Microsoft are starting to use a file-versioning filesystem.

Can somebody tell me if there is a filesystem which supports this natively, or do i need to install some tools / lib, in order to get the same behaviour on my Ubuntu Dapper System, and which one should i use?

I did some searches on the internet, but it's hard to get distinction between versioning-filesystems  and file-versioning-filesystems. I've currently found the following implentations:
- [http://www.ext3cow.com/](http://www.ext3cow.com/)
- ??

(only for ext3 support? )

---

### Post by anthro398 on 2006-08-16
This is a funny development is filesystem architecture.  Here I've been spending time figuring out how to make sure nothing is cached and empty space is overwritten to ensure that forensics on my disks would fail and now they're building versioning into the fs.

---

### Post by [flax] on 2006-08-16
Well, if been using versioning systems to keep track of my (source-)files (over time).

This is also the reason why i want to try a filesystem that supports it natively.

---

### Post by GeneralZod on 2006-08-16
I can't connect to the site at the moment, but I believe WayBack (a FUSE filesystem) can handle this.  I have no idea how well it works, though.

[http://fuse.sourceforge.net/wiki/index.php/FileSystems](http://fuse.sourceforge.net/wiki/index.php/FileSystems)

Edit:

Damnit - this is mentioned at the bottom of that page you linked :)

---


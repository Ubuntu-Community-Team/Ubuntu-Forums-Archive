---
title: "Looking for a way to have a portable filesystem (or mounting without root)"
date: 2009-02-25
forum: General Help
---

### Post by dkulchenko on 2009-02-25
I have a free software project I'm working on that provides portable versions of Linux applications capable of being carried around on removable media, with settings and documents traveling along. 

While developing the portable launcher, I fell into a problem: FAT32 partitions do not support symbolic links. This becomes a problem because 99% of Linux programs make use of symlinks for libraries, shared files, and whatnot. Therefore, I can solve the problem by duplicating directories where the symlinks would be, but this is extremely inefficient, and becomes a space problem on USB drives. 

In my search for solutions, I thought of having a filesystem in a file that mounts into a temporary directory, from which the program then executes. The problem with this solution is that to mount a file, you require root privileges, and my target user base is users that will be using the apps on random computers, users that will not have root privileges on those computers. 

**My question is:** Is it possible to have a read-write filesystem contained in a single file, and be able to mount it without root privileges? Maybe there is an alternative to mounting that accomplishes the same thing. Any ideas?

NOTE: Because of the situation, the users should not require root access on the host computers that they will be running apps on. It is safe to assume that they will have root access on the computers from which they will be downloading the apps from.

ANOTHER NOTE: I can't just use ext3 for the drive, because the portable apps will be for public use, and almost all removable media is either FAT or FAT32, neither of which support symlinks.

---

### Post by Gen2ly on 2009-02-25
well dkulchenko, you could use syslinux Definitely, but that is alot alot of work and I don't know alot about it.  syslinux is the way that bootableCDs are made.  why not format the drive ext3?

---

### Post by dkulchenko on 2009-02-25
I'm developing portable applications for general use. 99% of USB drives are FAT32. Therein lies my problem.

---

### Post by mb_webguy on 2009-02-25
> **dkulchenko said:**
> I'm developing portable applications for general use. 99% of USB drives are FAT32. Therein lies my problem.

Ok, but why can't you just reformat the drive as ext3?

---

### Post by dkulchenko on 2009-02-25
Because that puts too much of a burden on the user. I'm trying to make this as easy on the user as possible.

---


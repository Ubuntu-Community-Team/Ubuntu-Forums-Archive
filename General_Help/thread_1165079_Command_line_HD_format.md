---
title: "Command line HD format"
date: 2009-05-20
forum: General Help
---

### Post by prem1er on 2009-05-20
This may sound like a weird question, but what is the fastest way to format a drive from the command line?  I'm assuming it would be multiple commands or a simple script, but I would like to have this available to me.  Thanks.

---

### Post by dstempfley on 2009-05-20
I could be missing something here, but not including laying out a partition map with fdisk.  The fastest format is to layout a new filesystem with mkfs.

Why is speed an issue?  Format is one of those things that could ruin your whole day if you make a mistake.

/Dion

---


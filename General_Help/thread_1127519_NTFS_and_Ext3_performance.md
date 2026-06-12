---
title: "NTFS and Ext3 performance"
date: 2009-04-16
forum: General Help
---

### Post by conradcliff on 2009-04-16
Hey guys, I was just wondering if there was a noticeable read/write performance difference between ntfs and ext3 in linux?

---

### Post by paradigm2 on 2009-04-16
> **conradcliff said:**
> Hey guys, I was just wondering if there was a noticeable read/write performance difference between ntfs and ext3 in linux?

I can't say for sure but ext3 is native while ntfs is built using reverse engineering.  Microsoft does not really publish the full ntfs specification last I heard.  It is highly likely that ext3 is much faster on Linux.

Honorable mention is the new ext4 which is said to be even faster than ext3.  However it is pretty much in beta status and is optional in Jaunty (9.04).  If you try ext4, you are taking a risk.

---

### Post by conradcliff on 2009-04-29
Thanks for the info...I'm also guessing that NTFS is going to be slower then ext3 but I just don't know. Anybody else out there have a clue?

---

### Post by pparks1 on 2009-04-29
I wouldn't suggesting using NTFS over EXT3 on a Linux hosts.   You want the Linux based file system for the core system for security and such.

---

### Post by conradcliff on 2009-04-29
I'm dual booting between XP and linux and accessing multimedia files between both and am trying to determine how I want to partition my "files" drive. I'm trying to weigh things out so I need to know if ext3 is actually faster and if it is then how much...

---

### Post by buchan on 2009-04-29
> **conradcliff said:**
> I'm dual booting between XP and linux and accessing multimedia files between both and am trying to determine how I want to partition my "files" drive. I'm trying to weigh things out so I need to know if exr3 is actually faster and if it is then how much...

In reading your post it looks like you want to be able to access your files from an "intermediary" storage partition right?

If thats the case you will have to go with NTFS as windows will not read EXT3 as far as I know ... Maybe someone can prove me wrong but doing a quick google for ext3 windows comes back with limited (readonly) support.

There is support for read/write to NTFS from Ubuntu though I think.

---

### Post by conradcliff on 2009-04-29
Well, that's not necessarily the case either..I may determine that the best course of action is to create a substantial partition for linux to play in on my "files" drive. Are there any linux tools for measuring disk performance?

---


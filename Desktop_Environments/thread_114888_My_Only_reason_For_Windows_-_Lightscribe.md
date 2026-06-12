---
title: "My Only reason For Windows - Lightscribe"
date: 2006-01-09
forum: Desktop Environments
---

### Post by dragonfyre13 on 2006-01-09
HELP! I have been dualbooting for weeks! I can't stand windows anymore, and the only reason I still have it is for lightscribe direct disk labeling. Does anyone have any information on this?

when I googled it, it showed that K3B is making a lightscribe host, and I offered to donate, but I haven't recieved a response. I'm asking you all. I've tried wine, and crossover, as well as Cedega, and Qemu. Any suggestions?

---

### Post by linkunderscore on 2006-01-09
VMware ?

---

### Post by soulestream on 2006-01-09
you might want to check nero for linux. 

supposedly 6.0 was going to support lightscribe, I just don't know if the linux version supports it


soule

---

### Post by dragonfyre13 on 2006-01-10
I tried NeroLinux. It doesn't support it as yet, and actually doesn't support anything beyond K3B. K3b still outstrips it in nearly every respect anyway.

As for VMware, I'll give it a try. The problem that I had with Qemu is that it made a virtual drive out of things, which made it so it couldn't even burn disks, let alone labels.

---

### Post by dragonfyre13 on 2006-01-25
OK, guys, I found a solution.

If I load win 2000 in VMWare 5.5, it works perfectly, but only for CDs. DVDs still throw a major error about not being able to read the disk, but that is fine. 80% of the disks I label are CDs.

Just thought I would let everyone know.

If you have another way, prefferably a way to run it natively, I would definately be interested.

---

### Post by dragonfyre13 on 2006-01-28
OK, I got it working for both. I need to change to DMA mode writing for the ATAPI Controller. Then, it write both perfectly.

---


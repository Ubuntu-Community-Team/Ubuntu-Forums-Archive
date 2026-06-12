---
title: "Updating Live-USB causes disk space to go to zero"
date: 2009-04-15
forum: General Help
---

### Post by matrixblue on 2009-04-15
I installed Ubuntu 8.10 on a Flash drive and it works very well.

When I try to update it the disk space goes to zero even though my persistence file is over 1 gig.

Am I really running out of space? Or is this some bug? Or are Live-USB just not meant to be updated?

---

### Post by Bucky Ball on 2009-04-15
I don´t think you can update them.

---

### Post by Morat on 2009-04-27
I have also tried using the Update Manager to update a flash-drive live install and have also had all my disk space eaten up (3 gig reserved for my data)

> **Bucky Ball said:**
> I don´t think you can update them.

So any ideas how to reclaim the disk space used up? I have run 
[INDENT][/INDENT]sudo apt-get clean
and emptied the trash but I don't think it has got it all back. I still only appear to have 313mb free. What else can I do to reclaim disk space?

--- Morat.

---

### Post by matrixblue on 2009-04-27
That's another problem I couldn't figure out. All I could do it delete the casper file and replace it with another one.

---

### Post by Bucky Ball on 2009-04-28
Probably like a boot CD. You will notice that all the disk space is used up there also, even if it isn't if you follow me. This is a boot device therefore set up *not* to be overwritten. Wipe and start again.

---

### Post by dcstar on 2009-04-28
IIRC it is something to do with the "SQUASHFS" that the Live CD uses as default, basically it means that that files of the same name take up new space and the old space is never made available for reuse.

If you do a web search you can dig out all the technical guff.

---


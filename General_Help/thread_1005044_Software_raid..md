---
title: "Software raid."
date: 2008-12-07
forum: General Help
---

### Post by Blice on 2008-12-07
Hi.

My friend is using Linux for his first time (Kubuntu), and he had a raid on his windows machine. He has his main drive, and then he has two drives that mirror eachother.

On linux, it sees this as two different drives that have the same files in them- All of the software raid guides I've found consist of formatting the drives, is there any way I can do this without losing all the files?

I'm SSH'd into his machine so if you need me to check anything I can.

Thanks!

---

### Post by Blice on 2008-12-07
Bumping this up from the second page..

---

### Post by reality1011 on 2008-12-07
This isn't a raid solution but this would work... Make a backup of the entire filesystem:

Check the blog:
[http://ubuntu-commands.blogspot.com/2008/10/howto-backup-and-restore-your-system.html](http://ubuntu-commands.blogspot.com/2008/10/howto-backup-and-restore-your-system.html)

---

### Post by Blice on 2008-12-07
One question though- If I redo the raid on Linux, then it'll be two drives again in Windows, right? So it's one or the other here..?

---

### Post by samuraix51 on 2008-12-07
Does the BIOS on the motherboard have an option to do RAID there?
If it does I think you can set up the array on there and use dmraid for linux to see the array, and windows should be able to as well.

Definatly backup all the data on the drives you are going to be using, then if something goes wrong you do have a backup of it all.

---

### Post by reality1011 on 2008-12-09
You should be able to create a new partition on the 2 drives (if you have enough space) and use that new partition for linux... that would give you a dual os raid setup

---


---
title: "3 gigs of unallocated space, can i add it to vista or ubuntu?"
date: 2009-03-12
forum: General Help
---

### Post by dayv2005 on 2009-03-12
When i started partitioning my hard drive so i could dual boot ubuntu and vista, on my second partition i must have had some files on it. So Gparted didn't include about 3 gigs of space in the partition. The problem is now that i have 3 gigs of unpartitioned space that i can't seem to add it to the current ubuntu install or the vista ntfs. can anyone help me out on this one? Also i can't seem to find ntfsprogs to convert the unallocated space to ntfs.

---

### Post by logos34 on 2009-03-12
boot from the ubuntu live cd and use gparted (system>admin>partition editor) to grow ubuntu / to take up the space

---

### Post by dayv2005 on 2009-03-12
Thanks, will that also give me ntfs ability too? because i have a 10 gig rescue partition in there too i might just wipe out but i am going to try it now. Thanks

---

### Post by dayv2005 on 2009-03-12
i tried it but it wouldn't let me stretch the ubuntu partition for the more space. What should i format it to? Or should i leave it unformated?

---

### Post by philinux on 2009-03-12
> **dayv2005 said:**
> i tried it but it wouldn't let me stretch the ubuntu partition for the more space. What should i format it to? Or should i leave it unformated?

Post a screenshot of what gparted sees.

---

### Post by dayv2005 on 2009-03-12
[IMG]http://twitpic.com/img/21lxk-d4610cbc58abde051093c836bd06852a.49b9accc.jpg[/IMG]

The small one on the far left was unallocated. The next one in black is unknown. (i just deleted pqservice a hidden partition on my hdd) sda2 is my ntfs. The next two are the pieces i want to append to ubuntu. Also want to append the unknown to sda2. And the last one is sda5 ubuntu. I basically want to redo it so that there is sda1 (vista) sda2 (ubuntu).

If formating completely and reinstalling is the best thing to do i can do that too, but it wont let me delete sda5. It says i need to unmount anything higher than 5. 

I'm just aiming for cleaner partitioning of my hard drive and daul boot with ubuntu and vista.

for some reason the picture isn't showing up any more but here's the link

[http://twitpic.com/21lxk]("http://twitpic.com/21lxk")

---

### Post by logos34 on 2009-03-13
> **dayv2005 said:**
> [IMG]http://twitpic.com/img/21lxk-d4610cbc58abde051093c836bd06852a.49b9accc.jpg[/IMG]
The small one on the far left was unallocated. The next one in black is unknown. (i just deleted pqservice a hidden partition on my hdd) sda2 is my ntfs. The next two are the pieces i want to append to ubuntu. Also want to append the unknown to sda2. And the last one is sda5 ubuntu. I basically want to redo it so that there is sda1 (vista) sda2 (ubuntu).

If formating completely and reinstalling is the best thing to do i can do that too, but it wont let me delete sda5. **It says i need to unmount anything higher than 5.**

It's probably activating the swap, which ties up the entire extended partition.  Right-click on sda6>'swapoff' should fix it.

Backup whatever you need on sda3, delete it, grow sda4 to the left, then expand sda5 to take up the empty space. 

For windows, I would use vista's in-built disk management resize tool to delete the recovery/utility partition sda1, and expand vista to incorporate the space.  That'll give you the best chance of booting back into vista without a  hitch


> Thanks, will that also give me ntfs ability too?

yes, gparted handles ntfs format, but use the vista tool instead as mentioned above

good luck

---


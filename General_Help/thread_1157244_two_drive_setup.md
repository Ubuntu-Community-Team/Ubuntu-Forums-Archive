---
title: "two drive setup"
date: 2009-05-12
forum: General Help
---

### Post by adult swim on 2009-05-12
i recently got 2 older computers given to me and ive got a question about what i should do.  im going to take the hdd out of the lower performance one and place it in the better one.  ill end up having one computer with two hdds.  is there a way to daisy chain the drives together so they appear as one drive?  i did some research and i think that raid 0 is what i am looking for.  does that sound correct?  also i saw LVM, is that something i should look into?  thanks for the help!

---

### Post by fjgaude on 2009-05-12
I don't use LVM, dont' need it. Yes, raid0 will work but the smallest drive will determine the overall space. Also, if one drive fails you are toast, nothing left to read or recover.

Let's some links to get you going with raid:

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)
[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Hope these help.

---

### Post by adult swim on 2009-05-12
thanks for the info fjgaude, i will get to reading!

---

### Post by sgosnell on 2009-05-12
IMO you're better off just installing them as separate drives.  You can install Ubuntu using the smaller drive for / and the larger one for /home.  That helps insure that upgrades won't affect your data, if they go wrong.  You won't really notice that they're separate drives in use, you'll just see the filesystem, with /home showing as just another folder.

---

### Post by adult swim on 2009-05-12
i thougth about doing that but it really doesnt make any sense to have an 80gb root partition.  this is going to be more of a learning experience than anything.

---

### Post by sgosnell on 2009-05-12
So make your root partition whatever size you want, use a couple or 3 GB for swap, and the rest as a separate parition, mounted as a separate drive, and the second HDD as home.  That's the safest way to do it, I think, but you can make it as complicated as you like, learning as you go.

---

### Post by nacho32 on 2009-05-12
personnely I would run a dual boot , your making it harder then it has to be.

---

### Post by raymondh on 2009-05-12
> **adult swim said:**
> i thougth about doing that but it really doesnt make any sense to have an 80gb root partition.  this is going to be more of a learning experience than anything.

Just a thought ... if this is to be a learning experience, why not allocate separate spaces for other directories (/var, etc, etc, etc) ..... that'll give you more "control" when you start tweaking/customizing?

only my 2 cents :)  (Dunno if "control" was a good word though ... maybe "advantages" is better)

---


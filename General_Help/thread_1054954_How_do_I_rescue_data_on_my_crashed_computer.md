---
title: "How do I rescue data on my crashed computer?"
date: 2009-01-30
forum: General Help
---

### Post by funky_uncle on 2009-01-30
I've been running Linux Mint, and while saving up the money to buy an external HD to put my backups on, the entire system crashes and I can't even get a picture on the screen. It started out with some sort of problem deteting my nVidia card or something (it used to work perfectly), upon trying to change resolution/drivers etc I'm left with seeing nothing at all.

I was going to try Ubuntu again anyway. Problem is when I boot with a Live CD I can't seem to find any of my stuff on the HD, I can't even see my home directory. If I can at least find the files I could load them on to a server somewhere and do a clean install.

Any tips?

---

### Post by orlox on 2009-01-30
When running the live cd, open a terminal and use this command:
```

df

```
That should list the disks that are mounted. If your disk appears, you can robably find it under the /media/ folder.

If not, do this:
```

ls /dev

```
Your partitions should appear listed there, and you can mount them if they are unmounted.

If you dont understand the outputs, just put them here.

---

### Post by drs305 on 2009-01-30
This link may be helpful - ubuntu wiki on data recovery:
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by funky_uncle on 2009-01-30
> **orlox said:**
> When running the live cd, open a terminal and use this command:
```

df

```
That should list the disks that are mounted. If your disk appears, you can robably find it under the /media/ folder.

If not, do this:
```

ls /dev

```
Your partitions should appear listed there, and you can mount them if they are unmounted.

If you dont understand the outputs, just put them here.Thanks! I couldn't access my HD from Nautilus in Ubuntu, but While waiting for replies here I spun an OpenSUS Live CD and found it right away.

I see I have way too much data (esp. music) to even start burning them to CDs, much less upload them to some server.

How about this plan: make backups of the essential stuff like pictures from our wedding :o and then install Ubuntu without overwriting that partition. Then I can copy it all back where I want it and delete the partition.

I'm pretty nooby when it comes to partitions, but could it work?

And btw, this sort of community support is the main reason I'm going for Ubuntu. Again, thanks a bunch!

---

### Post by funky_uncle on 2009-01-31
bump

---

### Post by funky_uncle on 2009-01-31
I think I have only one partition on the disk. I'll see if I can create another partition with a LiveCD (SUSE or Ubuntu) and if I can, maybe I can install Linux without touching that partition.

---


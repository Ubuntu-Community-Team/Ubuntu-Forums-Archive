---
title: "Shrink ubuntu partition for vista?"
date: 2008-12-19
forum: General Help
---

### Post by Fzang on 2008-12-19
At first I gave ubuntu 150 GB and vista 150 GB but now that I've installed a lot of games on vista I've already used nearly 80 GB (!!!) of my vista partition...

Vista has a feature where you can shrink unusd NTFS partition into unpartitioned space, this process is completely safe.

Does ubuntu have something like that which won't damage files/partitions?

---

### Post by lovelyvik293 on 2008-12-19
You can better use the gparted.It's a live cd.

---

### Post by Fzang on 2008-12-19
But won't GPartEd forcefully shrink/move my partitions damaging any files standing in it's path? That's why I'm not doing a manual partition

---

### Post by redilyn on 2008-12-19
Gparted will resize the partitions without destroying files unless the power goes out or something.

Just pay very close attention to what you are doing and everything should be fine.

I've resized a few partitions with gparted without losing any data.

---

### Post by binbash on 2008-12-19
gparted is safe if  you dont face with power problems

---

### Post by Wartender on 2008-12-19
i had no idea Gparted could screw up my computer if the power went out, and it does here a lot. To think i've been using it so much:shock:

---

### Post by redilyn on 2008-12-19
I've only had it happen once. I did lose the partition.

Makes you want to invest in a UPS!

---

### Post by ugm6hr on 2008-12-19
> **Fzang said:**
> Vista has a feature where you can shrink unusd NTFS partition into unpartitioned space, this process is completely safe.

I find it hard to believe that any changes to the partition table could be *completely* safe.

My advice: Do a backup.

---

### Post by 1packer on 2008-12-19
I'm always repartitioning stuff, but I'm on a laptop so it's not really a problem with power outages. As long as you don't cancel the job as well it is safe. I have had issues resizing ntfs without the windows partition editor though.
As long as gparted can tell you how big a partition is and how much is used, then it can resize it safely.

---


---
title: "Best partitions for an Ubuntu only install."
date: 2009-02-23
forum: General Help
---

### Post by Arazu on 2009-02-23
I've never run Ubuntu alone before. I could use suggestions for the best partition scheme.

Thanks!

---

### Post by taurus on 2009-02-23
You need at least two partitions:  / and swap.  However, it's a good idea to have three, /, swap, and /home because all your personal files and settings will be in /home/username.  So when you upgrade or reinstall, you can keep all your personal files in /home.  You just have to mount that partition to /home and do not format that partition if you want to keep all your stuff.

---

### Post by Arazu on 2009-02-23
Thanks! What sizes would you suggest on a 180GB drive?

---

### Post by taurus on 2009-02-23
How much RAM do you have?  If you have 1GB, I would make 

/ = 50GB
swap = 2GB
/home = whatever left

Make them all primary partitions.

---

### Post by Slim Odds on 2009-02-23
Depending on the size of your drive. I recommend also putting /var and /tmp in their own partitions.

---

### Post by Arazu on 2009-02-23
What are the advantages to having /var and /tmp isolated? How much would you allocate? I've never kept those aside before.

---

### Post by CrucifiedEgo on 2009-02-23
50GB seems a bit large for / in most cases.  My laptop, I used 20GB for /, 4GB for swap(2GB RAM), and the rest in /home.

You'd want to make /var/ into it's own partition, in most cases, in case a log file or other process goes out of control.  That way, you can still (probably) boot the machine to fix the issue, instead of having a full / partition and having to rescue with a livecd.

---


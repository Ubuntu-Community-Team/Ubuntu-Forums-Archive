---
title: "I want to change /dev/sda to /dev/sda1337"
date: 2009-03-09
forum: General Help
---

### Post by Neo_The_User on 2009-03-09
How do I change my entire hard drive partition from /dev/sda to /dev/sda1337? I only want the hard drive to be called that. I want /dev/sda1 and /dev/sda5 to remain the same.

---

### Post by savagenator on 2009-03-09
I don't think that is practical or possible, since each partition is named when it is created. 

Would you can do is mount it under something like /mnt/1337/

---

### Post by kanikilu on 2009-03-09
You can change partition labels in gparted, but it sounds like you want to rename the entire device, not a particular partition.

I suppose you could create a symlink called /dev/sda1337 that points to /dev/sda, but I'm not sure why you would want to or if it would even work.

---

### Post by Neo_The_User on 2009-03-09
In that case, how would I change everything to start with 1337? Like /dev/sda13371 /dev/sda13375 etc etc?

---

### Post by heindsight on 2009-03-09
You could achieve that using udev rules. You can read more about writing udev rules [here.]("http://www.reactivated.net/writing_udev_rules.html")

I'd recommend making /dev/sda1337 a symbolic link to /dev/sda (and similar for sda1 etc) rather than just getting rid of the default names. I can't for the life of me think of any good reason why you'd want to do it though, it doesn't achieve any useful purpose...

---

### Post by Neo_The_User on 2009-03-09
oh ok. Thanks. and I want it because I was somewhere on the Internet reading up something on ext3 or ext4 journaling changing it from journaled to ordered or to writeback and I laughed so hard that I just got the feeling of me having to do this.

---


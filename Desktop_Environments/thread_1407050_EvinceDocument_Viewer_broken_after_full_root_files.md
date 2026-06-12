---
title: "Evince/Document Viewer broken after full root filesystem"
date: 2010-02-14
forum: Desktop Environments
---

### Post by bobstro on 2010-02-14
My root filesystem filled up today while using the system thanks to a misconfigured DVD copying exercise. I had to log out to kill the program (DVD Movie Backup) by logging out. To avoid a future repeat, I deleted my /tmp, and created a symlink to another filesystem. I've rebooted and everything is is working fine except evince, which insists on recovering files, then will not display. 

[EDIT: Apparently the problem was not missing files in /tmp, but that evince doesn't like /tmp symlinked to another location. I deleted my symlink and re-created a /tmp with 0777 and evince is happy again. This won't help if I run out of space again, but at least I can view PDFs properly now.]

- Bob

---

### Post by trevormtb on 2010-03-18
I just installed 9.10 on a 40GB SSD, and I have a symlink to another filesystem for /tmp. I have the same issue: evince shows a blank grey screen, and nothing else.

I'd rather avoid filling up my small root partition with tmp data, does anybody know of a fix for this issue?

---

### Post by mcduck on 2010-03-18
> **trevormtb said:**
> I just installed 9.10 on a 40GB SSD, and I have a symlink to another filesystem for /tmp. I have the same issue: evince shows a blank grey screen, and nothing else.

I'd rather avoid filling up my small root partition with tmp data, does anybody know of a fix for this issue?

/tmp is cleaned automatically when you reboot (if the programs themselves don't remove their temp files even before that), so unless your root partition is way too small you shouldn't really have any problems with temp data filling it... 

Anyway, if you really, really want to have /tmp elsewhere than on your root partition then just create own partition for it instead.

(If I had SSD as my root drive I'd definitely create specific /tmp and /var partitions on a traditional HDD.)

---

### Post by trevormtb on 2010-03-18
Did some research, this has already been reported and fixed in 10.04. 
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/446748]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/446748")

My usual linux setup is to have a small root, LVM partition for home, and a large LVM partition for misc stuff like /tmp, /var, etc, and setting up symlinks for them. I considered a separate partition for tmp, and also var, but then you get the problem of var filling up before tmp. I guess I'm stuck in my ways.

Found out over the past couple of weeks that Ubuntu does not like /var to be a symlink, or anything else for that matter in var. With the number of people getting SSDs, more are trying funky methods like this, and the good thing is bugs are being found and fixed relatively quickly.

---


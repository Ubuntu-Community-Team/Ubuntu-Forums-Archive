---
title: "Disk Mount Problem"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Gooty on 2005-11-17
Very new to Ubuntu, just installed it a few days ago (dual boot with windows).

I created a separate partition that could be shared by Ubuntu and Windows, and I was having trouble getting it to show up in Ubuntu.  So I went into the Administration -> Disks window and try to "enable" this partition.. it asked me where I wanted to mount it, and I just pointed it to my home directory.  Which I now realize was a huge mistake because now it says that 

Your home directory is listed as 'home/gooty' but does not appear to exist; whenever I try to log in, and I can't get to my desktop at all.

It then suggests I correct the problem with a failsafe session.  Which is where my question comes in, how can I revert this change back?  

Thanks in advance.

---

### Post by aysiu on 2005-11-17
Are you able to view /etc/fstab?

---

### Post by Gooty on 2005-11-17
sudo /etc/fstab?  I'm not sure what to type.

edit:  Ok, got it, I can see it.

---


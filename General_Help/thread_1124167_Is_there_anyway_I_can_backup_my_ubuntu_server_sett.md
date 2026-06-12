---
title: "Is there anyway I can backup my ubuntu server settings and configs for easy restore?"
date: 2009-04-13
forum: General Help
---

### Post by qianglong on 2009-04-13
Hi everyone...this is my first post!

Two years ago, I followed some random guide in the cool the ubuntu community to setup my first file server using Ubuntu 6.2 That box has been running perfect for the past 2 years and now its a time for major upgrade. I am going to install the latest version of ubuntu on a Compact flash card while upgrading the file system on my RAID arrays into EXT4. 

My friend who is a linux guru helped me config the box especially the Samba configs and the mounting of different HDs in the sytem. Is there a way I can backup those settings so it can be easily restored when I finish the upgrade?

---

### Post by bruno9779 on 2009-04-13
There are an amount of ways. 
Have a look at this post:

[http://ubuntuforums.org/showthread.php?t=290587](http://ubuntuforums.org/showthread.php?t=290587)

there are many links to help you choose your backup app

---

### Post by hyper_ch on 2009-04-13
I'd go for rsync + ssh + cron

---


---
title: "How do I clear room on this file"
date: 2009-05-07
forum: General Help
---

### Post by AmericanPrincess109 on 2009-05-07
I just went to the terminal and did that "sudo df -h" thing and it said I had no more space on /dev/sda2 

I went to this but it wont let me access it to clear it out.
I'm just really confused, what do I do. Please help me.
:KS

---

### Post by colau on 2009-05-07
Can you please post the result
[html]
sudo fdisk -l
sudo df -h
[/html]

---

### Post by colau on 2009-05-07
Can you please post the result
[html]
sudo fdisk -l
sudo df -h
[/html]

---

### Post by cariboo on 2009-05-08
I posted an answer to your question in this [thread=1109277]thread[/thread]

---

### Post by drs305 on 2009-05-08
I just posted this today to the ubuntu documentation wiki. If the commands cariboo907 aren't enough this guide will walk you through most of the reasons free disk space unexpectedly disappears:
[RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---


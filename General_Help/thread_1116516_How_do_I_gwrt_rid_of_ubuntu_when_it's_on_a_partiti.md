---
title: "How do I gwrt rid of ubuntu when it's on a partition"
date: 2009-04-05
forum: General Help
---

### Post by Zedday on 2009-04-05
Right now I have windows vista and I'm going to partition my hard drive and put ubunto on it, but if I don't like it, how do I get rid of it? Would I boot into windows then format all the other drives that aren't windows? Then how would I put the empty partitions back onto C:? (c: = the one with windows)

Thanks for any help

---

### Post by majamba on 2009-04-05
i am using you are trying to deleted it,

login into ubuntu
open terminal
sudo su (type your password)
aptitude update
aptitude install gparted

launch gparted tool and erase the linux partition

then use windows to resize the free space

---

### Post by GosthShadow on 2009-04-05
or if you decide to uninstall (probably not)
do the following 
1.Insert vista 
2.go to the partition maneger 
3.select ntfs or fat and formate quick or slow you decide
):P

---

### Post by majamba on 2009-04-05
my way works better because he has to use linux and learn a little of commandline

---


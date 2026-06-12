---
title: "only root can mount problem"
date: 2012-02-17
forum: Desktop Environments
---

### Post by forsubhi on 2012-02-17
I have the following error when I plug in my external hard drive , note I add some entries to /etc/fstab 

[IMG]http://i39.tinypic.com/zm1kl3.png[/IMG]

please help me !

---

### Post by Copper Bezel on 2012-02-17
The first thing to check would be the permissions on the entries you've added to fstab. Well, specifically, if you added one for the external drive and labeled it Transcend, what do you have for the permissions on that one?

---

### Post by mcduck on 2012-02-18
> **forsubhi said:**
> I have the following error when I plug in my external hard drive , note I add some entries to /etc/fstab 
please help me !

Perhaps you could show us the entries you added to fstab? If the problem started after adding those new entries, it's more than likely that the entries are the key to solving your problem... ;)

Anyway, did you use UUID's when making the entries in fstab? And is the drive you are now having problems with one of the drives you configured in fstab, or some other drive?

---

### Post by forsubhi on 2012-02-18
thank you for your help 
my problem solved after I deleted the extra entries 
it is stupid question , however I have benefited from noticing  the permission and learn about this file

---


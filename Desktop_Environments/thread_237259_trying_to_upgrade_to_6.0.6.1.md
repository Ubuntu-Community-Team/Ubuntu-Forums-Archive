---
title: "trying to upgrade to 6.0.6.1"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-15
Hi  I am trying to upgrade to 6.0.6.1 from 6.0.6 and I had a friend download the CD for me!  I cant get update maniger to find that I added the CD as one of the update sources.  How do I get it to find the CD.  The CD is listed in software properties but no updates are avlible in the update maniger.  Can someone help me?

Thanks

---

### Post by ardchoille on 2006-08-15
> **Magiczero said:**
> Hi  I am trying to upgrade to 6.0.6.1 from 6.0.6 and I had a friend download the CD for me!  I cant get update maniger to find that I added the CD as one of the update sources.  How do I get it to find the CD.  The CD is listed in software properties but no updates are avlible in the update maniger.  Can someone help me?

Thanks

All you need to do to upgrade to 6.06.1 LTS is:

```

sudo apt-get update && sudo apt-get dist-upgrade

```

If you have been keeping your system up to date, then you are running 6.06.1 LTS.
You can check which version you are running by opening a term and running:

```

lsb_release -a | grep Description

```

---

### Post by orb9220 on 2006-08-15
lsb_release -a is faster to type and shorter. 

And yes if you have been doing the updates then you are 06.1 that is not an upgrade so much as the orig  6.06 plus all the updates since july all rolled into one. 

No more triple digits upgrades after base install. Yea!

---


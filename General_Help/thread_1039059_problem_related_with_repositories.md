---
title: "problem related with repositories"
date: 2009-01-14
forum: General Help
---

### Post by dsharmaa on 2009-01-14
Hi,

I am trying to use these two steps but I think there is some problem with ubuntu repositories. Can anybody please help me?

sudo apt-get build-dep linux-image-2.6.22-14-generic linux-ubuntu-
modules-2.6.22-14-generic
apt-get source linux-image-2.6.22-14-generic linux-ubuntu-
modules-2.6.22-14-generic

And I am using ubuntu7.10 and I am getting following messages

root@ubuntu-desktop:/usr/src# apt-get source linux-image-2.6.22-14-generic linux-ubuntu-modules-2.6.22-14-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to find a source package for linux-source-2.6.22

thanks in advance,

Cheers
DP

---

### Post by mikewhatever on 2009-01-14
I think the source code repository is not enabled by default. Did you enable it?

---

### Post by dsharmaa on 2009-01-14
Hi,

Thanks for your reply, 
I am actually a new bee so I don't think I have enabled any source repository. Do I have to go in software sources and enable source code options. 

Cheers
DP

---

### Post by mikewhatever on 2009-01-14
Yes, I think so.

---

### Post by dsharmaa on 2009-01-14
Many thanks it is working now !!!
Cheers
DP

---


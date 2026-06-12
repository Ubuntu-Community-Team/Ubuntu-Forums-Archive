---
title: "locking down gnome"
date: 2009-05-27
forum: Desktop Environments
---

### Post by Darryl Moore on 2009-05-27
what is the best way to lock down gnome in a NFS networked environment? 

The HowTo at: [https://help.ubuntu.com/community/CorporateUbuntu](https://help.ubuntu.com/community/CorporateUbuntu) gives the basic information, but it looks like it would only work for a single machine environment. What about when I have a couple dozen on the network I want to do the same think with?

I think my options are as follows

1) make the changes to the /home/user/.gonf directory on the server which is already NFS exported and lock the files down by making root own them and only allowing root to have write access

2) make the changes to /etc/gconf/gconf.xml.mandatory then use scp or a login script to mirror those changes in the various workstations. 

3) make the changes to /etc/gconf/gconf.xml.mandatory as above, but then export the /etc/gconf directory and mount it on all the workstations.

Which of these would work best, or is there another option I am overlooking?

Thanks,
darryl

---


---
title: "NFS Mount Shows Multiple Times in the Places"
date: 2011-03-25
forum: Desktop Environments
---

### Post by peshko-lnx on 2011-03-25
I already posted this on the Network Support with no real solution:

[http://ubuntuforums.org/showthread.php?t=1713143](http://ubuntuforums.org/showthread.php?t=1713143)

I have the follwoing fenomenan. In my /etc/fstab I have an entry to automatically mount my NAS. Here is my entry:

192.168.1.10:/mnt/array1/My_NAS    /media/My\040NAS    nfs    _netdev,
auto,rw,hard,users,intr    0    0

When my laptop boots it successfully mounts the NFS NAS and I get an  icon "My NAS" on my dekstop that points to the NAS. If I double click on  the icon it opens my file browser and I can browse thru my NAS fodlers.

What I see on the left hand side of the file browser is that I have to  entries for My NAS. One of it has a button to shows that it is mounted  and the other does not.

If I go to Places I also see 2 entries for "My NAS". One of it takes me  to browsing the NAS and if I click on the other it says "Unable to mount  ... busy or already mounted". Which makes sense.

If I unmount everything and mount everything back, it seems to be ok.

The question is why do I have 2 (two) entries for the same thing?

---

### Post by peshko-lnx on 2011-03-25
Forgot to mention that I just tested this on a plain new 10.10 instalaltion and the problem is still there.

---

### Post by peshko-lnx on 2011-03-26
Bump...Anyone?

---


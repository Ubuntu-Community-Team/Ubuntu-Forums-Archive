---
title: "mounting windows partitions"
date: 2005-12-09
forum: General Help
---

### Post by Lin-X on 2005-12-09
I dual booted Win98 with the Hedgehog and was able to see my main Windows partition by typing some stuff into a terminal. Fine. I left Ubuntu temporarily to try a new Suse distro, but things didn't work out for me with it, so here I am with Badger installed. My problem: the instructions I used before don't work. When I type
sudo cp/etc/fstab/etc/fstabbackup it tells me no such directory. I struggled with this
for awhile but got nowhere. Can someone please help me out?:confused:  I have lots of neat linux tutorials and other helpful information stored in my fat32 partition.
Thanks... and it's good to be back here!
    Sorry for such a stupid post!!! I did a search and easily found what I needed.:oops:

---

### Post by amohanty on 2005-12-09
> sudo cp/etc/fstab/etc/fstabbackup

Instead of that use this:

> sudo cp /etc/fstab /etc/fstabbackup

mind the spaces.
HTH

---


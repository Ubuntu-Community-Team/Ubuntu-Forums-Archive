---
title: "First day using Ubuntu and something went wrong"
date: 2005-12-28
forum: General Help
---

### Post by d11wtq on 2005-12-28
Hi,

I'm pretty used to Linux and I've been using Gentoo for quite a while.  I'm experimenting with Ubuntu.  First impressions are excellent for Desktop users.... not so good for servers (I'd prefer Gentoo personally for my VDS server).

I left my Laptop running in Ubuntu last night and when I woke up it had powered off :shock:   Fair enough... Ubuntu does attempt to set things up for new-to-linux users so it may be a default config to power off after an hour idle or so.

I powered the laptop back on and booted into Ubuntu again.... GNOME refused to started with errors about .ICEAuthority not being writable.  At this point I thought gahh... just go back to Gentoo so I rebooted into Gentoo.  I'd forgotten that I'm using the same /home on both distros so I got the same issue in Gentoo.

I chown'd the file back to the correct user and it's all working now.... what would have caused this though?

Thanks,

d11wtq

---

### Post by yaaarrrgg on 2005-12-28
i had that problem once too.  for me, i believe i had launched an application as root (well, actually from a sudo -i shell), and this changed or created the config file as being owned by root.  then, when i went back as a regular user, i noticed the problem.

---


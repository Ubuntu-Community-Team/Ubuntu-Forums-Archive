---
title: "Ubuntu 9.04 Graphics card / Display Problem"
date: 2009-04-23
forum: General Help
---

### Post by wavefront on 2009-04-23
Hi im a total newb to ubuntu but iv always fancied getting out from grasps of Microsoft and since 9.04 was released today I thought I whold be a good excuse to give it a go, and iv been loading it and iv spent the entire day installing different apps. However about an hour ago when I downloaded the ATI Graphics controller (I think that was what it was called) from within downloads  in Add/Remove programs. the problem is ever since I rebooted I cant see the desktop its just a black screen with a whiteline at the bottom and I have no idea how to recover  if you could help me out I would rely appreciate it as it will be and entire day wasted if I have to install again
  Many thanks for you help
  Ben :)
  Ohh PS: im running a dell vostro 1000 laptop and the Gfx card is a ATI Radeon Xpress 256 MB HyperMemory (integrated)Radeon X1100

---

### Post by ubu-for on 2009-04-23
Start Ubuntu in recovery mode and enter into the console ...

```
sudo dpkg-reconfigure xserver-xorg
```

... and restart Ubuntu.

Hope it helps!

---

### Post by Demonizer on 2009-04-23
> **ubu-for said:**
> Start Ubuntu in recovery mode and enter into the console ...

```
sudo dpkg-reconfigure xserver-xorg
```... and restart Ubuntu.

Hope it helps!

Thanks, same problem here.. it may help well I hope it does because if it doesn't then another reinstall is coming up. :P

---


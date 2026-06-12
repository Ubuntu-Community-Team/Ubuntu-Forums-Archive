---
title: "downloaded packages restored to cache... what now?"
date: 2005-08-16
forum: Desktop Environments
---

### Post by rstana on 2005-08-16
Folks,

I have downloaded a lot of packages and made a backup according to ubuntuguide. The file created was apt.tgz

I have managed to restore it (sudo tar zxvf apt.tgz -C /) and the deb packages are now in /var/cache/apt/archives if I am not mistaking

BUT! how do I install them all at once? Is there any way how I can edit source.list to be able to do it all at once in kynaptic? Or do I need to install all manually using dpkg -i

any help appreciated. thanks

---

### Post by sargo on 2005-08-16
I supose that the packages are correct and match with the Ubuntu version. Select them in Kynaptic or in Synaptic and the program takes the packages from the /var/cache/apt/archives.

It worked for me...  :neutral:

---

### Post by rstana on 2005-08-17
the packages are correct, that I am sure of, but I don't think I can see them in kynaptic which is a problem...

---

### Post by zAo on 2005-08-17
Yuo can install them all by running
```
sudo dpkg -i /var/cache/apt/archives/*.deb
```

---


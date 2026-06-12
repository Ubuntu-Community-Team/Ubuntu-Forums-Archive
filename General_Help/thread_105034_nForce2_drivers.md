---
title: "nForce2 drivers"
date: 2005-12-17
forum: General Help
---

### Post by Hancoque on 2005-12-17
I used the search on this but only found old threads that belong to previous Ubuntu releases.

My question is as follows: Under Windows I use the mobo drivers from nvidia.com because they do not only enable you to use the onboard network and sound, but also because they provide better performance and stability than the Windows default drivers. Those three drivers are installed in addition to network and sound: GART, Memory controller and SMBus. Also, the sound drivers provide hardware mixing and overall acceleration features. As far as I understand built-in drivers (like graphics drivers) they only let you use a hardware but mostly with very low performance because there's no hardware acceleration at all. As I'm interested in getting the same performance under Linux (for instance in Quake 4) as under Windows, I'd like to know how good the built-in Ubuntu drivers are and if the nforce driver package from nvidia.com is any better or not.

---

### Post by BathroomNinja on 2005-12-17
Linux has had mature, native support for the Nforce 2  chipset since kernel 2.4.20; so everything should work fine.

To install Nvida drivers for video:


Automatix
[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)


OR


Nvidia HOWTO
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

These will get the latest Nvida video drivers for linux.  As to the performance...  It's good but not as good as Windows.  Obviously, Nvidia has more Windows users than Linux users, so they have more guys working on drivers for Windows.  But they DO have very good support for linux with their native drivers that you will be installing via one of the above links.  Game play for native games is almost the same as native windows.  I don't notice any real difference.

---


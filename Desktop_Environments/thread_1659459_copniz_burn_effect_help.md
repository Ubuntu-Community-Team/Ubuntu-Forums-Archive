---
title: "copniz burn effect help"
date: 2011-01-04
forum: Desktop Environments
---

### Post by ryan andrews on 2011-01-04
well i installed compiz on my ubuntu 10

after giving command ccsm command in terminal it says no python pakages found , dont wory its optional


when the setting manager of compiz opened i did not foud any enable add on in effect menu 


there was only standard animations like glide , magic lamp 

and i did not find any burn effect ,,


  i am well aware that you have to enable animation add  on but i didnot find any option like this please tell me what went wrong!!

](*,)

---

### Post by ellalan on 2011-01-04
Which version of Ubuntu(10.04 or 10.10),which version of Compiz? have you installed Fusion icon, ubuntu-restricted-extras in Synaptics package manager.
If you have Compiz 8.2, burn effect should be in as default.

---

### Post by piquat on 2011-01-04
I have 8.2 and I had to install compiz-fusion-plugins-extra to get the burn effect.  That installed "Animations Addon" in effects in compiz.  Without that, I have no burn effect, among others...

Edit:  Almost forgot, that plugin is in the repos.

---

### Post by realzippy on 2011-01-04
> **ellalan said:**
> Which version of Ubuntu(10.04 or 10.10),which version of Compiz? have you installed Fusion icon, ubuntu-restricted-extras in Synaptics package manager.
If you have Compiz 8.2, burn effect should be in as default.


Fire plugin is **not** installed by default,also *fusion-icon* or *ubuntu-restricted-extras* have nothing to do with the "paint fire on desktop" compiz plugin.
You have to install *compiz-fusion-plugins-extra* and restart compiz.

```
sudo apt-get install compiz-fusion-plugins-extra
```

---

### Post by ellalan on 2011-01-04
> **realzippy said:**
> Fire plugin is **not** installed by default,also *fusion-icon* or *ubuntu-restricted-extras* have nothing to do with the "paint fire on desktop" compiz plugin.
You have to install *compiz-fusion-plugins-extra* and restart compiz.

```
sudo apt-get install compiz-fusion-plugins-extra
```
Thank you.

---

### Post by ryan andrews on 2011-01-08
well thanks i used that code and it solved my problem!!!

cheers!!!!!!!!!:D:popcorn:

---


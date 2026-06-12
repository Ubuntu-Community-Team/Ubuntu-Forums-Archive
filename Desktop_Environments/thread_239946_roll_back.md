---
title: "roll back?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by drtvasudevan on 2006-08-20
if i think a updated package is causing a problem, is it possible to roll back by deleting that package? i mean does it automatically go to the old version or i have to fetch that old version and install?

---

### Post by KhaaL on 2006-08-20
I think you have to get the old one and install it. AFAIK, there is no way to roll back changes - a feature I really miss from xp since it gave some sense of security while you tried out things...

---

### Post by codejunkie on 2006-08-20
you can roll back packages in synaptic, first search for the package, click on the package you want to downgrade then go to Package and choose Force Version click the drop down box and choose the version prior to your current one and click apply. you'll also need to lock that version by clicking the package and then go to Package then choose Lock Version or it will be upgraded the next time you upgrade using synaptic.

---

### Post by drtvasudevan on 2006-08-20
wow!
that is exactly what i wanted.
so there is no need to download again?
since synaptic not working is the problem it will be ironic!

---

### Post by codejunkie on 2006-08-20
> **drtvasudevan said:**
> wow!
that is exactly what i wanted.
so there is no need to download again?
since synaptic not working is the problem it will be ironic!
you souldn't have to download any packages again, once there downloaded they are stored in the /var/cache/apt/archives directory, you can also navigate to that directory in nautilus and double click on the package you want reinstalled and it should reinstall it, or open a terminal and run 
```
cd /var/cache/apt/archives
``` then run ```
sudo dpkg -i packagename+version.deb
``` if synamptic is not working, but exactly how is synaptic broken could you decribe the problems your having with it.

---

### Post by drtvasudevan on 2006-08-20
thanks!
synaptic worked for sometime and does not after a few updates.
reason seems to be something that was updated though i cant be sure.
all was well till i installed automatix and updated twice. msttcorefonts failed but then i removed it from wanted list.
network setting being the same, being able to browse to the required pages via browser...i dont know why i cant update anymore.
a few times that i tried i ended up with cant connect msg.
so i copied the dependencies from synaptic error msg and dowloaded and installed via browser. now if i want something i have to follow this tedius route, ask synaptic to get it- times out-copy the dependencies and the url - go to the site via browser and download.
this of course cant work long as the sources list will get obsolete,

---

### Post by codejunkie on 2006-08-21
> **drtvasudevan said:**
> thanks!
synaptic worked for sometime and does not after a few updates.
reason seems to be something that was updated though i cant be sure.
all was well till i installed automatix and updated twice. msttcorefonts failed but then i removed it from wanted list.
network setting being the same, being able to browse to the required pages via browser...i dont know why i cant update anymore.
a few times that i tried i ended up with cant connect msg.
so i copied the dependencies from synaptic error msg and dowloaded and installed via browser. now if i want something i have to follow this tedius route, ask synaptic to get it- times out-copy the dependencies and the url - go to the site via browser and download.
this of course cant work long as the sources list will get obsolete,
wow that sounds like a headache i dont know an exact answer on how to fix this but here is a couple of things to try
1: ```
run sudo dpkg --configure -a
```just incase some packages are not fully configured and hanging somthing up.

2: reinstall synaptic just incase something got broken by running ```
sudo apt-get update
```then ```
sudo apt-get install --reinstall synaptic
```

3:create a new user account and make sure to grant it administrator privlidges, login using this account and try synaptic if it works using this account, it means some file permissions have got changed under your user account.

---

### Post by drtvasudevan on 2006-08-21
> **codejunkie said:**
> wow that sounds like a headache i dont know an exact answer on how to fix this but here is a couple of things to try
1: ```
run sudo dpkg --configure -a
```just incase some packages are not fully configured and hanging somthing up.

ok

> 2: reinstall synaptic just incase something got broken by running ```
sudo apt-get update
```then ```
sudo apt-get install --reinstall synaptic
```

seeing the update is not working from synptic, apt get, aptitude i hope have not.

[QUOTE:create a new user account and make sure to grant it administrator privlidges, login using this account and try synaptic if it works using this account, it means some file permissions have got changed under your user account.[/QUOTE]

idea! will try

---


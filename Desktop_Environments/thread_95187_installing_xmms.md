---
title: "installing xmms"
date: 2005-11-25
forum: Desktop Environments
---

### Post by ikki_72 on 2005-11-25
how am i gonna be able to install this thing. anyone? say that i extracted the file  on desktop.

---

### Post by invalid on 2005-11-25
```
sudo apt-get install xmms
```

Cheers,
Cb

---

### Post by aysiu on 2005-11-25
Open up a terminal (Applications > Accessories > Terminal) and type this in: ```
cd Desktop
rm -rf *xmms*
sudo apt-get update
sudo apt-get install xmms
``` Now it's installed. Here's the translation:

Go to the desktop directory.
Delete the file you downloaded but didn't need to.
Update your online repositories list.
Download and install XMMS and all of its dependencies from the online repositories.

---

### Post by neobloodline on 2005-12-01
Thanks a million this help me too..

---

### Post by ikki_72 on 2005-12-04
do it on terminal, but it keeps saying that 'cannot get ubuntu hostname' or something. any way i can be root with gui?

---

### Post by linbetwin on 2005-12-04
You can install xmms in Synaptic, but you must enable the universe (or multiverse?) repository.

---

### Post by Gray. on 2005-12-04
To enable universe/multiverse repositories:
System > Administration > Synaptic Package Manager
Settings > Repositories
Settings > Tick "Show disabled software sources" > Close
Tick all entries that have Universe or Multiverse > OK
Synaptic should automatically reload to include the new repos.
Voila!

---

### Post by tomwell on 2005-12-04
Hey,

You will also need to enable the different multimedia plugins, gs streamer/lame/wma etc so that you can make it your default Media player... It kicks once its setup... loads of tutorials on that in the forums....

Peace

Tom

---


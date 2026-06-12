---
title: "Configuring apt _after_ install"
date: 2005-09-12
forum: Desktop Environments
---

### Post by carlos1 on 2005-09-12
I had to bypass configuring apt in order to get Kubuntu to install.
Now that I've done that I can't figure out how to configure apt to use it. 
I checked /etc/apt/sources.list but there is nothing in there except a line pointing to the cdrom.
I checked the online howtos but they are concerned with adding various repositories. Is that all I need to do - and if so, which repositories should I add? 
Do I just have to add them to /etc/apt/source.list and then run it again?

---

### Post by KingBahamut on 2005-09-12
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by carlos1 on 2005-09-13
Thanks.
I just cut and pasted the un-commented file (change the "us" at the beginning of the archives to my local mirror) and it worked like a charm.

---

### Post by KingBahamut on 2005-09-13
Glad to be of service. 

<Gives and Alfred-like Bow>

---


---
title: "getting kde 3.5"
date: 2006-04-11
forum: Desktop Environments
---

### Post by dq101 on 2006-04-11
how can i update to kde 3.5 from the one that i got kde 3.4?

i installed from here 
[https://wiki.ubuntu.com/InstallingKDE](https://wiki.ubuntu.com/InstallingKDE)

but i only wanted to use the kde-core install so how do i get kde 3.5 core?

---

### Post by badrinarayan on 2006-04-11
For updating to KDE 3.5, you need to add new repositories. See [http://kubuntu.org/announcements/kde-352.php](http://kubuntu.org/announcements/kde-352.php)

To do so, open a terminal and issue the following commands:
```
sudo sh -c 'echo deb http://kubuntu.org/packages/kde352 breezy main >>/etc/apt/sources.list'
sudo aptitude update
sudo aptitude install kde-core
```

To upgrade all your packages (this will also upgrade KDE), type
```
sudo aptitude dist-upgrade
```

---

### Post by dq101 on 2006-04-11
i did what you said the first box then the second and it still says kde 3.4

---

### Post by dq101 on 2006-04-12
anyone know what went wrong?

---


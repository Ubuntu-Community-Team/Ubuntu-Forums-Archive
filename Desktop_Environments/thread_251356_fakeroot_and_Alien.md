---
title: "fakeroot and Alien"
date: 2006-09-05
forum: Desktop Environments
---

### Post by cosworthgizmo on 2006-09-05
hi.. 

i have installed the alien package so i where sopoused to be able to install deb package, but every time i try to convert a package to a deb,  it just says "unknown type of package" and i have done it before which the same package .. what is wrong ??

and i can i use fakeroot to convert a bin package to a deb package ??

and how ??

---

### Post by taurus on 2006-09-05
Are you trying to convert .rpm to .deb???

---

### Post by cosworthgizmo on 2006-09-05
> **taurus said:**
> Are you trying to convert .rpm to .deb???

yes i am.. and have tried to get another package.. its the java package as a bin package and rpm package.. 

i also have some troubles installing the bin.. can u also help there ?? :)

---

### Post by LKRaider on 2006-09-05
For alien, try like this:
```
fakeroot alien -d Package.rpm 
```

For Java, get it from the repos:
```
apt-get install sun-java5-bin 
```
Note that you need the multiverse repository enabled.
More info here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by taurus on 2006-09-05
Just change the permission on the .bin and run it as

```

chmod 755 <package_name>.bin
sudo ./<package_name>.bin

```

---


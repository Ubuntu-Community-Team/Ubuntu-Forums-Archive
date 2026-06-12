---
title: "How to receive updates of LXDE?"
date: 2013-11-13
forum: Desktop Environments
---

### Post by arroy_0209 on 2013-11-13
After upgrading to ubuntu12.04 (from 10.04), I installed LXDE desktop environment for convenience. Now I am confused whether I have received the security or other updates related to LXDE. So far I have relied on the automatic update message of ubuntu from time to time (typically twice a month) but I do not remember ever having received updates regarding LXDE. That is strange since I had installed LXDE more than one year ago. How do I check if LXDE updates have really been received or not?

Also if I remember correctly the updates of the version I installed woluld be available till a period much shorter than support period of ubuntu 12.04. In that case should I uninstall existing version of LXDE and reinstall latest version of LXDE?

---

### Post by TheFu on 2013-11-13
It all depends on how you installed it.

If you used the normal repositories, all is good, provided you either have automatic updates on or perform them using the normal tools like apt-get/aptitude or whatever GUI tool Ubuntu is pushing this release.

If you installed using a PPA, .DEB file or, heaven forbid, a tgz ... then you have accepted responsibility to manually perform any updates.

12.04 desktop and server are supported for 5 yrs - so until Apr 2017.

---

### Post by Bashing-om on 2013-11-13
arroy_0209; Hi !

To see what is and what is not:
Update the system to make sure all is current; Terminal command:
```

sudo apt-get update
sudo apt-get upgrade

```
Now lets look at the LXDE desktop:
```

apt-cache policy lxde

``` note "lxde" as lower case.
Which shows what is installed and what is available for installation.

ubuntu's package management system ->
[INDENT][INDENT][INDENT]a wonder to behold
[/INDENT][/INDENT][/INDENT]

---


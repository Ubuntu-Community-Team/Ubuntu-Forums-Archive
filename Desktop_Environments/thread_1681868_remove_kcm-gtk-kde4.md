---
title: "remove kcm-gtk-kde4"
date: 2011-02-04
forum: Desktop Environments
---

### Post by Kingcheese26 on 2011-02-04
hi guys, i installed kde on my ubuntu system, but all my gtk apps look really ugly. i messed around with a few 'solutions' but none of them seemed to work. i removed the 'kde-standard' package thinking i would install the 'kubuntu-desktop' package instead, but it didn't work :confused: the package is called kcm-gtk-kde4 and i can't remove it. here is the output if i run apt-get remove kcm-gtk-kde4:

```
sudo apt-get remove kcm-gtk-kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kcm-gtk-kde4
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
1 not fully installed or removed.
After this operation, 2,751kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210000 files and directories currently installed.)
Removing kcm-gtk-kde4 ...
cd: 2: can't cd to /usr/share/kubuntu-default-settings/
dpkg: error processing kcm-gtk-kde4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kcm-gtk-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any ideas?
thanks!

---

### Post by vietnam_forever on 2011-02-22
If you are still stuck

I created the missing directory 
sudo mkdir /usr/share/kubuntu-default-settings/

then 

sudo apt-get -f install


and my problems went away :)

---


---
title: "how to revert to default settings in compiz fusion???"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by threeonethree on 2007-08-06
hi, i would like to revert to default settings in compiz fusion.. i go to profiles button and click import button but i only get a file open dialog box which wants me to open a .profile file but i dont where it is!!!

please help me .. and is there any way to revert to default settings in compiz fusion ? like deleting some configuration file so it uses default? please help me

---

### Post by threeonethree on 2007-08-06
help??

---

### Post by Waappu on 2007-08-07
Hi

Type in terminal```
metacity --replace
mv ~/.compizconfig ~/compizconfig_old
```
and start compiz again

---

### Post by threeonethree on 2007-08-08
that command didnt work .. i went to my home dir then checked show hidden files but there isnt any .compizconfig folder in my home dir? help

---

### Post by Mr Greencastle on 2007-08-08
Are you sure?
Try typing:
```
cd ~/.compizconfig
```

Does the terminal say that this directory doesnt exist?

---

### Post by threeonethree on 2007-08-11
the folder is there now .. it was renamed because of 

> mv ~/.compizconfig ~/compizconfig_old

but renaming or even delein that folder doesnt work .. same settings .. mayb they are saved somewhere else on my computer? what do i do help.. and i wont remove and install compiz fusion again .. seems like a risky procedure because its removing lot of apps with it

---

### Post by threeonethree on 2007-08-11
anyways if i find solution to this problem i will post it on my blog [www.knb.phpnet.us](www.knb.phpnet.us)

---


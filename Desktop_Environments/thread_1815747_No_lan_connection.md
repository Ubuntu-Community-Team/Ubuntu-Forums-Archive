---
title: "No lan connection"
date: 2011-07-31
forum: Desktop Environments
---

### Post by inspire mind on 2011-07-31
Total noob to linux,i have a desktop and downloaded new version of ubuntu after loading live dvd i have no ethernet connection the lan chipset is realtek RTL8111DL any ideas ?

Also currently running win7 hoping to change to linux only if this can be fixed.

---

### Post by varunendra on 2011-08-01
Open a terminal, enter these commands one-by-one and post back their outputs:
```
ifconfig -a
```
```
sudo lshw -C network
```
```
lsmod | grep -i rtl
```
and
```
route -n
```

Just copy the outputs using your pointer, and paste it in your new post. Then select (only) the pasted output and click on the '**#**' symbol at the top of the editing box. This will create 'code' tags around the pasted text which makes it well formatted and easy to read.

---


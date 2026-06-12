---
title: "Installed LXDE, now can't use Ubuntu 3D"
date: 2012-06-21
forum: Desktop Environments
---

### Post by WMichael on 2012-06-21
I thought to give LXDE a go on ubuntu, I've some friends do it so I thought it wouldn't do anything wrong on the ubuntu machine. 

When I went on LXDE environment nothing was wrong, its just when I went back onto Ubuntu 3D it loads up but I don't get Unity. Unity comes up in Ubuntu 2D but not 3D. 

I even went to the point of uninstalling LXDE, no change. 
Reinstall unity through software centre, no change. 

Could someone help me out please.

Thanks.

---

### Post by ringo28 on 2012-06-21
this nog unity , try Gnome shell.... :) i begin to love this.. :)

---

### Post by ringo28 on 2012-06-21
go to your file.... unlock hidden directory.., look voor compiz, delete  what in that directory... go to terminal; en trij compiz --replace                mayby it will help... in that directory compiz-1    its the sessions information holdup, so reinstall unity wont work.. delete with in that, en mayby help

---

### Post by WMichael on 2012-06-22
Ok ringo28, I have deleted both folders, and did "compiz --replace". 

It hasn't got up the unity bar but it has made made all my start up applications load faster on 3D(Weird).

---

### Post by Shadius on 2012-06-23
> **WMichael said:**
> Ok ringo28, I have deleted both folders, and did "compiz --replace". 

It hasn't got up the unity bar but it has made made all my start up applications load faster on 3D(Weird).

If the Unity Launcher isn't loading you can try in Terminal:
```
unity --reset
```

---

### Post by WMichael on 2012-06-24
thanks Shadius it nows works.

---


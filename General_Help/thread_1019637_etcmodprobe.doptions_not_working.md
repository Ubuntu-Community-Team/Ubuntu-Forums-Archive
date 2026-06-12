---
title: "/etc/modprobe.d/options not working"
date: 2008-12-23
forum: General Help
---

### Post by [woodstock] on 2008-12-23
Hi there!

I rescently updated to Intrepid via dist-upgrade on a MacBook Pro. While trying to configure it properly, I noticed, that there seems to be an errror with **/etc/modprobe.d/options**.

To change the FN-key behavior, I would like to load the module **hid** with the parameter
```
hid pb_fnmode=2
```
and so I added it to the **/etc/modprobe.d/options** file.

However, it does not work. Checking the state of the module after booting always results in
```
 $cat /sys/module/hid/parameters/pb_fnmode
  1
```

If I do this manually, I get
```
$modprobe hid pb_fnmode=2
$cat /sys/module/hid/parameters/pb_fnmode
2
```

but then, the module **usbhid** is still needed. And ***after*** loading it we're back to the original state. :-(

```
$modrobe usbhid
$cat /sys/module/hid/parameters/pb_fnmode
1
```

Is this a bug or a feature?


Meanwhile I added a line in /etc/init.d/bootmisc.sh
```
 echo "2" > /sys/module/hid/parameters/pb_fnmode
```
which does the job, however, I think this isn't as nice as loading the module with a parameter.

Aside from aesthetical considerations, the question remains, if it can be expected that another module overwrites the parameters of an already loaded one.

---

### Post by cyberdork33 on 2008-12-28
i think your syntax is wrong:
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

---


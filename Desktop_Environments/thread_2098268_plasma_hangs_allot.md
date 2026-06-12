---
title: "plasma hangs allot"
date: 2012-12-26
forum: Desktop Environments
---

### Post by zander1013 on 2012-12-26
hi,

i am using the latest edition of kubuntu 12.10.

i have recently switched to kubuntu after using ubuntu for perhaps 5 years.

plasma is hanging allot when i try to switch between pages or try to launch something like dolphin.

the md5sum of the install image did check with the reference.

i am using 12.10 to run a dell netbook with 1.8Ghz atom processor, 2GB ram, 30GB SSD, built in bluetooth, wifi.

one issue that may be causing this is i believe this dell mini 9 has(had) a proprietary graphics card but it has been well supported in the past by ubuntu. there have never been any problems running this machine with ubuntu.

it seems so close to running perfectly. i feel there must be a solution we can find.

please advise.

---

### Post by catlover2 on 2012-12-26
Try toggling between OpenGL and Xrender in the Advanced tab of Desktop Effects in System Settings; that would probably rule out a graphics issue.

Also, please post the output of the below commands so we can know what graphics card/driver you have.

```
lspci | grep VGA ; echo ; glxinfo | grep direct ; echo ; xdriinfo
```

---

### Post by zander1013 on 2012-12-26
i found this info about running a mini 9 with linux. there are some notes about the graphics card here. my particular unit is a generation later than the one on the link

[http://www.linlap.com/dell_inspiron_mini_9](http://www.linlap.com/dell_inspiron_mini_9)

the symptoms i am observing are not like the ones described on the link but perhaps something i could add to xorg.conf to get it straightened out? i feel it is a problem with X.

thank you.

---

### Post by zander1013 on 2012-12-26
hi,

i switched to Xrender things have not hung switching around to get this from a terminal...

> alonzo@eartha:~$ lspci | grep VGA ; echo ; glxinfo | grep direct ; echo ; xdriinfo
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)

The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils

Screen 0: i915
alonzo@eartha:~$ 


---

### Post by zander1013 on 2012-12-26
i switched to XRrender from OpenGL but i am having trouble switching back to OpenGL.

trying to restore defaults leaves me in XRender where i seem stuck now.

---

### Post by zander1013 on 2012-12-26
here is the results of the diagnostic line given after installing glxinfo...

> alonzo@eartha:~$ lspci | grep VGA ; echo ; glxinfo | grep direct ; echo ; xdriinfo
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)

direct rendering: Yes

Screen 0: i915
alonzo@eartha:~$ 


---


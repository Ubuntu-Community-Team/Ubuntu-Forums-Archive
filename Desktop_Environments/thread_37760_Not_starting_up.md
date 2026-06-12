---
title: "Not starting up"
date: 2005-05-28
forum: Desktop Environments
---

### Post by catastrophee on 2005-05-28
ubuntu wont start up now it just loads like normal with the black screen after i select to boot linux and then goes black. 

I got a message one time and it was something X. It failed to work and it showed me 2 logs of what went wrong. 

Im guessing it has to do with the nvidia driver i installed..... well any suggestions ?

---

### Post by twisted_steel on 2005-05-28
If it's just X that is broken, you should be able to switch to a terminal by using [crtl] + [alt] + [f1]. Login and you can then ```
sudo nano -w /etc/X11/xorg.conf
``` Then look for a line with the driver and (if you remember what it was), change it back to the original. The section for my ATI card looks like this:
```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver	  "fglrx"
	BusID	   "PCI:1:0:0"
EndSection

```

---


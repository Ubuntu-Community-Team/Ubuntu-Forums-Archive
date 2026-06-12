---
title: "Help needed with &quot;build&quot;"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Psquared on 2005-10-16
Anybody know what is going on here? I have downloaded the build-essentials twice now and still I get stuck at this point.

> peyre@PTL-Mobile:~/Desktop/Downloads/ieee80211-1.0.3 $ make
Checking in /lib/modules/2.6.12-9-686/build/ for ieee80211 components...

CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT=m
CONFIG_IEEE80211_WPA=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
Above definitions found.  Comment out? [y], n y
sed: can't read /lib/modules/2.6.12-9-686/build//build/.config: No such file or directory
make -C /lib/modules/2.6.12-9-686/build M=/home/peyre/Desktop/Downloads/ieee80211-1.0.3 MODVERDIR=/home/peyre/Desktop/Downloads/ieee80211-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
peyre@PTL-Mobile:~/Desktop/Downloads/ieee80211-1.0.3 $


---

### Post by yage on 2005-10-16
[QUOTE=Psquared]sed: can't read/lib/modules/2.6.12-9-686/build//build/.config: No such file or directory[/QUOTE]
Here you probably have the error.. I don't know bacause i don't see the hole output from this but it seems you have entered /lib/modules/2.6.12-9-686/build/ at some point. Leave out the last "/build/" and try again.
Hope this does it for you ;)

EDIT: Cleanup

---

### Post by Psquared on 2005-10-16
[QUOTE=yage]Here you probably have the error.. I don't know bacause i don't see the hole output from this but it seems you have entered /lib/modules/2.6.12-9-686/build/ at some point. Leave out the last "/build/" and try again.
Hope this does it for you ;)

EDIT: Cleanup[/QUOTE]

Can't leave out the last "/build/" because it is part of the "make" routine for the ieee80211 module. Check the first line when I change into the directory and then type make. This is the output.

---


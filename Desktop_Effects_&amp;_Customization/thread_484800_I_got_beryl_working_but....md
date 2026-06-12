---
title: "I got beryl working but..."
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by Leela on 2007-06-26
Well, I got beryl working with the cube and stuff, only problem is, I lost my title bar... I know a lot of people asked about this, and alot of people had answers, well, I tried what they did, but it just doesn't work..
Here's a screenshot:
[[IMG]http://img391.imageshack.us/img391/2536/screenshotek5.th.png[/IMG]](http://img391.imageshack.us/my.php?image=screenshotek5.png)
Hope someone could help me out with this...

---

### Post by speaker219 on 2007-06-26
I had the same exact problem a while ago, i just used the following command to uninstall everything that has to do with Beryl:
```
sudo apt-get --purge remove beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-bindings emerald libberyldecoration0 libberylsettings0 libemeraldengine0


sudo apt-get autoremove
sudo apt-get autoclean
rm -r ~/.beryl

rm -r ~/.emerald
rm -r ~/.beryl-managerrc
```

Beryl worked fine after I removed everything and then reinstalled it, but I reccomend you get Compiz Fusion instead, which is replacing Beryl and beryl will no longer be supported.
It is a combination of Beryl and Compiz. The howto says it's not for beginners, but I installed it very easily and it seems to work smoother than beryl and seems to be more stable. There is a howto on Compiz Fusion on a sticky at the top of the forum.

---

### Post by AriciU on 2007-06-26
> **Leela said:**
> Well, I got beryl working with the cube and stuff, only problem is, I lost my title bar... I know a lot of people asked about this, and alot of people had answers, well, I tried what they did, but it just doesn't work..
Here's a screenshot:
[[IMG]http://img391.imageshack.us/img391/2536/screenshotek5.th.png[/IMG]](http://img391.imageshack.us/my.php?image=screenshotek5.png)
Hope someone could help me out with this...

Go to System / Administration / Synaptic packet manager and search for "libdecoration". You will find 2 entries, libdecoration and libdecoration-dev. Mark them both and click apply. It will update to version 0.5 if you don't have it already.

---

### Post by demitrix on 2007-06-26
Well if u are using a Nvidia card make this commando on shell :

sudo nvidia-xconfig --add-argb-glx-visuals -d 24


restart and should work :D

---

### Post by Dagur on 2007-06-29
thanks demitrix, this works for compiz as well :KS:KS:KS:KS:KS

---


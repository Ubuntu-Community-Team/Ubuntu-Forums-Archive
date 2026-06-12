---
title: "Access different wireless networks?"
date: 2005-04-09
forum: Desktop Environments
---

### Post by jakroo99 on 2005-04-09
I know that ubuntu users have a few proggies they use integrated with gnome to switch wireless networks, but what do u guys reccomend us kubuntu users to do?  All i have installed is kwifimanager, and its ok but i dont think it can scan different wireless access points.  Can anyone reccomend a kde tool or a program that us kubuntu users can use to scan diff wireless networks?

---

### Post by sjalex on 2005-04-09
I don't have a "good" answer for you, but I have a workable one. What I have done to get my rig working is get monitor mode working on my card then use kismet. This depends on your card and drivers, and you may already have monitor mode available in your drivers. The default drivers for orinoco (prism cards) though, for instance, have to be patched and recompiled. That's not too hard but it's kind of mind numbingly slow unless you're really doing it manually. If you know how to compile individual modules it's not bad. In any case to do this you'll need the kernel sources off the ubuntu repository and kismet from the universe repository and whatever patches might be needed for your card. check out kismetwireless.net for more info., [https://www.ubuntulinux.org/wiki/OrinocoMonitorKimset2005Hoary](https://www.ubuntulinux.org/wiki/OrinocoMonitorKimset2005Hoary) for more info about monitor mode patching/compiling.

---

### Post by jakroo99 on 2005-04-09
Thanx man I'll try kismet out, BTW i have a linksys wpc11 ver.3 which i think is a prism based chipset card.  So i have to recompile kernel modules eh?

---

### Post by sjalex on 2005-04-09
yeah, the other option is to use the hostap modules which I actually recommend over the patched standard kernel tree modules. The orinoco_cs drivers (for me and some others, maybe not for all) throw a lot of dropped packet errors which I never saw with the hostap drivers. And the hostap drivers build much quicker! You'll still need to download the kernel source tree (oh yeah and gcc etc) though.

---

### Post by sjalex on 2005-04-09
I should mention that I have only ever used the hostap drivers with slackware and not Kubuntu or any other debian type distro.

---


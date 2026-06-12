---
title: "Lubuntu missing features after installing update and then removing openbox"
date: 2015-12-15
forum: Desktop Environments
---

### Post by ross11 on 2015-12-15
Hello forums user,

I'll try and give as much information as possible to my problem.

After trying ubuntu 14.4 on a Samsung N145 Plus the OS is great but for a netbook not the best, so looking for something slimed down drum roll for lubuntu. burned to DVD and set-up really painless no faults then starting up for first time with the new Lubuntu on the netbook worked like a treat then looked for updates clicked yes and let it do it's thing no harm done I THOUGHT after updates and reboot I saw on the login screen top righthand corner that from my previous OS I still had lubuntu netbook & openbox installed as other OS installed along side ubuntu 14.4 so went about looking for a way to get rid of iether of them through lubuntu.

Found the command that I needed to get shot of openbox, and this is where things start getting odd so longed out of my lubuntu account only lubuntu netbook was there now along with the default OS lubuntu loged back in open up firefox and now I have no close, no minimize no maximize buttons (I can move the firefox window around) the only way I can close is through the tab button. 

Oh must just be firefox I thought open up documents folder and it's the same story no close nor minimize nor maximize. Then using the volume key for this netbook it's the arrow buttons + fn nothing happened, and then on top of all this the right button on the track pad stops working, flash still works date of installing lubuntu 15th December 2015 
I'm at abit of a loss here anyone could help would be smashing.

---

### Post by deadflowr on 2015-12-15
Moved to Desktop Environments.

---

### Post by furtom on 2015-12-15
hmmm. several things here. first of all, what commands did you run? exactly.

I'm not completely sure from your post if you had another linux enviornment previously installed or installed along side your current one.

In any case, it seems you removed packages from your 14.04 enviornment. we really need to know what that was. please post the commands the same way you ran them

---

### Post by mcduck on 2015-12-15
Well, Lubuntu's desktop is LXDE, and LXDE uses Openbox as it's window manager, so uninstalling it would definitely break your desktop... Reinstall the [lubuntu-desktop]("apt:lubuntu-desktop") package and that should get things back...

Also you are talking about having "ubuntu netbook & openbox installed as other OS installed along side ubuntu 14.4", while the rest sounds more like you uninstalled Openbox from the 14.04 you are actually running at the moment? You won't see any other OS installed on your system in the *login screen*, those would be other *desktop* options available. (and yes, in a system with LXDE, you are expected to also have a pure Openbox login option, since Openbox is installed as part of LXDE).

---


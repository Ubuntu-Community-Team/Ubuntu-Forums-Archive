---
title: "I installed kde and got rid of it and got leftovers"
date: 2010-05-21
forum: Desktop Environments
---

### Post by oleink on 2010-05-21
hey I'm pretty new to desktop environments and I installed kde to see what it was like (didn't like it went back to using gnome) but all the kde packages were kept. For instance

-My mouse pointer is still the kde look
-I've got kde stuff in my applications folder.

How can I get rid of these and if I have to uninstall each manually thats ok but how do I get my regular mouse back??

---

### Post by SlidingHorn on 2010-05-21
First, a disclaimer:

***_Please do not do this until someone more experienced comes along to verify or deny what I'm about to tell you._***

I believe that in order to remove configuration files for KDE you would have to purge instead of the usual 'remove'.  However, @ this point, since you've already uninstalled KDE, purging would simply say it's no longer installed.  So:

1.  Re-install KDE
```
sudo apt-get install kde-desktop
```

2. Purge it
```
sudo apt-get remove --purge kde-desktop
```

The reason I ask you not do this until someone else verifies what I'm saying is I'm not sure 'purge' won't remove any vital configuration files needed by gnome

---

### Post by oldfred on 2010-05-21
I did the same thing with 9.04 and never got rid of everything, primarily because I liked several KDE apps like K3b, kmymoney & a few others. Each of those install various dependencies  and would also be uninstalled if I removed all of KDE.

You can uninstall as above but if concerned you can reinstall the entire standard desktop with
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by Joe of loath on 2010-05-21
The cursor is a bug, I had that problem a while back and found a way to fix it. JFGI ;)

To be safe I'd remove the applications manually, one at a time. When I tried to remove KDE as a whole on fedora 12 it broke my installation.

---

### Post by wojox on 2010-05-21
I've always used psychocats link for that [Getting Back to a Pure Gnome on Ubuntu]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by oleink on 2010-05-21
> **wojox said:**
> I've always used psychocats link for that [Getting Back to a Pure Gnome on Ubuntu]("http://www.psychocats.net/ubuntu/puregnome")
trying this and if it doesn't work trying this: (ill post my results after
[QUOTE]
I believe that in order to remove configuration files for KDE you would have to purge instead of the usual 'remove'. However, @ this point, since you've already uninstalled KDE, purging would simply say it's no longer installed. So:

1. Re-install KDE
Code:
sudo apt-get install kde-desktop
2. Purge it
Code:
sudo apt-get remove --purge kde-desktop
The reason I ask you not do this until someone else verifies what I'm saying is I'm not sure 'purge' won't remove any vital configuration files needed by gnome[Quote]

---

### Post by oleink on 2010-05-21
First one didn't work:(

---

### Post by oleink on 2010-05-21
and the 2nd.  My boot screen says kubuntu now instead of ubuntu too..

---

### Post by oleink on 2010-05-21
Nevermind after a quick restart I found it worked.  Thanks a million to you all for you help I no longer have a kubuntu start up ubuntu login and a mixed array of loading symbols and window grabbing symbols.  Just back to good old clean Gnome.  Ok I know everyone argues over Gnome vs KDE but idk if i could ever work in kde its kind of ugly, boring, and hard to move around in

---


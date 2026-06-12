---
title: "Wireless works in Ubuntu but not Kubuntu?"
date: 2007-07-17
forum: Desktop Environments
---

### Post by aysiu on 2007-07-17
Has anyone else had this happen to them?

I've been running IceWM with Network Manager on my laptop for almost half a year. Worked fine.

Then, a couple of weeks ago, I added Gnome (*ubuntu-desktop*, specifically). Still working.

Then, just yesterday, I added KDE (*kubuntu-desktop*). In Gnome, the Network Manager works fine with my wireless connection. In the KDE network manager (forget what it's called), the wireless connection doesn't work (tries to join the network, then peters out).

Now, here's the weird part. If I Alt-F2 ```
nm-applet --sm-disable
``` in KDE, I still can't join. That's the Network Manager--the same one I use in Gnome.

But if I log out and go back to Gnome, the Network Manager does work.

Does anyone have a possible explanation for this? And am I the only one who's experienced something like this?

---

### Post by Gary.M on 2007-07-24
Well I have had my troubles with Knetworkmanager and my wireless network. The brief play I had with Ubuntu desktop instead of the Kde one and the network manager there was easy to use in comparison. Any tutorials on the Kde one anywhere?

---

### Post by aysiu on 2007-07-24
I don't know about any tutorials on KNetworkManager, but in my case i had even tried the regular Gnome one *inside of* KDE.

---

### Post by Gary.M on 2007-07-24
I read the forums and found a thread on wicd. I took the plunge, installed it. Saw that it removed knetworkmanager which worried me. Opened it, saw it could see all available networks. Chose my home network, told it to autoconnect, entered Wep key. Done. Restarted and it autoconnects with no keyring password request. Looks to support wired as well as wireless interfaces found on the machine. Yeehaa!

---

### Post by Gary.M on 2007-07-27
This is where I got Wicd

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---


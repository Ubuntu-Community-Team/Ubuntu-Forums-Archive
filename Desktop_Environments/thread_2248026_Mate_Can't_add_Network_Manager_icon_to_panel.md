---
title: "Mate: Can't add Network Manager icon to panel"
date: 2014-10-11
forum: Desktop Environments
---

### Post by PopsTheSailor on 2014-10-11
Using Ubuntu 14.04 with Mate 1.8.0. I can't figure out how to add Network Manager to the panel. 

My wifi works but if I'm at a new location where I need to connect to a new network, I have to select Unity at login, connect to the network and then boot back into Mate. I stay connected in Mate and everything works fine but this is a real pain.

Network Manager isn't listed in the options when I try adding applets to the panel

If it go to a terminal and type nm-applet it starts up and then shows up in the panel (and works)

If I go to /usr/shared/app-installed/desktop and double click on Network it shows up in the panel (and works). What's odd is that there are 2 files named network in this folder but as long as I double click on the right one, network manager starts and runs fine.

I've edited /etc/NetworkManager/NetworkManager.conf and changed **managed=false** to read **managed=true **(saw this in a post) 

I've uninstalled and reinstalled network-manager-gnome with not change

Anyone have any ideas on how to fix it?

---

### Post by mcduck on 2014-10-12
It's not a panel applet, which is why you can't add it there that way. And since you even mentioned yourself, simply starting the program makes it appear in your notification area, everything is working fine. All you need to do is add network manager to your startup applications so it gets started every time you log in.

---

### Post by PopsTheSailor on 2014-10-12
Well, I tried that and it didn't work. I added it to my startup applications then logged out and back in. No change so I rebooted. Still nothing. I then deleted it from my startup applications and rebooted. Even though I removed it from my list of start up apps, when I rebooted it, it was readded. Another strange thing is that when I first boot and come to the login screen, before I ever log in, NM appears in the panel. As I said before, if I log in with Unity it stays there. If I log in with Mate, it disappears even though it is included in my startup apps.

This is a strange one.....

---

### Post by tgalati4 on 2014-10-12
There are a lot of network tools.  What is on your system? Open a terminal.

```
apropos network
```

Examine what network manager thinks your connections are:

```
nm-tool
```

managed=false means to ignore entires in /etc/network/interfaces--which can screw up NetworkManager--so don't touch /etc/network/interfaces unless you know what you are doing or you can't get the correct configuration using the NetworkManager GUI.  I have noticed that the nm-applet will disappear in MATE 1.4 if there is a conflict between what is specificed in /etc/network/interfaces and what you have set up in the NetworkManager GUI.  It fixes itself magically if you go back to the stock /etc/network/interfaces and set managed=false in the NetworkManager.conf.

You want /etc/network/interfaces to look like:

> tgalati4@Mint14-Extensa ~ $ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


---

### Post by PopsTheSailor on 2014-10-12
I upgraded to Mate 1.8.1 and that fixed it so I'm marking this as solved.

---


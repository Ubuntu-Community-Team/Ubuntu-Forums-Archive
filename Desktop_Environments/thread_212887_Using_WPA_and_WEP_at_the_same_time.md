---
title: "Using WPA and WEP at the same time"
date: 2006-07-10
forum: Desktop Environments
---

### Post by simao on 2006-07-10
Hi,

I'm using a Asus WL500g router, and because I have one older computer, WEP has to be enabled, so that computer can connect to my network, but I'm using WPA for the other computers, because this router supports it.

The problem is that, Ubuntu doesn't seem to handle well networks with both WPA and WEP enabled.

It works fine with WPA only or WEP only.

I'm using Dapper Drake, does anyone have a solution for this?

Thanks,

Simao

---

### Post by NeoChaosX on 2006-07-10
How are you connecting to the wireless networks? Is it through the GNOME networking tools, or through something like Network Manager?

---

### Post by simao on 2006-07-10
I used this [https://wiki.ubuntu.com/WifiDocs/WPAHowTo?action=show&redirect=WPAHowto](https://wiki.ubuntu.com/WifiDocs/WPAHowTo?action=show&redirect=WPAHowto) 

To setup a WPA connection, and I'm using gnome networking manager to connect to my network.

---

### Post by NeoChaosX on 2006-07-10
First, in that document you linked to, it says
> These instructions are targeted toward Ubuntu 5.10 (breezy).

In Dapper, wpasupplicant has been changed radically since then, so those instructions really don't work with Dapper.

The best way you can have both WPA and WEP is just to install NetworkManager, which you can do by installing the network-manager-gnome package, and running "nm-applet".

---

### Post by simao on 2006-07-11
Yeah, it worked. Now I can connect to my network, with WEP or WPA.

Thanks

---


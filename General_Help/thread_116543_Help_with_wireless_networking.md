---
title: "Help with wireless networking"
date: 2006-01-12
forum: General Help
---

### Post by PersonMan92 on 2006-01-12
I'm having trouble connecting to the network in my house. I'm using a Linksys WMP54G card, but I can't figure out how to configure it using network-admin, and I've checked the Wiki multiple times. If someone could help me configure the wireless card, that'd be great.

---

### Post by TheIdiotThatIsMe on 2006-01-12
Just a few questions:

When connecting to the network, do you mean to access the internet or access files on another computer?

If it's to access internet:

Is your wireless card detected? If it is an unsupported card you can use ndiswrapper (which is what I use for my netgear) which is a program that uses a windows driver to use the card.

What result do you get from iwconfig? Do you have anything similar to wlan0?

---

### Post by PersonMan92 on 2006-01-13
[QUOTE=TheIdiotThatIsMe]When connecting to the network, do you mean to access the internet or access files on another computer?[/QUOTE]

Access to the internet.

[QUOTE=TheIdiotThatIsMe]Is your wireless card detected? If it is an unsupported card you can use ndiswrapper (which is what I use for my netgear) which is a program that uses a windows driver to use the card.[/QUOTE]

It's not detected in Device Manager, but I'm a Linux newbie, so I'm not sure if that was the right place to look. If you meant whether it was detected by the computer at all, it detected it in the network-admin tool as ra0.

[QUOTE=TheIdiotThatIsMe]What result do you get from iwconfig? Do you have anything similar to wlan0?[/QUOTE]

It lists lo, eth0, ra0, and sit0, but no wlan0.

---


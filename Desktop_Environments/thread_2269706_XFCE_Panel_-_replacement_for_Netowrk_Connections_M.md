---
title: "XFCE Panel - replacement for Netowrk Connections Manager wanted"
date: 2015-03-17
forum: Desktop Environments
---

### Post by kazakore on 2015-03-17
Hi all.

I have recently reinstalled Ubuntu Studio 14.04 (I wont go into the why and how right here and now) and have again come across how atrociously bad the Indicator plugin in the Panel is! I have replaced the Sound widget with the Audio Mixer but this still leaves me as needing a widget to replace the Network Connection part before I can fully remove it (and have the symbols which I don't want and which wont Hide gone from my screen!)

I have an inkling that previously I may have used one designed for Gnome (there doesn't seem to be anything pre-installed,) I also know at a later point I had to install KDE's network manager as it was the only way to set my laptop up as a true access point so my phone could share its connection (ad hoc doesn't work with many mobiles and the XFCE and Gnome mangers only offer ad hoc.) Something of this broke with a later update so that I was no longer prompted to enter passwords for wifi connections (it wouldn't probably scan the connection to work out the type of encryption until I opened it with the KDE network manger and entered the password in there. A bit of a pain but at least I eventually found the workaround...)


Anyway I really am going off on unneeded information now! Suggestions for network connection widget much appreciated! ;)

---

### Post by kerry_s on 2015-03-17
connman-ui ?

have you tried the standard ubuntu ?

---

### Post by kazakore on 2015-03-18
I tried various versions, Gnome, LXDE, XFCE and possibly some others (not KDE as at the time had an older computer) and found XFCE by far suited my workflow the best at the time (probably about three years ago, actually more likely 5 going on the date I joined this forum) and have stuck with it since, no matter the minor quibbles. Although I have been tempted to give Openbox on Arch a try but feel I need to be settled somewhere (currently travelling) to take on something like that. Note I used Ubuntu Studio, not Xubuntu, as I do some audio production and video work at times so need the pre-empt kernel and things which are not on the standard distribution.

But this issue is solved. Not sure exactly why it didn't appear when I first just removed the Indicator...

What I did:
Removed Indicator from Panel and unchecked related items in Settings > Startup.
Added Startup item: nm-applet
On restart there were two icons in the taskbar.
Found there was already an nm-applet item in startup and so removed the one I had added.

As I say, not sure why the network widget didn't seem to appear when just removing Indicator from panel originally but seems that should be enough. But then again a few things about it don't seem to quite make sense (eg as the item was already in the startup I would have expected to see it standalone, plus the one for Indicator. Plus the Notification Area widget also has Network Connections set so it should display but it doesnt, only the power/battery status does....)

---


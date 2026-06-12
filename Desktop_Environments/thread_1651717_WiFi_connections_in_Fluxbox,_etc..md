---
title: "WiFi connections in Fluxbox, etc."
date: 2010-12-23
forum: Desktop Environments
---

### Post by plumper on 2010-12-23
**[FONT=Arial Black][SIZE=3]Question[/SIZE][/FONT]**

I was curious about other window managers, but the main thing holding me back from exploring them is connecting to Wi-Fi in these environments.    So, how would one go about connecting to wireless in a lightweight window manager?

**************************************
[FONT=Arial Black]**[SIZE=3]Additional Information[/SIZE]**[/FONT]

I am scoping out the possibilities on my **iMac5,1** with a 2.33 GHz "Core 2 Duo" (T7600) processor and an ATI 256Mb Mobility Radeon x1600 with 3Gb of RAM so that I get a feel for what I can install and use on my PII **Dell Latitude CS** which will use a CardBus Wi-Fi card.    I will include its specs just for the purpose of giving you more information:  I have a Zonet ZEW1505 802.11g CardBus Adapter.

---

### Post by 3Miro on 2010-12-23
Ubuntu uses the program called NetworkManager to do network managing. Under Gnome (Ubuntu), XFCE (Xubuntu) and LXDE (Lubuntu), one would use nm-applet (network manager applet) to get the icon with the network options. If you have a panel and "notification area" you should be able to run nm-applet even on other environments. If not, you can take a look at the nmcli tool:

[http://askubuntu.com/questions/1820/can-i-use-networkmanager-without-a-tray-dock-bar](http://askubuntu.com/questions/1820/can-i-use-networkmanager-without-a-tray-dock-bar)

---

### Post by hhh on 2010-12-23
Just fire up network manager or wicd and get to it.

-edit- dang, didn't mean to step on you, 3Miro.

---

### Post by plumper on 2010-12-23
I will try it soon.  Thanks for the help, both of you!:D
I will get back to you on how it works in a sec.

---

### Post by plumper on 2010-12-23
Thank you so much!  Works great!  

Now I just need to remember how to set it to start when I log in!  I used to know fluxbox pretty well - I even had a custom splash that used to say AndrewBox!  I'll just re-RTFM first, then I'll ask in a different thread if I still need help.

---

### Post by katjapurrs on 2011-09-23
Thank You! Thank You! Thank You!

---

### Post by boydrice on 2011-09-24
> **plumper said:**
> Thank you so much!  Works great!  

Now I just need to remember how to set it to start when I log in!  I used to know fluxbox pretty well - I even had a custom splash that used to say AndrewBox!  I'll just re-RTFM first, then I'll ask in a different thread if I still need help.

In your fluxbox startup file just put wicd-client &

---


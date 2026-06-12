---
title: "wifi manager?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by DarkManX4lf on 2006-05-08
is there a wifi manager in ubuntu like there is in windows, like where you can store wifi profiles so that you dont have to keep entering the wifi ssid each time you move to a different area....is there something like this for ubuntu?


edit:

so i did a search and i came up with Network-Manager...i went to synaptic and installed this package but i cant run it, when i go into terminal and type:

sudo NetworkManager 

nothing happens....

---

### Post by FryerFox on 2006-05-09
From [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager):

Go to System -> Preferences -> Sessions In the Startup Programs tab, click Add type "nm-applet", click OK. log out of your gnome session, and log back in again.

You also have to comment out the line that 'auto's the network interface in /etc/network/interfaces. Check out the wiki for more info.

You could also try out gtkwifi, which I used for a while and was quite satisfied with:

[http://gtkwifi.sourceforge.net/](http://gtkwifi.sourceforge.net/)
[http://sourceforge.net/projects/gtkwifi](http://sourceforge.net/projects/gtkwifi)

---

### Post by DarkManX4lf on 2006-05-09
thanks! itworked !

---


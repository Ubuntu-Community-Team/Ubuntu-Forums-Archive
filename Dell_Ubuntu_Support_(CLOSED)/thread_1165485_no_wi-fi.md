---
title: "no wi-fi"
date: 2009-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by therumblebox on 2009-05-20
after attempting to install some updates with no success, my wi-fi totally stopped working. i cant find where to make it work again. i can turn the bluetooth/wifi on and off manually but it still doesnt work. any ideas?

---

### Post by Alexis Phoenix on 2009-05-20
We can better help you if you supply some more information.  What model of computer (I presume laptop) are you using, what wireless card does it have?  What did you attempt to upgrade?  What was the result that led you to believe this was unsuccessful?  What is the output of ```
iwconfig
```? Do you get any errors running (as root)? ```
modprobe module_for_your_card
```  Is the network you are trying to connect to listed when you try to use (as root)? ```
iwlist scanning
```  If it is, try to connect manually (as root) using the following, where you will have to substitute eth1 with the name of your wireless interface, address with the address you got from iwlist scanning, and netname with the essid of your network, and password with your password: ```
iwconfig eth1 essid "netname" ap address key password
``` (this method will not work with a passphrase, however.  If you need to use a passphrase, you will need to use wpa_supplicant).

You should also be checking your log files (in /var/log/) for error messages when you try to connect - this is likely to give you some useful information.

Good luck!

---

### Post by tyroeternal on 2009-05-21
What type computer/laptop are you using, and which version of Ubuntu is it running?

---


---
title: "Wireless networking problem!"
date: 2006-06-04
forum: Desktop Environments
---

### Post by zshall on 2006-06-04
All day I have been trying to get my Netgear WG311V2 card to work with Ubuntu. I have been using NDisWrapper, and have followed this tutorial: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29)
.
*To avoid getting information I already know, this is what I have already done.*
I removed the acx driver, which had been causing problems for me for a while I think.
After removing the acx driver, I installed the NDisWrapper source, and the C++ and G++ compilers and everything else they said to install.
I then configured NDisWrapper and installed my driver. Modprobed it, and got it to start on boot.
Rebooted, and went to network administration, expecting to find wlan0, activate it, and then get on with it
.
*This is where the problem started.*
There was NO WLAN0 device anymore on the network configuration. It was gone off the face of the earth. Just vanished.
That was disturbing, so I went into the device manager.
I saw my network card listed, BUT there was no piece of paper representing acx under it. I thought 'well its fine, because I removed the acx driver. I'll just add another wlan0 to my system.'
.
I have no clue how to get my wlan0 back. Once i get it though, I can configure it using **sudo ndiswrapper -d wg311v2 wlan0** or something, and the paper icon will display below it. But I have no idea how to get wlan0 back, or to add a wlan1 if 0 is out of the picture
.
*I just reinstalled Ubuntu again, and don't know what to do next. Does anyone know how to get my wireless going without the acx built in driver and using NDisWrapper and wg311v2.inf? It is driving me CRAZY! ](*,) ](*,) ](*,) *

---

### Post by metalheart on 2006-06-04
First install GTK Ndiswrapper tools

```
sudo apt-get install ndisgtk
```

Then run it

```
sudo ndisgtk
```

and load your card drivers and configure the interface.

---

### Post by zshall on 2006-06-04
I've tried that, and it doesn't work.
I now have associated the driver with the device, but the nick is still acx.
Basically all I need to do now is get online, as everything looks ok under iwconfig EXCEPT that I am not associated with an accesspoint.

Oh, and could one of the nice moderators here kindly move this thread to the networking support forum? I didn't know there was one until just now.

---


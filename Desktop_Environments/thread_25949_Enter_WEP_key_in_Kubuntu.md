---
title: "Enter WEP key in Kubuntu?"
date: 2005-04-11
forum: Desktop Environments
---

### Post by weeguy on 2005-04-11
It seems that the Wifi apps that come with Kubuntu doesn't allow one to enter WEP key for wireless networks via the GUI. So at the moment I'm entering it using command line. Is there any app that allows Kubuntu users to enter WEP in an easier manner? Tried installing Netapplet but I don't think it works in Kubuntu or am I wrong to say that?

---

### Post by philipacamaniac on 2005-04-11
In the KDE menu, go to Internet-->KWiFiManager (Wireless LAN Manager). In the KWifiManager, go to Settings-->Configuration Editor

You'll enter your password, and then you see the WiFi configuration module. This can also be found in the Control Center. For WEP, check the "Use Encryption" box, and then "Configure" it.

Linux+Wireless is pretty buggy still, especially when using WEP encryption, so good luck. I did have it working, using the GUI configuration, on a KDE 3.3/Linux 2.4 box. I know it should work (probably better) in Kubuntu, since it is KDE 3.4/Linux 2.6 box.

---

### Post by adder1972 on 2005-04-13
Hi,

My KWiFiManager isn't able to set the WEP-key for me.

Instead I manually changed "/etc/network/interfaces" by adding " wireless_key2 12345678 ". I use a 128-bit key in my network (26 characters - replace 12345678) idetified as Key 2 by my router.

Read more in "/usr/share/doc/wireless-tools/readme.debian"

Kind regards,

S

---

### Post by BassTek on 2005-04-13
[QUOTE=adder1972]Hi,

My KWiFiManager isn't able to set the WEP-key for me.

Instead I manually changed "/etc/network/interfaces" by adding " wireless_key2 12345678 ". I use a 128-bit key in my network (26 characters - replace 12345678) idetified as Key 2 by my router.

Read more in "/usr/share/doc/wireless-tools/readme.debian"

Kind regards,

S[/QUOTE]

Thanks for the help, I was having problems getting my WEP/Wireless working and editing this file did the trick.  Manually added ESSID, WEP Keys and WEP mode and all is good.

---

### Post by usererror on 2005-04-14
[QUOTE=adder1972]Hi,

My KWiFiManager isn't able to set the WEP-key for me.

Instead I manually changed "/etc/network/interfaces" by adding " wireless_key2 12345678 ". I use a 128-bit key in my network (26 characters - replace 12345678) idetified as Key 2 by my router.

Read more in "/usr/share/doc/wireless-tools/readme.debian"

Kind regards,

S[/QUOTE]

could you post a copy if your interfaces file?

i roam, A LOT, with wireless and I need to have this thing just pick up at least the places i roam to all the time.

i have wirelss at home, no wep, at work i have WEP 128bit and friends place no wep...

I got it to work at home, somehow, but i cant get it on at work today, and i'm afraid if i go home it wont work there anymore.   :???:

---

### Post by epb613 on 2005-04-14
For me, I go into System->Networking then select my wi-fi connection and click properties. This allows me to enter my SSID and WEP key. It occurs to me that this may be a GNOME app (I have both installed), but if it is you could try downloading the package.

Hope this helps.

---

### Post by usererror on 2005-04-14
[QUOTE=epb613]For me, I go into System->Networking then select my wi-fi connection and click properties. This allows me to enter my SSID and WEP key. It occurs to me that this may be a GNOME app (I have both installed), but if it is you could try downloading the package.

Hope this helps.[/QUOTE]

now this is getting interesting!  that is exactly how I got wifi to work last night, in my home, with my AP.  tonight, after all my troubles of getting on my wifi AP at work, I tried again tonight at home.  

I am successfully able to connect to both my non-WEP enabled AP **and** my neighbors non-WEP enabled linksys router by just selecting the SSID's from the Gnome Applet's pulldown menu.

now here comes the confusion... i can't get on an AP at work.  We have 4 different wifi signals available in our office.  Our own with WEP, my neighbor with WEP, and two very, very faint non-WEP enabled AP's...

i could not ocnnect to any of them.  Just when the Gnone Wifi Applet was about to connect to my work's AP (after I turned off WEP) the whole Gnome Desktop would freeze, leaving me no option but to power down. 

so what's the difference between my home and my workplace?? :confused:  are the multiple signals causing the interference??  ](*,)

**update**

I think this problem is with this make and model of linksys routers (BEFW11S4 Ver. 4, Firmware 1.54.x) and linux

i have done a firmware update, and still no luck connecting.  I plugged in a Belkin G router, and was able to connect with that and get an IP without a problem.  thinking of ditching the linksys router now for the belkin at work.  :-|  even restored the factory defaults to the router.  no luck.  switching to Belkin.

---


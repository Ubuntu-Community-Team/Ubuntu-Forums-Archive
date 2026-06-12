---
title: "Kubuntu wireless"
date: 2009-01-19
forum: Desktop Environments
---

### Post by monkeybus on 2009-01-19
I have an old Gateway 200ARC ([specs]("http://support.gateway.com/s/Mobile/Gateway/200ARC/3501609sp83.shtml")) and i just installed kubuntu 8.10 on it. I am trying to configure it so that my internal wireless card will connect to the internet, but i am not sure what to do. any help will be greatly appreciated. thanks :)

---

### Post by sleepitoff on 2009-01-19
Do you have the wireless driver installed? If not, make sure you to goto System -> Hardware Drivers and pick the wireless driver to install. 

After that, on the bottom right, you'll see a gray globe looking icon, right click on it and pick your wireless network, or pick the configuration setting to add it if your router isn't broadcasting an SSID.

---

### Post by monkeybus on 2009-01-19
no i don't have it installed. i am not quite sure how to install it or where to get it from. there was nothing i could do in system->hardware drivers to install it

---

### Post by abn91c on 2009-01-19
press alt+f2, type **[COLOR="Blue"]knetworkmanager[/COLOR]** then at bottom right toolbar right click on the globe, select new connection> [COLOR="blue"]wlan0[/COLOR], next screen input you SSID security keys>next at the SSID screen check the connect at startup box, then select connect and save.

---


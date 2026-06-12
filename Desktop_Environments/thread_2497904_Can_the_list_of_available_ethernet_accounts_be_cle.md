---
title: "Can the list of available ethernet accounts be cleaned up?"
date: 2024-05-22
forum: Desktop Environments
---

### Post by ascendant2 on 2024-05-22
I'm running Ubuntu 20 Mate in an HP notebook.
We have a few  troubled neighbors who use their internet account titles to bully and gross-out the honorable meek elderly people living on this street.  When we click the ethernet connect icon we see their vile messages every day in their distasteful wifi network names.
Is there a way to edit that nauseating list, to erase the disgusting account titles we see whenever we click the connect/disconnect ethernet icon? 
Is there a way to configure that icon's tool bar to show only our own IP accounts listed?

---

### Post by grahammechanical on 2024-05-22
I am not familiar with the Mate desktop environment but I doubt very much that it offers a list of ethernet accounts. Perhaps you mean WiFi. Ethernet is a direct cable connection between the computer and the router/hub/modem. There will only be the one ethernet connection listed in System Settings and you will only see it if the computer is connected by an ethernet cable to a router/hub/modem that is switched on.

I do not think we can remove WiFi connections that are in the list of WiFi available connections within range. You should be able to set up a default WiFi connection to your WiFi router/hub/modem. Then the router/hub/modem will automatically connect to the Internet Service Provider (ISP) when it is switched on and the computer will automatically connect to the router/hub/modem as soon as the computer is switched on.

What you are seeing in that WiFi list are the WiFi router/hubs/modems of those neighbours that are annoying you so much. 

Regards

---

### Post by MAFoElffen on 2024-05-25
<<I think this would be better handled if move to the Networking Section>>

I'm not sure, btu I think it might be possible through wpa_supplicant...

In [https://w1.fi/cgit/hostap/plain/wpa_supplicant/wpa_supplicant.conf](https://w1.fi/cgit/hostap/plain/wpa_supplicant/wpa_supplicant.conf) and [https://gist.github.com/penguinpowernz/ce4ed0e64ce0fa99a5e335c1a4c954b3](https://gist.github.com/penguinpowernz/ce4ed0e64ce0fa99a5e335c1a4c954b3).

wpa_supplicant.conf has a section for 
```

excluded_ssid: Excluded SSID
#    This optional field can be used to excluded specific SSID(s) from
#    matching with the network. Multiple entries can be used to specify more
#    than one SSID.

```
But I think that option only covers whether it will connect or not...

I think what you rather want is for it to be excluded from being filtered... Like in this section
```

# filter_ssids - SSID-based scan result filtering
# 0 = do not filter scan results (default)
# 1 = only include configured SSIDs in scan results/BSS table
#filter_ssids=0

```
If you set that to "1" then it would only filter confgured SSIS's.

This example Doc ([https://web.mit.edu/freebsd/head/contrib/wpa/wpa_supplicant/wpa_supplicant.conf](https://web.mit.edu/freebsd/head/contrib/wpa/wpa_supplicant/wpa_supplicant.conf)), near the bottom has examples of configured SSID connections...

I am not positive, but I think that would exclude SSIDs not configured from showing up in the list. I may be wrong about that, but... LOL

---

### Post by grahammechanical on 2024-05-25
It occurs to me that the reason your good neighbours have the the WiFi networks of your bad neighbours showing up is that at some point your good neighbours have tried to access those WiFi access points of your bad neighbours. Ubuntu remembers these access points and keeps the connection available.

In system settings>WiFi these WiFi networks will have a cog icon next to them. Click on the cog icon and then click forget connection. That should make things simpler.

Regards

---

### Post by currentshaft on 2024-05-26
dap

---

### Post by him610 on 2024-05-26
> Is there a way to edit that.... list, to erase the.... account titles we see whenever we click the connect/disconnect ethernet icon?
Yes, there is, by using a wired connection instead of a wireless connection. 
You probably don't want to be running Cat5 internet cable throughout your home, but there is a way to use your existing electrical wiring.

Here is a link to an article about Powerline adapters....[https://www.popularmechanics.com/technology/g35470087/top-powerline-adapters/?utm_source=google&utm_medium=cpc&utm_campaign=arb_ga_pop_b1_md_dsa_hybd_mix_us_21214990476&gad_source=1&gclid=Cj0KCQjwu8uyBhC6ARIsAKwBGpQtIBYdP5pef_WQ9Fi9glW2nhIokG73ggc2Oy9729HcTsrdMqQI5kcaAmkqEALw_wcB]("https://www.popularmechanics.com/technology/g35470087/top-powerline-adapters/?utm_source=google&utm_medium=cpc&utm_campaign=arb_ga_pop_b1_md_dsa_hybd_mix_us_21214990476&gad_source=1&gclid=Cj0KCQjwu8uyBhC6ARIsAKwBGpQtIBYdP5pef_WQ9Fi9glW2nhIokG73ggc2Oy9729HcTsrdMqQI5kcaAmkqEALw_wcB")

---


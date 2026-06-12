---
title: "WiFi issues..."
date: 2006-07-05
forum: Desktop Environments
---

### Post by analogdevices on 2006-07-05
Hey, I can say that I've been using ubuntu for a while and am comfortable with it. The only damned problem that seems to be recurring is the WiFi one. 

I bought a D-Link DWL-G630 because I was told that it worked out of the box with linux, which is nice. The only thing is, I don't know how to work the WiFi interfaces with Ubuntu. I have KWiFi manager, but run Gnome. Could anyone help me out on this, maybe explain how the WiFi tools in Gnome and Ubuntu work? It seems to know the card is there, but I don't know how to hook up with any networks. I've tried scanning with KWiFi, but that returns no results.

---

### Post by analogdevices on 2006-07-05
I forgot to say that right now, I am trying to connect to an unsecured network at a library. I have heard that there are two different chipsets for the card at hand. One being the atheros chipset which shows up as ath1 and the other acx111 that shows up as wlan0. I hear that the Atheros ones work better, and do supposedly what The D link cards should, but I have the acx111.

---

### Post by kpkeerthi on 2006-07-05
Open synaptic and install network-manager-gnome. Then open terminal and run nm-applet.

---

### Post by analogdevices on 2006-07-05
the nm-applet doesn't seem to work. I attempt to connect to 'kcls.org' (the library's network) and use 'no encryption' but it never seems to actually connect, The icon spins in the taskbar forever.

---


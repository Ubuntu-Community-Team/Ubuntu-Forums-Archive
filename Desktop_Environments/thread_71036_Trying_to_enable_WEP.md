---
title: "Trying to enable WEP"
date: 2005-10-02
forum: Desktop Environments
---

### Post by w.hill on 2005-10-02
Hi,

My first post...

I've made a clean 5.04 install onto a PC. The wireless network card is correctly detected.

With WEP disabled I can access my local LAN and the Internet without a problem. BUT if I enable WEP I can no longer connect. the DHCP process times out which according to some of the doco usually means that the KEY is wrong. (I can access the LAN from a Windows box using the same WEP KEY).

I'm using a 64bit KEY - Ten HEX digits. I configured the Wireless Card through the UI. The IP address is provided via DHCP.

Is there a trick to entering the WEP key?

TIA

[EDIT] The NIC is a Netgear WG311 [/EDIT]

---

### Post by cbudden on 2005-10-02
I had a problem with my hex key, so i didn't use it, but in breezy you can tell the ui that it is a hex key and works fine.

---

### Post by w.hill on 2005-10-02
Does that mean that you didn't use WEP? I noticed that there is no option to specify whether the key is ASCII or HEX.

---

### Post by Foaming Draught on 2005-10-02
Please forgive me if this is too basic; I need basic myself :) 
1  I connected an ethernet cable from my laptop to my Belkin wireless router and enabled eth0, the ethernet port.
2  I disabled wlan0, my Belkin F5D7010au card.
3  I surfed to the Belkin setup page on Epiphany (I assume that you configure your router via a web interface?), logged in and changed Security setting from Disabled to 128 bit WEP.
4  I used a passphrase to generate the 26 character (13 x 2) Hex key, and hit Apply.
5  I carefully wrote this key down, and logged out of the Belkin web UI.
6  I left-clicked on the network connection icon on the top right of my GNOME panel.
7  I left-clicked configure
8  In the resulting box, I highlighted wlan0, Properties.
9  I picked hex, and carefully entered all 26 hex characters in correct sequence.
10 I re-activated wlan0, de-activated eth0 and removed my cable.
11 I checked that Firestarter was scanning wlan0.
12 Hey presto, a WEP protected wireless LAN. Neighbours eat your heart out, get your own jolly broadband ;) 
13 I forgot to tell my wife that I'd done this. Good job I'd kept the WEP key :eek:

---

### Post by w.hill on 2005-10-06
I entered an ASCII WEP password proceeded by "s:' I can access the wireless network from a Windows PC on the same network.

/etc/network/interfaces has the password in it!!!

wireless-key s:mykeyishere

Curiously when I go into the properties of the wlan0 device through the GNOME interace the SSID dialogue box displays both the SSID of my WAP and that of my neighbours. The icon below the name has a padlock next to my neighbours but not mine. I assume that the icon means encryption. My WAP is encrypted and so is my neighbours.

---

### Post by Toddy on 2005-10-06
I remember a similar problem with my setup.  Eventually, I changed my router's authentication from "shared" to "open".  Magically, the machine connected using WEP after that.

---

### Post by w.hill on 2005-10-07
My DI-624 is already configured for "Open" :(

---


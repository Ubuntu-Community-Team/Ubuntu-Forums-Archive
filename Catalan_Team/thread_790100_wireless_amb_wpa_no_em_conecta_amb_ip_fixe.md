---
title: "wireless amb wpa: no em conecta amb ip fixe"
date: 2008-05-11
forum: Catalan Team
---

### Post by sianeu on 2008-05-11
Ho he provat en dos equips diferents i amb dos targetes usb diferents. Amb el mode itinerant, cap problema, però si faig la configuració manual amb ip fixe no hi ha manera. El fitxer interfaces diu:

> auto lo
iface lo inet loopback





iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk 326c5de.................
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid xxxx

auto eth1

M'estranya que la clau wpa surti en hexadecimal, per que l'escric com a frase. Ho he canviat i tampoc funciona.
El interfaces del mode itinerant consta nomès de les dues primeres línies(loopback).

Alguna idea?

PD: També cal dir que amb la protecció wep sí que puc posar-li ip fixe.

---


---
title: "nous problemes amb la wifi"
date: 2007-12-02
forum: Catalan Team
---

### Post by lluisanunez on 2007-12-02
hola,
estem intentant fer anar un adaptador wifi USB 'OvisLink Wireless G USB Dongle' en un PC d'escriptori. Tenia Debian, i com que no funcionava la wifi, hem insta&#320;lat Ubuntu 7.04. 
Ara el networkmanager veu la xarxa, entrem les dades de la connexió DHCP, i no es connecta. (En canvi amb el portàtil sí que connecto amb la mateixa xarxa)
Quan am el networkmnager m'intento conectar, sembla que es queda repetint la mateixa instrucció:
```
iwevent:

Waiting for Wireless Events from interfaces...
22:30:42.329770   wlan0    Set ESSID:"huggyfer"
22:30:47.342745   wlan0    Set ESSID:"huggyfer"
22:30:52.354069   wlan0    Set ESSID:"huggyfer"
22:30:57.361410   wlan0    Set ESSID:"huggyfer"
22:31:02.369520   wlan0    Set ESSID:"huggyfer"
22:31:07.373482   wlan0    Set ESSID:"huggyfer"

```

A part, adjunto el iwconfig, ifconfig i lspci:
```
iwconfig:

wlan0     IEEE 802.11g  ESSID:"huggyfer"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:XXX-XXX-XXX-X
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:08:A1:B3:C2:8E  
          inet6 addr: fe80::208:a1ff:feb3:c28e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:1836 (1.7 KiB)


lspci:
root@Feynman:/etc/network# lspci
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:06.0 Ethernet controller: MYSON Technology Inc SURECOM EP-320X-S 100/10M Ethernet PCI Adapter

```

---

### Post by papapep on 2007-12-02
És aquest dispositiu?: [http://www.qbik.ch/usb/devices/showdev.php?id=4239](http://www.qbik.ch/usb/devices/showdev.php?id=4239)

Fent un **lsusb**, quina id dóna?

Potser seria interessant que provessis amb el **wicd**. A mi el network manager em porta bastants problemes amb el wifi...

---

### Post by lluisanunez on 2007-12-02
Gràcies!
Ara enviaré el lsusb. És l'ordinador de ma filla, que s'ha traslladat de casa i allà on viu només pot tenir wireless. 
Ja havia pensat en el wicd, però, com l'hi insta&#320;lo sense xarxa?

Sí, es aquest dispositiu, que ja veig que té el chipset ralink de mala fama...

---

### Post by lluisanunez on 2007-12-02
lsusb diu això:
```
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 0000:0000 
Bus 004 Device 002: ID 148f:2573 Ralink Technology, Corp.
Bus 004 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by papapep on 2007-12-02
> Ja havia pensat en el wicd, però, com l'hi insta&#320;lo sense xarxa?


No tens possibilitat de connectar-te amb el teu portàtil i baixar-te els paquets? No té massa requeriments, la majoria de paquets ja els deu tenir instal·lats. Aquestes són les dependències i conflictes:

```
apt-cache show wicd
Package: wicd
Version: 1.3.1
Section: extras/web
Priority: optional
Architecture: all
Essential: no
Depends: python, python-gtk2, python-dbus | python2.4-dbus, wpasupplicant, python-glade2
Conflicts: network-manager, wifi-radar, gtkwifi
Replaces: connection-manager
Provides: wicd

```

---

### Post by lluisanunez on 2007-12-02
Cal algun repo especial per instalar wicd? No el trobem al synaptic

---

### Post by papapep on 2007-12-02
```
##Wicd
deb http://wicd.longren.org gutsy extras
```

---

### Post by lluisanunez on 2007-12-02
Gràcies, Papapep, però el WICD té el mateix problema: es queda intentant connectar, i pel terminal veiem:
set SSID  etc....

---

### Post by papapep on 2007-12-02
Doncs així apunta al controlador. Fas servir el rt63 que posava a la pàgina que he referenciat abans?

---

### Post by lluisanunez on 2007-12-02
Sí, exactament aquest :(

---

### Post by papapep on 2007-12-02
Jo de wifi no controlo gaire, però igual provant a compilar la última versió del controlador...(ja sé que no és un bon rotllo, però no tinc més respostes).

El que si que faria és assegurar-me de que no és problema de ferro i que el dispositiu funciona correctament a alguna altra màquina (ni que sigui amb un "altre" sistema operatiu), però amb el mateix router per eliminar també problemes de configuració o compatibilitat (que seria molt estrany) amb aquest.

---


---
title: "Problemes amb el wireless. UBUNTU 8.04 Desktop Edition 32 bits"
date: 2008-09-07
forum: Catalan Team
---

### Post by alfaalbert on 2008-09-07
Molt bones:

Tinc dos sistemes operatius en el portàtil ACER TravelMate 5720: WINDOWS VISTA (WV) AND UBUNTU 8.04 Desktop Edition 32 bits. Amb WV no tinc cap problema, però amb l’ubuntu sí: no reconeix cap connexió wireless. A Barcelona (ara estic a l’estranger per estudis) vaig fer servir només la connexió via cable amb el mòdem ADSL.

A més, no puc encendre el dispositiu Wireless a Ubuntu (el led sempre està apagat, però no passa el mateix per exemple amb el Bluetooth, que sí que funciona). La tarjeta wireless és: : Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02).

[COLOR="Blue"]A continuació us passo els següents reports del Terminal: lspci, sudo lshw -C network i iwconfig:

albert@albert-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02) 
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) 
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller albert@albert-laptop:~$


albert@albert-laptop:~$ sudo lshw -C network 
[sudo] password for albert:    
*-network                       
description: Ethernet interface        
product: NetLink BCM5787M Gigabit Ethernet PCI Express        vendor: Broadcom Corporation        
physical id: 0        
bus info: pci@0000:02:00.0        
logical name: eth0        
version: 02        
serial: 00:1d:72:32:90:be        
capacity: 1GB/s        
width: 64 bits        
clock: 33MHz        
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair   
*-network        

description: Wireless interface        
product: PRO/Wireless 3945ABG Network Connection        
vendor: Intel Corporation        
physical id: 0        
bus info: pci@0000:04:00.0        
logical name: wmaster0        
version: 02        
serial: 00:1f:3c:2f:61:04        
width: 32 bits        
clock: 33MHz        
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless        
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g 

albert@albert-laptop:~$ iwconfig 
lo     no wireless extensions. 
eth0     no wireless extensions. 
irda0     no wireless extensions. 
wmaster0  no wireless extensions. 
wlan0     IEEE 802.11g  ESSID:""  Nickname:""           
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated              
Tx-Power=27 dBm              
Retry min limit:7   RTS thr:off   Fragment thr=2346 B            
Power Management:off           
Link Quality:0  Signal level:0  Noise level:0           
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0         
Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
albert@albert-laptop:~$  [/COLOR]

---

### Post by alfaalbert on 2008-09-07
Ostres, les cares alegres :) de l'anterior thread són el char 'o'.

A més, he estat provant amb altres ordres:
- sudo iwconfig wlan0 essid any
- sudo dhclient wlan0
- sudo ifconfig wlan0 up

[COLOR="Blue"]albert@albert-laptop:~$ sudo iwconfig wlan0 essid any  
[sudo] password for albert:  

albert@albert-laptop:~$ sudo dhclient wlan0  
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:1f:3c:2f:61:04 
Sending on   LPF/wlan0/00:1f:3c:2f:61:04 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 
receive_packet failed on wlan0: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database – sleeping. 

albert@albert-laptop:~$ sudo ifconfig wlan0 up  
SIOCSIFFLAGS: Error de entrada/salida 
albert@albert-laptop:~$ [/COLOR]

---

### Post by papapep on 2008-09-07
Sembla que el controlador d'aquesta placa no és especialment gloriós, però [aquí]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226411") i [aquí]("http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579") diuen que es pot fer funcionar fent això:

- Descarregar el controlador (iwl, anteriorment era ipw) actualitzat del repositori de Backports.
- Crear el fitxer /etc/modprobe.d/iwl3945, i ficar-hi el següent dins:
    
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```

---

### Post by patrickfromspain on 2008-09-07
es curios, jo tinc exactament el mateix i funciona de maravella sense haver de fer res d'especial.

salut

---

### Post by alfaalbert on 2008-09-07
Hola Josep:

1. No sé molt bé com fer:
- Descarregar el controlador (iwl, anteriorment era ipw) actualitzat del repositori de Backports.


2. Del primer enllaç veig que hi ha un pas més:

- Installed wicd instead of network-manager.
Again only helped temporarily

És necessari? Com es faria?


3. És possible descarregar tot lo necessari des de windows (només tinc accés a connexió wireless) i després aplicar-ho a ubuntu?

---

### Post by papapep on 2008-09-07
> 1. No sé molt bé com fer:
- Descarregar el controlador (iwl, anteriorment era ipw) actualitzat del repositori de Backports.

Si tinguessis xarxa amb l'ubuntu ho faríem d'una manera. Com que més avall dius que no en tens, el descarregarem del lloc web de paquets d'ubuntu, però just ara no respon el servidor...bon punt estigui accessible et poso l'enllaç.

> 2. Del primer enllaç veig que hi ha un pas més:

- Installed wicd instead of network-manager.
Again only helped temporarily

És necessari? Com es faria?

És necessari si, com en el meu cas, el gestor de xarxa que ve de l'instal·lació d'Ubuntu (network-manager) no fa la feina com cal. En el teu cas, deixe'm-ho per més endavant, si cal.

> 
3. És possible descarregar tot lo necessari des de windows (només tinc accés a connexió wireless) i després aplicar-ho a ubuntu?

Sí, sempre que tinguis un directori compartit o un pendrive que sigui accessible pels dos sistemes per passar els fitxers.

---

### Post by alfaalbert on 2008-09-08
Hola de nou:

Gràcies papapep. Espero les teves instruccions per a realitzar els tres passos mencionats descarregant des de windows.

PD: Sí que tinc directori compartit...

---

### Post by Diegstroyer on 2008-09-09
Posa al google: **ndiswrapper wifi acer (+ el teu model de portàtil)**

El google és el nostre gran amic... No em de tenir por de preguntar-li...

---


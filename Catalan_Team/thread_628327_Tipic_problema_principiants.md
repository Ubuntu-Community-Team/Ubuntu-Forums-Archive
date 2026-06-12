---
title: "Tipic problema principiants"
date: 2007-12-01
forum: Catalan Team
---

### Post by pixu on 2007-12-01
Bon dia a tots,
En primer lloc avisar que no se res de linux, i que per a les vostres respostes no doneu res per sabut, jeje

Be, he insatalat la versio 7.1 i el meu problema es la conexio a internet. He mirat en un fum de llocs i al final no he conseguit res, per tant me decidit per registrarme i publicar un post. Al principi em detectaba la red inalambrica pero cuan li posava la contraseña no es conectaba i la tornava a demanar. Ara ja ni detecta la red i no se que fer.

Com soc novell necesite internet per poder fer cosetes ja que les tinc que buscar cada vegada.

Garcies

---

### Post by cortsenc on 2007-12-01
Val, anem a pams.

Et conectes amb WiFi. Hi ha algun altre equip que controlis que es conecti a la mateixa xarxa? El primer que hauries de saber és quin tipus de clau fa servir, ja que n'hi ha més d'un (WPA, WEP....) ja que un dels errors més comuns és no canviar la opció que et ve per defecte WPA Personal, quan el Router fa servir WEP, i t'ho dic per pròpia experiència.

Per altra banda, obre un terminal (**Aplicacions>Accesoris>Terminal**) i tecleja (**iwlist scan**) i s'haurien de llistar les xarxes disponibles. Si t'en surten, vol dir que la tarjeta funciona, ubuntu la reconeix i que a més hi ha xarxes disponibles. Mira si surt la teva i prova de conectar-ti desde (**Sistema>Administració>Xarxa**).

---

### Post by pixu on 2007-12-01
El tipues de contraseña es WEP. Al utilitzar iwlist scan no apareix cap llista de  reds i en wlan0 diu que es un recurs temporalment no disponible
en lo i eth0 Interface doesn't support scaning

---

### Post by jodufi on 2007-12-01
Prova de fer un **iwconfig** i ens envies el resultat.

Has provat de connectar-te mitjançant cable? Si pots prova-ho, així ens assegurem que l'únic problema és la connexió WiFi.

---

### Post by pixu on 2007-12-01
Depres de iwconfig apareix aço:

lo        no wireless extensions.


eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

No puc conecterme per cable.

---

### Post by eduardsola on 2007-12-01
A mi em passava just el mateix...

No me'n vaig sortir, i vaig optar per comprar-me una tarja de xarxa ethernet, que va més bé, així mai tens problemes.

---

### Post by pixu on 2007-12-02
Be, he estat llegint per ahi i el que he trobat son coses com que tinc que compilar el kernel i coses aixi, i aixo matemoritza.Per tant a la espera de respostes vostres no toque res relacionat amb la wici.

---

### Post by papapep on 2007-12-02
Pixu, si molt no m'equivoco, no has comentat quin dispositiu wifi tens. Saber això és bàsic per a poder intentar-te ajudar.

Si no ho saps, executa la comanda** lspci** i enganxa aquí el resultat.

---

### Post by pixu on 2007-12-02
Ops no mavia adonat. El dispositiu que utilize es el tipic adaptador usb de telefonica el WL382F wireless LAN 11Mbps Adapter.
I la tarjeta de red Broadcom NetLink BCM5789 Gigabit Ethernet Controller, per si de cas ajuda.

Tambe adjunte el resultat de la comanda lspci: 
pau@pau-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)

---


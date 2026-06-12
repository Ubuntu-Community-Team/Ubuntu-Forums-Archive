---
title: "Connexió a internet"
date: 2008-01-31
forum: Catalan Team
---

### Post by xavixa on 2008-01-31
Hola a tothom, sóc totalment nou en això de l'Ubuntu. 

La qüestió és que no aconsegueixo connectar-me a internet. He estat mirant per fòrums però l'únic que he aconseguit és embolicar-me més.

A veure, ara estic connectat des d'un pc amb windows. On tinc l'Ubuntu és al portàtil, i si m'hi acostumo bé doncs el posaré també aquí.

El que sé que he de fer és anar a sistema>red, allà he provat d'activar-la posant la contrasenya wep de la xarxa, però res.

He llegit en algun lloc que durant la instalació de l'Ubuntu ja et pregunta sobre la connexió a internet, però el problema és que me'l va instalar un tècnic. Hi ha alguna manera de que em detecti automàticament la xarxa?

La meva connexió és a ONO, per cable, un modem Thomson i el portàtil va amb wireless.

Moltes gràcies

---

### Post by papapep on 2008-02-01
Hola Xavixa, benvingut (assumeixo que ets un noi) al fòrum.

El primer que ens caldria saber és quin model de dispositiu wifi té el teu portàtil.
Per a saber-ho del cert, fes a un terminal:

```
lspci |grep Network
```

i enganxa'ns aquí el que et mostri.

---

### Post by CarlesOriol on 2008-02-02
Posa també el resultat de les comandes:

**iwconfig**
**ifconfig**
i 
**iwlist scanning**

---

### Post by xavixa on 2008-02-02
Ep. He fet el que m'heu dit:

**El que em surt a la primera ordre és:**

0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 208.11g Wireless LAN Controller (rev 02)

**I a les altres em surt:**

xavi@xavi-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"THOMSON"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


xavi@xavi-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F2:15:89
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)


xavi@xavi-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.



Moltes gràcies! :)

---

### Post by papapep on 2008-02-02
Si no recordo malament, pel xip BCM4318 cal utilitzar el controlador restringit que s'instal·la amb la eina que hi ha a "Sistema > Administració > Gestor de controladors restringits". Per a fer-ho crec que et farà falta tenir connexió a internet per cable, per poder baixar el que cal.

---

### Post by CarlesOriol on 2008-02-02
Totalment d'acord amb en patatet però per descarregar el firmware crec que cal que estiguis connectat  a internet per cable.

---

### Post by papapep on 2008-02-02
El dia que aprenguis a llegir Pol·liol....:-D

---

### Post by xavixa on 2008-02-03
D'acord. Miraré de fer això, doncs.

Moltes gràcies a tots dos!

---

### Post by CarlesOriol on 2008-02-03
Jo sols he copiat. ;-) Perdona papapep disculpa el teu humil servidor.

---

### Post by xavixa on 2008-02-03
Ja estic connectat des del cable. A sistema>administració no hi tinc cap pestanya que em digui gestor de controladors restringits..

El que he trobat i m'he descarregat és un paquet que en teoria activa el meu model de targeta de xarxa. L'he instalat però segueix sense funcionar quan desconnecto el cable, tot i que ara quan vaig a la configuració de la xarxa ja em diu que l'inalàmbrica està activa.

He tornat a fer aquelles ordres que em vau posar (connectat des del cable) i els resultats són aquests:

xavi@xavi-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F2:15:89
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef2:1589/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:200128 (195.4 KiB)  TX bytes:53584 (52.3 KiB)
          Interrupt:169 Base address:0x1800

eth1      Link encap:Ethernet  HWaddr 00:14:A4:52:5D:20
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

xavi@xavi-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"THOMSON"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

xavi@xavi-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.



Vaig per bon camí? hehe..

---

### Post by CarlesOriol on 2008-02-03
No. 

Has de tenir la opció de menú que t'hem dit. Si no es així deus haver insta&#320;lat una versió vella d'ubuntu.

---


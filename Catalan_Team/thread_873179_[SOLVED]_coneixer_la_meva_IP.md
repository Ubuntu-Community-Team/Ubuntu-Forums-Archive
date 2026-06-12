---
title: "[SOLVED] coneixer la meva IP"
date: 2008-07-28
forum: Catalan Team
---

### Post by quitus on 2008-07-28
Fa temps que tinc problemes per obrir els ports de l'enrutador. 

Resulta que si en el terminal hi poso ifconfig em surt que tinc la ip 192.168.1.2 però si clico en la icona de xarxa amb fil em surt 192.168.1.3

A part, amb el temps la configuració de l'enrutador amb canvia. Es un conceptronic C54APR2

salut.

---

### Post by papapep on 2008-07-28
...mmmm això que dius és MOLT curiós. L'ifconfig _només_ mostra una interfície configurada??

Enganxa aquí el resultat de la ordre, si us plau.

> A part, amb el temps la configuració de l'enrutador amb canvia. Es un conceptronic C54APR2

Respecte això, què preguntes? com saber la teva ip dinàmica externa del router? Què vols dir amb "la configuració de l'enrutador canvia"?

---

### Post by quitus on 2008-07-29
Quan dic que canvia la configuració, em refereixo als ports que havia obert i que de sobte en apagar i encendre l'ordinador tornen a estar tancats.

En aquest cas el ifconfig te la raó, vaig poder obrir els ports amb la ip 192.168.1.2 

després del ifconfig

```
marcimerce@marcimerce-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:d6:1c:d1  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fed6:1cd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2853289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3152591 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1871178458 (1.7 GB)  TX bytes:1690894630 (1.5 GB)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116856 (114.1 KB)  TX bytes:116856 (114.1 KB)

marcimerce@marcimerce-desktop:~$ 

```

ara la informació de la icona

---

### Post by papapep on 2008-07-29
Respecte el tema de la doble ip, el gnome-network-manager (dins el diàleg de configuració d'interfícies) també et mostra la 1.3?

Jo he tingut al llarg del temps MOLTS problemes amb el gnome-network-manager, i ja fa temps que vaig passar-me al **wicd** (gràcies Patrick) per configurar la xarxa tant ethernet com wifi, i em va de perilles.

---

### Post by quitus on 2008-07-29
gracies, he tirat pel dret i he instal·lat el wicd te molt bona pinta i la informació que dona sobre la ip es la correcta. Com configuro el wicd per que es connecti en engegar-se? No ho he trobat per enlloc, potser un script?

---

### Post by lluisanunez on 2008-07-29
Pots posar-lo a la sessió:
Sistema > Preferències > Sessions > Afegir

---

### Post by quitus on 2008-07-29
volia dir per que el wicd es connecti a la xarxa automàticament en iniciar, ja que li haig de dir cada vegada quan engego l'ordinador. Gracies

---


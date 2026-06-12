---
title: "Connexio mòbil amb Ubuntu"
date: 2008-03-23
forum: Catalan Team
---

### Post by crazyserver on 2008-03-23
Bé... la cosa és difícil.
M'he comprat un Dell XPS M1330. L'he formatat i li he instal·lat la última versió estable de l'Ubuntu (7.10). He fet funcionar TOT el que porta.. però em queda una petita cosa que vaig trobar que portava i no sabia:

Sota la bateria hi ha una ranura on posar una SIM de telèfon mòbil. Indagant he trobat que porta una mena de mòbil al seu interior, però no sé model, marca ni cap lloc on trobar aquesta informació (a dell tampoc...) XD
M'agradaria instal·lar drivers (o potser no cal) però em desespero quan no se per on començar (pq no sé el model, ni res).
Avui m'he adonat d'una cosa. A la configuració de Xarxa, surt la Wifi, la ethernet i un modem (cosa que el portatil no porta) pot ser que sigui aquest? De tota manera no se de quin dispositiu es tracta ni res... 
Alguna idea? Algu ha conectat el mobil ni que sigui amb usb?

Si no... provare d'instalar windows (es com tallar-se les venes) a veure que puc trobar (pq el drivers de windows si que els tinc)

 Gràcies!

---

### Post by CarlesOriol on 2008-03-24
Això sona a prova xunga de la gimcana. :-D

Au envia'ns els sospitosos habituals dmesg, lspci, lsusb ...

Per cert jo m'hi vaig trobar fa mig any amb un sony amb un modem com el que descrius tipus highsierra (em sembla recordar) i vaig tirar la tovallola.

Comentari OFFTOPIC. Si algú necessita una connexió internet collonuda amb l'ubuntu us recomano el mòbil sony ericsson w880i. El connectes i el detecta com una xarxa amb fil sense haver de fer absolutament res de res. (desconec si altres models de mòbil ho fan ho comento per que és el meu)

---

### Post by crazyserver on 2008-03-24
No se si caldrà un interminable dmesg...

LSPCI (diria k aqui no hi és):
```
 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) // VGA
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
```

LSUSB Aqui hi falta el blutooth que esta deshabilitat per la BIOS pero va al Bus 003 Dev 003 i és Broadcom:
```
 Bus 007 Device 004: ID 05a9:7670 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 15ca:00c3  
Bus 003 Device 001: ID 0000:0000 
```

L'Omnivision... deu ser la webcam? i el lector d'empremtes queda clar suposo XD

Bé us adjunto el dmesg sencer... però ja us aviso.. l'he mirat per sobre i dp he fet un grep net i no he trobat res... Potser el dispositiu està sense soldar XD
Vés a saber... però m'intriga que no hi hagi informació!

---

### Post by RainCT on 2008-03-24
Suposo que sí que deu ser el que et surt com a mòdem (jo em connecto amb un mòdem GPRS/UMTS extern i a la Gutsy el podia configurar com a mòdem normal i se'm connectava sol). A la Hardy ja me'l detecta com a dispositiu GPRS/UMTS, però en canvi m'ha deixat de funcionar (he hagut d'editar els arxius de configuració manualment per esborrar els canvis que hi havia fet i utilitzar un script que ja tenia per a la Feisty cada cop que em vull connectar).

---

### Post by crazyserver on 2008-03-24
Moltes gràcies a tots!
Però la meva inutilitat em supera... Prou dubtava jo...però volia que funcionés i avui m'he decidit a obrir el portàtil i mirar si realment aquesta targeta existia...
Evidentment si Ubuntu no la veu es perquè no existeix... És com si google no troba alguna cosa... ja m'enteneu. L'ordinador té la ranura posada per introduir la SIM, però la tarjeta controladora WWAN no hi és. Hi ha el banc on ha d'anar buit.
A part d'això RainCT: Ubuntu posa el mòdem per... no se pq però el posa, en tinguis o no! XDç

En fi, disculpeu les molèsties. Fins i tot he actualitzar la BIOS a veure si la reconeixia.. però res. Quan em compri la targeta que hi va, seguirem el fil.;)

---

### Post by CarlesOriol on 2008-03-25
T'ha costat gaire treure la tarjeta de telèfon del disipador?

---

### Post by crazyserver on 2008-03-25
He necessitat unes alicates que m'ha deixat el papapep, que es veu que eren d'un dentista... Ara amb el forat  ventila tot millor XD

Inútil perdut.. no se pq vaig a la universitat.. per fer això!XD

---

### Post by papapep on 2008-03-25
No dissimulis, que el que m'has demanat ha estat un martell i una escarpra, "manolillu".  Podries enviar-nos una foto de la regata com ha quedat??? (així no m'estranya que ventili bé) :-D

---

### Post by crazyserver on 2008-03-25
Si fa no fa...;) És un portàtil Dell-Vaio XD
[IMG]http://www.blogsmithmedia.com/www.engadget.com/media/2006/08/exploding-vaio.jpg[/IMG]

---

### Post by papapep on 2008-03-25
Ostres, si et funciona bé la solució potser m'ho haurè de plantejar pel meu. Últimament tinc la impresió de que s'escalfa una mica més que abans...

---

### Post by crazyserver on 2008-03-25
Fes, fes... el martell i l'escarpa són tot teus!
De totes maneres crec que encara el tens força bé de temperatura!

---

### Post by CarlesOriol on 2008-03-26
ITC:  I love this screensaver.

---

### Post by papapep on 2008-03-26
I jo encara diria més (Dupond i Dupont (tm)): [Nice screensaver]("http://youtube.com/watch?v=QMuFwLM6oBg") 

I think I need a stress machine :-D

---


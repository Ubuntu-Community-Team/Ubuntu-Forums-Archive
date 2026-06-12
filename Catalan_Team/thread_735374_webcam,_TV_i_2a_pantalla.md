---
title: "webcam, TV i 2a pantalla"
date: 2008-03-25
forum: Catalan Team
---

### Post by blopnotdid on 2008-03-25
M'he posat la beta de la Hardy i tot em va molt bé excepte que no sé com instal·lar la web cam i també que quan instal·lo el tv time o altres no em detecten la tarja de TV-TDT.
Un altre problema que tinc és que no puc posar la 2a pantalla. Amb el PC vell que porta una nVidia funciona bé, però aquest PC va amb una ATI integrada a la placa base. També la sortida DVI es diferent els pins que a l'altre pc, he comprat un adaptador nou i ja està, però ho comento per si pot tenir algo a veure.

---

### Post by menut on 2008-03-25
Per a la webcam, mira si es troba en aquesta llista (drivers UVC):

[http://linux-uvc.berlios.de/#devices]("http://linux-uvc.berlios.de/#devices")

Els pins del connector NO tenen res a veure, ja que et falla la part de drivers de l'Ubuntu.

Estàs segur de que no et detecta la targeta ? Busca-la al llistat de maquinari de l'Ubuntu.

---

### Post by blopnotdid on 2008-03-25
la targeta ATI si que me la detecta i em diu activar nose quins drivers per millorar el rendiment (crec ke em diu els drivers de la casa) i els activo i llavors els efectes d'entorn grafic van. Pero no s'encen la pantalla que tinc coenctada al DVI. I vaig a Screens & Graphics i alla tampoc surt a la llista. I a la targeta grafica posa Graphics card (VESA driver (generic)) i a sota driver: (menu desplegable)= fglrx
el nom de la targeta no se pq va integrat am una placa base, i al probar de posarla li vaig posar integrated noseke (ara no u recordo be) pero em vaig carregar la configuracio i haver-ho d'arreglar en modo de seguro o com es digui

---

### Post by blopnotdid on 2008-03-26
he estas mirant en varis foros i instalan varis drivers i res, i en cap forum he trobat solucio per webcams Microdia...

---

### Post by papapep on 2008-03-26
T'identifica la càmara i la placa el sistema? Enganxa'ns el que et mostri quan fas a un terminal:

```
lspci
```

i 

```
lsusb
```

---

### Post by blopnotdid on 2008-03-26
lspci:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 7930
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7932
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7936
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RS600 [Radeon Xpress 1200 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

lsusb:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 006: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 006 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 006 Device 004: ID 0784:1692 Vivitar, Inc. 
Bus 006 Device 003: ID 0c45:627b Microdia 
Bus 006 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 006 Device 001: ID 0000:0000

---

### Post by papapep on 2008-03-26
Doncs sembla que sí, que ho tens complicat. Suposo que ja havies trobat el grup de patidors de càmeres Microdia::[http://groups.google.com/group/microdia](http://groups.google.com/group/microdia) (per cert, la foto amb cadell de gat és genial)

[Aquí]("http://cirl.unex.es/consultas.php?opcion=1&ind=336&type=logged&ver=yes") tens una resposta que fan a un tema com el teu, tot i que no se sap si funciona o no (però com a molt et pots quedar com estàs).

Però vaja, excepte sorpreses agradables, crec que t'hauràs de seguir esperant a que el fabricant alliberi les especificacions (mira que en són de burros, les càmeres que vendrien...)

---

### Post by intel on 2008-04-16
I can't read Catalan dialect, sorry.
(online translators are not any good)

Please post on the google group pointed out above.

---

### Post by papapep on 2008-04-16
Hi Intel,

Thanks for your post.
BTW catalan is not a dialect, it's a language: [http://en.wikipedia.org/wiki/Catalan_language](http://en.wikipedia.org/wiki/Catalan_language).

---


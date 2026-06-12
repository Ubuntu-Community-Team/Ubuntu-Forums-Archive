---
title: "[SOLVED] Configuració nVidia C51G (GeForce 6100) [Era:Problema amb targeta nvidia int"
date: 2008-08-28
forum: Catalan Team
---

### Post by bolidoone on 2008-08-28
Hola a tothom,soc nou amb ubuntu,he terminat ara de instalar-lo pero no trobo un driver que funcioni amb la meva targeta grafica,es una targeta CineFX 3.0 i va integrada a una placa mare Gigabyte ga-m51gm-s2g.He intentat instal.lar drivers pero,cuan reinicio el ordinador,el monitor es queda tot negre (out of range) aixi donçs,solament puc posar una resolucio de pantalla de 800x600.

Algu em podri fer un cop de ma.
Gracies.

---

### Post by papapep on 2008-08-29
Benvingut, Bolidoone,

Abans que res, estaria bé que et passessis pels dos fils de capçalera pels benvinguts, el de benvinguda i el de forum-Tiquette ;-)

Respecte el teu problema, enganxa aquí el resultat de fer a un terminal:

```
lspci
```

---

### Post by bolidoone on 2008-08-29
gracies per la resposta,ara paso pels fils que em dius.

despres de fer lspci em diu aixo:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by papapep on 2008-08-29
Aquí la tenim:

> 00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

Doncs aquí: [https://answers.launchpad.net/ubuntu/+question/10156](https://answers.launchpad.net/ubuntu/+question/10156)

diuen que instal·lant el paquet **nvidia-glx-new**, i esborrant (més que esborrar-lo podries provar a canviar-li el nom per ara, a xorg.conf.backup per exemple) el fitxer /etc/X11/xorg.conf, i un cop reiniciis tot plegat, obtenen 1280x1024. Evidentment, jo no ho he provat pas.

---

### Post by bolidoone on 2008-08-29
aixo no lo he provat,pero no se molt be com fer-ho.
vaig a probar

---

### Post by papapep on 2008-08-29
Tot el que no entenguis ho preguntes. O et diem com fer-ho, o et donarem referències a documentació que ho expliqui. ;-)

---

### Post by bolidoone on 2008-08-29
solament em queda borar el fitxer,com tinc que fer-ho?

---

### Post by papapep on 2008-08-29
Una manera fàcil:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

així no l'esborres, li canvies el nom, que és més precavut.

---

### Post by bolidoone on 2008-08-29
gracies,ho provo ara mateix.

---

### Post by bolidoone on 2008-08-29
sembla que no funciona,continuo amb 800x600 i no em deixa pujar mes,m'he donat compte que no reconeix la marca ni el model del monitor,tindria que resoldre aquet problema no sigui per culpa del monitor i es quedi out of range.

---

### Post by papapep on 2008-08-29
Sé que és obvi, però a vegades...has reiniciat l'ordinador?

---

### Post by bolidoone on 2008-08-29
si,si. ho he reiniciat y surt una finestra dient que es posa en mode de baixa resolucio,que puc continuar aixi o seleccionar yo el hardware,en aquesta finestra trobo la tarja,pero no hi trobo el monitor,ho tinc que posar com monitor pug and play i aixi arranco el sisitema,i ara mateix em diu que el driver per aquesta tarja hi es habilitat pero,el monitor es desconegut,per aixo tinc els mues dubtes sobre qui es el causant del problema.

---

### Post by papapep on 2008-08-29
Jo provaria a posar un live-cd, reiniciar l'ordinador, i veure si em configura l'entorn gràfic a més resolució. Si realment ho fa, molts cops passa, fixa't en el contingut del /etc/X11/xorg.conf i a l'apartat corresponent del menú a veure com defineix i configura el monitor. Si ho intentes reproduïr un cop tret el live-cd al sistema instal·lat a l'ordinador, és possible que funcioni.

---

### Post by papapep on 2008-08-29
Per cert, enganxa, si us plau, el que et mostri fer:

```
ls -la /etc/X11/
```

---

### Post by bolidoone on 2008-08-29
aquesta tarda he desfet tot,tinc dos discs dur,en un he posat win xp i a l'altre ubuntu,llavors he desfet tot y desde live cd he intentat canviar la configuracio i no em deixava,seguia 800x600.Despres d'imstalar ubuntu,el primer que em diu es que habiliti el controlador restringit de la grafica,el mateix que em instal.lat aquesta tarda.Pero quan lo instal.lo i reinicio l'ordinador,em quedo out of range,ara,sense habilitar el controlador,quan faig  ls -la /etc/X11/ em diu aixo:
total 80
drwxr-xr-x  10 root root  4096 2008-07-02 12:17 .
drwxr-xr-x 120 root root  4096 2008-08-29 20:10 ..
drwxr-xr-x   2 root root  4096 2008-07-02 12:08 app-defaults
drwxr-xr-x   2 root root  4096 2008-07-02 12:10 cursors
-rw-r--r--   1 root root    14 2008-07-02 12:06 default-display-manager
drwxr-xr-x   6 root root  4096 2008-07-02 11:57 fonts
-rw-r--r--   1 root root 17394 2008-05-14 02:10 rgb.txt
lrwxrwxrwx   1 root root    13 2008-08-29 21:23 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2008-07-02 12:02 xinit
drwxr-xr-x   2 root root  4096 2008-07-02 11:49 xkb
-rw-r--r--   1 root  999  1225 2008-08-29 19:20 xorg.conf
drwxr-xr-x   2 root root  4096 2008-07-02 11:51 Xresources
drwxr-xr-x   2 root root  4096 2008-07-02 12:10 xserver
-rwxr-xr-x   1 root root  3730 2008-05-14 02:10 Xsession
drwxr-xr-x   2 root root  4096 2008-07-02 12:13 Xsession.d
-rw-r--r--   1 root root   265 2008-05-14 02:10 Xsession.options
-rw-------   1 root root   614 2008-07-02 11:51 Xwrapper.config
aquest es l'unic problema que tinc amb ubuntu,i sento molt que t'estiguis calentant el cap amb mi,si estigues segur que amb otra targeta de video ho soluciono,la canvio.De totes maneres,el monitor es un Videoseven L17PS,pero ubuntu no el coneix,em diu monitor desconegut i m'ho posa com plug and play,et digo aixo perque al instal.lar el controlador i reiniciar si que escolto com arranca el sistema pero el monitor es queda negre,aixo em dona que pensar,amb win xp tinc la resol.lucio a 1280x1024 que es el maxim que em permet el monitor.Ara intentare fer els mateixos passos d'abans,instalar desde gestor de paquets de symantec y canviant el nombre a xconfig.

T'ho dic una alta vegada,sento molt calentar-te tant el cap amb aixo.
Saluts

---

### Post by papapep on 2008-08-29
Hauries de provar el tema del live-cd, a veure a quina resolució t'ho deixa posar.

---

### Post by bolidoone on 2008-08-29
Ara estic desde live cd,la resolucio es la mateixa 800x600 he fet:

sudo gedit /etc/X11/xorg.conf

i al apartat de pantalla em surt aixo:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

he vist en altres llocs que aqui te que sortir les distintes configuracions de pantalla,a mi no em surt res.

continuo a liveCD per si vols que provi una altra cosa.

---

### Post by papapep on 2008-08-29
Buscant una mica més a fons, he trobat dues pàgines interessants:

- [Relació de plaques Nvidia]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia") que, teòricament , han de funcionar correctament amb Ubuntu. La teva entenc que és dins l'epígraf **GeForce 6 Series**.

- [Com resoldre problemes de resolució]("https://help.ubuntu.com/community/FixVideoResolutionHowto") (com el que tu tens) que es poden produir en aquestes, i altres, plaques.

Crec que fer un cop d'ull, sobretot a la segona, et pot ajudar.

---

### Post by bolidoone on 2008-08-29
Ho vaig a intentar,no estic molt posat amb el ingles pero,utilitzare un tradctor de pagines web a veure si soc capa|.

---

### Post by bolidoone on 2008-08-29
ooooooooohhhhhh!!!!!!!!
Ha funcionat,moltissimes gracies papapep,no estic molt segur de com ho he fet pero crec que,he modificat la linia per poder posar la tasa de refresc a xorg y despres,he habilitat el controlador,ara funciona amb totes les resolucions posibles.

---

### Post by papapep on 2008-08-30
Molt bé Xavi. Enhorabona!

[Ara ja pots marcar el fil com a resolt]("http://ubuntuforums.org/showthread.php?t=599965") :-)

> 
12.- Acabeu amb una nota sobre la solució

Com a conseqüència directa dels punts anteriors, és important acabar el fil explicant, si no s'ha fet abans, com s'ha arribat a la solució del problema. De pas, aprofiteu per marcar el fil com a resolt [SOLVED].

Això ho podreu fer un cop us identifiqueu amb el vostre usuari i contrassenya i anant al damunt del fil, fent clic a "Thread tools" i marcant l'opció "Mark this thread as solved". Tingueu present que això només ho podrà fer qui ha creat el fil o un dels moderadors del fòrum.


---

### Post by bolidoone on 2008-08-30
Com ho faig,ho poso al titol o i ha auna pestanya per posar-ho?

---

### Post by papapep on 2008-08-30
Ja t'ho he posat abans:

> Això ho podreu fer un cop us identifiqueu amb el vostre usuari i contrassenya i anant al damunt del fil, fent clic a "Thread tools" i marcant l'opció "Mark this thread as solved". Tingueu present que això només ho podrà fer qui ha creat el fil o un dels moderadors del fòrum.

:-D

---

### Post by papapep on 2008-08-30
Ja t'ho he posat abans:

> Això ho podreu fer un cop us identifiqueu amb el vostre usuari i contrassenya i anant al damunt del fil, fent clic a "Thread tools" i marcant l'opció "Mark this thread as solved". Tingueu present que això només ho podrà fer qui ha creat el fil o un dels moderadors del fòrum.

:-D

---


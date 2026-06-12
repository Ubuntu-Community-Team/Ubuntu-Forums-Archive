---
title: "[SOLVED] Ubuntu 8.04 i Atheros  AR242x no funciona [Era: no troba la xarxa wifi]"
date: 2008-05-05
forum: Catalan Team
---

### Post by diablessamariken on 2008-05-05
Hola

tot just acabo d'actualitzar l'Ubuntu amb la versió 8.04 des del gestor d'actualitzacions i tot ha anat bé fins que un cop reiniciat l'ordinador resulta que no em detecta la xarxa wifi que tinc a casa i no em puc connectar a internet!

A més, no sé quin problema tinc amb el firefox 3 beta 5 que està en mode fora de línia. Això deu voler dir que no troba la xarxa, no?

He vist que hi ha un munt de fils sobre coses similars però no acabo de trobar-ne cap que digui el que em caldria, crec...

A veure si em podeu orientar una mica.
Gràcies

Astrid

Salut, tabals i foc!

---

### Post by papapep on 2008-05-05
Astrid, sense saber quina placa inalàmbrica tens, ni tabals, ni foc, ni wifi...:-)

---

### Post by diablessamariken on 2008-05-05
cert, perdó:

802.11b/g wireless LAN

Així millor, oi?

De fet, puc afegir que quan intento configurar la connexió de manera manual no m'ofereix ni tan sols la possibilitat de configurar una connexió sense fil. És raro, raro...

Gràcies!

---

### Post by cortsenc on 2008-05-05
Bones Astrid!

Sóc l'Oriol de la colla grallera (cada cop més cortsencs i més cortsenques per aquí :))

Per començar, **802.11b/g** ho són la majoria de targetes WiFi del mercat, no és el número de model :P.

Podem començar per que ens enganxis el que et diu a la consola quan poses la següent comanda:

**iwlist scan**

Així sabrem si l'Ubuntu detecta la teva wireles o no, i en cas que la detecti quines xarxes agafa.

Per anar al terminal, has d'anar a **Aplicacions>Accesoris>Terminal**

---

### Post by menut on 2008-05-05
No dones cap informació rellevant...

Has de dir fabricant, model, etc :)

---

### Post by MorlanXaos on 2008-05-05
Hola, jo vaig tenir un problema similar. Al actualitzar-me, el drivers "propietaris" que vaig instal.lar en el seu moment, es van esfumar!?, i per això em vaig quedar sense conexiò. 

Per tant va ser questiò de tornar a instalar el drivers una altre vegada, utilitzant el Nsdiswrapper driver utlity, configurar la red i a corre.

No se si es aquest el cas, de que vas fer servir drivers propietaris quant vas instal.lar l'Ubuntu per primer cop o no.

De totes maneres com diu en cortsenc, fent iwlist scan, sabras si agafa la xarxa o no. En el cas de que no, llavors podria ser això.

---

### Post by diablessamariken on 2008-05-05
hola Cortsenc, quina sorpresa!!! i la resta!

lo interface doesn't support scanning
eth0 interface doesn't support scanning

Això diu la consola després de posar "iwlist scan"


Mirant els controladors que hi ha actius, identifica el següent:

Atheros Hardware Access Layer (HAL) (Habilitat i en ús)
Controlador gràfic amb acceleració d'ATI (deshabilitat i no s'està usant)
Support for Atheros 802.11 wireless LAN cards (habilitat i en ús)


Aquesta darrera deu ser la targeta del wifi, no? i com és que no la reconeix? ai mare...

Gràcies per la paciència!!

Astrid

---

### Post by papapep on 2008-05-05
Enganxa el que et surti en fer en un terminal:

```
lspci|grep Network
```

---

### Post by diablessamariken on 2008-05-05
ei Papapep

no em surt res de res després de posar la comanda que em dius...

---

### Post by papapep on 2008-05-05
......mmm....doncs enganxa tot el que et surti fent:

```
lspci
```

(esperem que no sigui massa llarg :-))

---

### Post by diablessamariken on 2008-05-06
Ei

després de fer "lspci" m'ha sortit això:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
```

No sé què vol dir... espero "instruccions" :)

Gràcies

---

### Post by CarlesOriol on 2008-05-06
Vaig a especular:

1. De el iwlist al lspci pots haver apretat alguna tecla de wifi al portàtil que l'hagi desactivat fisicament.

  Comprova-ho apreta les tecles i torna a fer un lspci ( a vegades jo ho he vist en un hp no hi ha ni resposta després de fer-ho, però sempre veus si passa res escrivint dmesg)

2. Algunes atheros son xungues de configurar i cal recompilar el modul del nucli. Quan es fa això és habitual que al haver un canvi de versió del nucli (i evidentment un canvi de versió d'ubuntu fa un canvi de nucli) calgui recompilar-ho.
Recordes haver fet res especial amb la versió anterior?

---

### Post by diablessamariken on 2008-05-06
Hola

hi ha una mena de botó al portàtil que desactiva i activa la wifi, però per defecte està sempre encesa a no ser que la desactivis, ja ho vaig provar.

Pel què fa a la primera instal·lació que vaig fer de l'Ubuntu vaig seguir un fil d'un forum que ara mateix sóc incapaç de tornar a trobar i que no sabria reproduir, seguiré buscant-ho a veure si ho trobo, però potser hauria de baixar-me els drivers de nou? com ho puc fer?

---

### Post by papapep on 2008-05-06
Aquí: [http://www.ubuntu-es.org/index.php?q=node/83813](http://www.ubuntu-es.org/index.php?q=node/83813)

diuen que els funciona amb les instruccions que indiquen i el driver Madwifi

---

### Post by diablessamariken on 2008-05-06
Hola de nou

després de molt cercar ja sé quina wifi tinc i alguna cosa més.

Atheros AR242x que segons sembla és la mateixa que: AR5BXB63
en un ACER ASPIRE 5104WLMi

He trobat alguns forums de gent que ha tingut problemes similars i n'hi ha un de molt guiat, però no acaba de ser ben bé pel mateix model de portàtil i no sé si això pot fer que no funcioni igual.

[http://kaleimn.blogspot.com/2007/10/si-voltean-su-notebook-vern-esto.html]("http://kaleimn.blogspot.com/2007/10/si-voltean-su-notebook-vern-esto.html")

A més, l'home suggereix que eliminem els moduls restringits però jo en tinc molts d'instal·lats (per defecte eh) i no sé què implicaria eliminar-los...

Sento donar males informacions o poc completes, però vaig molt perduda! sóc una novata total!! 

Gràcies

---

### Post by diablessamariken on 2008-05-07
Visca!!

he seguit les instruccions de l'últim post d'en Papapep i ara ja funciona!!

Gràcies!!

Astrid

---

### Post by diablessamariken on 2008-05-07
Estic intentant marcar el fil com a SOLVED però no en trobo l'opció, jo creia que era a THREAD TOOLS...

Bé, doncs això, que està SOLVED

---

### Post by lluisanunez on 2008-05-07
Felicitats!
El **solved** va desaparèixer amb el darrer maquillatge dels fòrums, esperem que el tornaran a posar

---


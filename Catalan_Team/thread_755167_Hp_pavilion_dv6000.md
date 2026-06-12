---
title: "Hp pavilion dv6000"
date: 2008-04-14
forum: Catalan Team
---

### Post by Kururu on 2008-04-14
M'acabo de comprar un [portatil]("http://www.carrefouronline.carrefour.es/noalimentacion/TemplateProduct.aspx?itemMarcado=catalog310026&navAction=push&navCount=5&menu=no&nivel_desplegado=nivel2_4&itemId=37603355") nou, com sempre, ve amb windows vista i el primer que he fet ha sigut intentar instalar ubuntu però me trobat amb el següent:
quan ficava el cd, despres del menu de boot s'està molta estona amb la pantalla negra fins que surt que ubuntu està corrent amb low graphics mode. configuri el que configuri, no arrenca.
He provat amb tots els commands que posa en aquesta [web]("https://wiki.ubuntu.com/HP_dv6000_Series#head-3098c05ddf52133f6c0c8252fca3b7737db434be") però res.
Alguna idea?

---

### Post by papapep on 2008-04-14
Has provat passant-li a l'arrencada al kernel?:

```
noapic noloapic
```

---

### Post by menut on 2008-04-14
Espero que ho hagis intentat amb el cd per a processadors de 64 Bits...

---

### Post by Kururu on 2008-04-14
> **menut said:**
> Espero que ho hagis intentat amb el cd per a processadors de 64 Bits...

Sí, clar! xD

Papapep, també ho he intentat però res.

---

### Post by papapep on 2008-04-14
Però a quin punt de l'arrencada se't queda?? Treu el quiet i l'splash de l'arrencada per que puguis veure tot el procés, sinó estem tots a les fosques.

---

### Post by Kururu on 2008-04-15
Doncs em surt això: 
bcm43xx: Error: Microcode "bcm43xx_microcodes.fw not available or load failed

---

### Post by papapep on 2008-04-15
Si no recordo malament, la Hardy ja fa funcionar correctament (amb els controladors restringits) aquesta placa de wifi (la bcm43). Jo provaria a instal·lar-la. Juraria que hi ha com a mínim un o dos fils que en parlen al fòrum.

---

### Post by Kururu on 2008-04-16
> **papapep said:**
> Si no recordo malament, la Hardy ja fa funcionar correctament (amb els controladors restringits) aquesta placa de wifi (la bcm43). Jo provaria a instal·lar-la. Juraria que hi ha com a mínim un o dos fils que en parlen al fòrum.

bé, he aconseguit arrencar-lo i instalar-lo posant que iniciés amb low graphics mode, el problema es que ara no em funciona ni l'internet ni els ports usb. Em sembla que m'esperaré a Hardy  a veure què tal m'anirà

---

### Post by CarlesOriol on 2008-04-16
> **Kururu said:**
> Doncs em surt això: 
bcm43xx: Error: Microcode "bcm43xx_microcodes.fw not available or load failed

Això és el firmware privatiu de la tagertawifi. 

Ja el gutsy ho insta&#320;la automàticament però per fer-ho cal que la màquina estigui connectada a internet per cable per tal de descarregar aquest arxiu.

---

### Post by elbuit on 2008-04-17
Jo tinc un dv6000, concretament dv6624 i també disposa d'una broadcom.
El driver actual no funciona (bcmx43) i  hi han dos opcions:
-1ª emprar ndiswrapper+ driver de windows (jo ho faig així, amb un driver d'un portatil de dell, ja et buscaré l'enllaç quan arribe a casa)
2ª-Opció es emprar el driver nou b43 (ara ja no es bcmx43), i te'l pots pillar a [www.linuxwireless.org](www.linuxwireless.org)), lo que passa es que les ultimes versions no em van. Empre una versio anterior.
Amb la segona opció tens monitorització, pero em donava problemes si iniciava el equip sense alimentacio (sols en mode bateria), així que supose que serà acpi.
Jo et recomane la primera, o ambdos (jo tinc les dos, i depenent del que vull faig una cosa o altra)
Estic parlant de Gusty, suppose que a hardy al ser un nucli més nou ja hauran inclos els nous drivers (b43) i sols caldrà el firmware.
Lo dit, quan arribe a casa t'ho mire.
Un abraç

---

### Post by elbuit on 2008-04-17
Ja he arribat a casa.
El driver de Windows que empre jo està ací:

[http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE)
Caldria fer:
```
wget http://ftp.us.dell.com/network/R140747.EXE
unzip R140747.EXE
```
entre els axius que t'extrau hi ha una carpeta que s'anomena drivers
ahí estan els drivers, que amb un:
```
 sudo ndiswrapper -i Driver/bcmwl5.inf
```
Te'l instal·laria.
de totes formes ja queda poc per a la Hardy, i tal com diuen ja estarà suportada

---

### Post by CarlesOriol on 2008-04-17
No tinc cap ordinador per provar-ho però crec recordar que a més cal posar el bcm43 o b43 a la blacklist per que no carregui els dos controladors no?

---

### Post by elbuit on 2008-04-17
Tens raó, en el meu cas tinc "blacklisted":
blacklist bcm43xx
blacklist b43
Per que empre ndiswrapper.
Si per alguna questio vull emprar b43 que soporta mode monitor, doncs lleve el modul del ndiswrapper i carregue el b43.(Obviament cal "baixar" la interfície)

Un abraç

---

### Post by CarlesOriol on 2008-04-17
el bcm43 sols funcionava a 11 Mbs

---

### Post by elbuit on 2008-04-21
Ahir em vaig actualitzar a Hardy al portàtil a tal de provar-la.
Sembla que la meva targeta no esta encara suportada (ho estarà en els nuclis 2.6.25) ja que es la segona revisió.
A tal de fer-la funcionar, cal aplicar-li un pegat al nucli, concretament als mòduls ssb i b43) per a que funcione.
El pegat es troba disponible a:
[http://www.linuxwireless.org/download/b43/patch_2.6.24_for_4311_2](http://www.linuxwireless.org/download/b43/patch_2.6.24_for_4311_2)
i arreu d'Internet hi han diversos tutorials de com fer-ho anar, com per exemple aquest:
[http://kernelcat.wordpress.com/2008/04/18/wifi-amb-targetes-broadcom-sense-ndiswrapper/](http://kernelcat.wordpress.com/2008/04/18/wifi-amb-targetes-broadcom-sense-ndiswrapper/)

---


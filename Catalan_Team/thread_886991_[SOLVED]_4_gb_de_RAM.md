---
title: "[SOLVED] 4 gb de RAM"
date: 2008-08-11
forum: Catalan Team
---

### Post by freski on 2008-08-11
Acabo d'instal·lar-me l'Ubuntu 8.04 en un portàtil que té 4 gb de memòria RAM. Abans d'instal·lar-lo vaig estar buscant i vaig veure que necessitava la versió de 64 bits per a poder utilitzar tota la memòria, però ara no sé si ja està activada automàticament o s'ha de fer alguna cosa.

Gràcies!

---

### Post by papapep on 2008-08-11
Amb un sistema de 32 bits també pots accedir als 4Gb, sempre que tinguis el [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") activat. En cas contrari només podràs accedir directament a 3-3,5 Gb ja que la resta els reserva per coses del sistema.
En 32 bits cal tenir un kernel amb el paràmetre del kernel CONFIG_HIGHMEM64G activat. Ubuntu Desktop no ho porta per defecte. El kernel d'Ubuntu Server sí, pero és millor no barrejar les coses i, si realment et cal accedir als 4 Gb, recompilar el kernel amb el paràmetre tu mateix.

En 64 no sé si ja ve "de fàbrica" activat o no, tot i que per lògica així hauria de ser.


PD Benvingut al fòrum ;-)

---

### Post by freski on 2008-08-11
Doncs espero que ja vingui "de fàbrica"... ;)

Gràcies!

---

### Post by CarlesOriol on 2008-08-12
freski: Veig pel fil de benvinguda que ets nou. El començar al mon del programari lliure amb una 64 bits pot ser que et compliqui bastant la iniciació ja que moltes coses no hi son i d'altres les trobaràs complicades.
(pot llegir-ne moltes referències en aquest mateix fòrum)

D'altra banda per un ordinador d'escriptori en linux veuras que amb 1 Gb la màquina funciona extraordinariament bé. (tot i que també pot funcionar amb menys memòria).

papapep: Quan la mida dels registres d'adreces d'un processador és de 64 bits no precisa d'extensions per gestionar-les. Per tant no és que "vingui de fàbrica" és que senzillament no li cal.

---

### Post by papapep on 2008-08-12
> tot i que **per lògica** així hauria de ser significa --> els processadors de 64 bits ja direccionen ells solets 4 Gb (i més, clar).

---

### Post by CarlesOriol on 2008-08-12
> **papapep said:**
> Amb un sistema de 32 bits també pots accedir als 4Gb, sempre que tinguis el [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") activat

...

En 64 no sé si ja ve "de fàbrica" activat o no, tot i que per lògica així hauria de ser.

papapep: fas trampes amb les paraules.
El PAE com els controladors antics que anaven en DOS al config.sys com himem... etc, no deixen de ser pedaços per superar una limitació d'una arquitectura.

---

### Post by papapep on 2008-08-12
I a tu qui t'ha dit que el que surt pels meus dits és el que circula per la meva neurona???? :-P

---

### Post by Rubunter on 2008-08-12
Jo tinc ubuntu 64 bits i 4GB de RAM i només me'n utilitza 3. La resta es comparteixen entre la PCI i la gràfica. La bios els veu tots quatre i el windows també, però d'efectius (tan en ubuntu com en windows) només en són 3. Em vaig posar en contacte amb Toshiba per demanar explicacions, ja que a la web hi deia que l'ordinador accepta fins a 4GB de RAM i, no van poder fer res més que donar-me la raó (em van atendre en Català, fet que em va rebaixar l'emprenyamenta inicial).Fins i tot em van dir que tenia dret a estar enfadat, que s'apuntava la queixa. No crec que canviin la manera de fer les coses, però com a mínim que quedi constància que tenen un client descontent. Això passa amb el chip Intel 945.

---


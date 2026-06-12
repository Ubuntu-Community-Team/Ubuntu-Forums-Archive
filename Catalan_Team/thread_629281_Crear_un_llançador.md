---
title: "Crear un llançador"
date: 2007-12-02
forum: Catalan Team
---

### Post by alhanduin on 2007-12-02
Bones!

Vull crear un llançador que m'executi la següent frase quan hi faci doble click:

$ sudo ln -sb /dev/ttyUSB0 /dev/ttyS0

Aquesta frase és la que faig sevir cada vegada que he d'enxufar el gps a l'ordenador mitjançant el port usb-serial i serveix per transfomar el port usb1 en un port seial1. 

La cosa és que si creo un llançador amb aquesta frase no funciona... suposo xq al haver-hi la paraula sudo necessito introduir la contrassenya... Algú sap com ho puc fer????

Moltes gràcies per adelantat

---

### Post by papapep on 2007-12-02
El que fa aquesta ordre

```
$ sudo ln -sb /dev/ttyUSB0 /dev/ttyS0
```

és crear un enllaç simbòlic entre el dispositiu que "connecta" amb el port USB i el que representa el port RS232 que el teu ordinador, com el meu, no té. Fet pel qual, tot el que el programa envia, o reb, pel port sèrie (virtual) és redirigit al port USB (real).

Aleshores, perquè no et funciona simplement posant aquesta ordre a la llançadora? Doncs per que li cal obrir una shell (terminal) per a funcionar, **ln** és una ordre de terminal. Així doncs, cal que creis un fitxer el qual serà el que executis per a invocar la ordre.

Obrim un editor de terminal, per crear el fitxer que executarà la llançadora:

```
sudo nano /home/serie_usb.sh
```

i hi fiques dins:

```
#!bin/bash
sudo ln -sb /dev/ttyUSB0 /dev/ttyS0

```

surts desant, prement Ctrl+X.

Un cop fet això, cal donar-li permisos d'execució:

```
sudo chmod +x /home/serie_usb.sh 
```

I ara, ja pots crear la llençadora i posar-hi com a fitxer a executar /home/serie_usb.sh.

Així t'hauria de funcionar.

---

### Post by alhanduin on 2007-12-02
Gràcies papapep xq sempre m respons tots els dubtes! xo no m'ha funcionat.... em surt:

Detalles: Ha ocurrido un error al ejecutar el proceso hijo «/home/serie_usb.sh» (No existe el fichero ó directorio

---

### Post by papapep on 2007-12-02
A tot el procés, on t'he ficat /home, fica-hi /home/nom_del_teu_usuari

---

### Post by RainCT on 2007-12-02
Si això no et funciona, prova canviant el «sudo» per un «gksudo».

---

### Post by orestesmas on 2007-12-03
> **alhanduin said:**
> Bones!

Vull crear un llançador que m'executi la següent frase quan hi faci doble click:

$ sudo ln -sb /dev/ttyUSB0 /dev/ttyS0

Aquesta frase és la que faig sevir cada vegada que he d'enxufar el gps a l'ordenador mitjançant el port usb-serial i serveix per transfomar el port usb1 en un port seial1. 


No ho acabo de captar: segons això, estàs "tapant" un port sèrie normal amb el port sèrie simulat que crea el GPS quan l'endolles via USB. No seria més senzill dir-li a l'aplicació que fas servir que usi /dev/ttyUSB0 enlloc de /dev/ttyS0? No sé quina aplicació deu ser, però com a opció elemental hauria de deixar configurar el port sèrie que ha d'utilitzar, no?

D'altra banda penso que la manera més correcta de fer això seria en tot cas instruir el sistema UDEV per tal que, en connectar el teu GPS, crei els enllaços simbòlics i estableixi els permisos necessaris per tal que tot funcioni. Qualsevol altra solució és una mica "guarra", peró vaja, potser això són qüestions estètiques...

---

### Post by papapep on 2007-12-03
> No ho acabo de captar: segons això, estàs "tapant" un port sèrie normal amb el port sèrie simulat que crea el GPS quan l'endolles via USB

Si, per enganyar al programa que només sap fer-ho per port sèrie i amb l'afegit de que el seu ordinador no té port sèrie físic real.
Segur que el teu sistema és més correcte, però quan no se'n sap més... (parlo per mi) :-D

---


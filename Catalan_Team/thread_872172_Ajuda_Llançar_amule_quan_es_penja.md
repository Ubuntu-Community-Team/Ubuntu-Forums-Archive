---
title: "Ajuda: Llançar amule quan es penja"
date: 2008-07-27
forum: Catalan Team
---

### Post by _iridium_ on 2008-07-27
Hola nois:

Abans d'anar de vacances, volia deixar preparat un script per si l'amule es penja, que el crontab el tornès a arrancar.......:lolflag:

Si el llanço des d'un terminal funciona sense problemes, però des del crontab no hi ha manera :confused:......i no se veure quin error pot estar passant. Algú em pot donar un cop de mà?

```

#!/bin/bash
#Busquem si l'amule s'està execuant
#set -xv
if [ -z "$(ps -A | grep amule)" ]
then {
       /usr/bin/amule >> /home/fran/Scripts/log_amule
       echo "S'esta iniciant l'amule" >> /home/fran/Scripts/log_amule  
       date >> /home/fran/Scripts/log_amule
       id >> /home/fran/Scripts/log_amule
}
    else {
       echo "El procès amule està executant-se" >> /home/fran/Scripts/log_amule 
       date >> /home/fran/Scripts/log_amule
       id >> /home/fran/Scripts/log_amule
}
fi
#exit 0

```

Adjunto també el log; el crontab executa el script cada minut, i això és el que es graba....

```

S'esta iniciant l'amule
dl jul 28 00:42:01 CEST 2008
uid=1002(fran) gid=1004(fran) grups=4(adm),20(dialout),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),106(fuse),108(lpadmin),110(admin),125(sambashare),1002(vboxusers),1004(fran)

```

Com veieu..........al log no apareix res de res de com ha anat "l'intent" d'arrencar l'amule.

Salutacions,
Francesc.

---

### Post by _iridium_ on 2008-07-28
Ningú em pot ajudar amb l'script?  :lolflag:

Mil gràcies avançades,
:popcorn::popcorn:

---

### Post by papapep on 2008-07-28
Si us plau, no pugis el fil artificialment. Si no et responen pot ser per vàries causes: no volen, no poden, no saben. :-)

---

### Post by orestesmas on 2008-07-29
> **_iridium_ said:**
> Ningú em pot ajudar amb l'script

Jo no sé massa bash (sempre m'haig de mirar el manual quan m'hi poso, cosa que, d'altra banda, s'hauria de fer sempre), però d'entrada diria que manca un ";" abans del "then", i d'altra banda jo no he vist en cap exemple dels que acabo de mirar (bàsicament els scripts de /etc/init.d) que els blocs de sentències del "then" i de l'"else" vagin entre claudàtors "{ }".

Pots explorar per aquí.

---

### Post by oriolsbd on 2008-07-29
Hola a tothom.

Jo he treballat amb diversos intèrprets (sobretot ksh), però amb "bash" he fet poca cosa. No he comentat res en aquest fòrum perquè ja havia contestat una mica (fins on jo sé) a la mateixa pregunta quan en Francesc l'havia fet al fòrum de SomGNU.

Abans que res, per l'Orestes, no cal posar el ";" abans del then. Realment, el ";" indica que comença una nova sentència, el mateix que es fa amb un "Enter", que és el que ha posat el Francesc.

Apart d'això, jo també tenia el mateix dubte que tu quant als "{ }", però he comprovat que funciona igual.

El problema que hi ha amb aquesta shell (i no en sé el motiu) és que si s'executa des de terminal va bé, però si s'executa amb el cron no funciona la següent línia:
```
 /usr/bin/amule >> /home/fran/Scripts/log_amule
```

Quan ho vaig estar provant, vaig posar una línia "echo $?" després d'aquesta que dóna error. Per qui no ho sàpiga, a la variable $? hi ha sempre el Return Code de l'última sentència executada. Doncs bé, quan s'executa la shell per terminal, em dóna "$?=0" (és a dir, final ok) i quan s'executa per cron, dóna "$?=255"!!!

En el fòrum de SomGNU, li vaig proposar d'executar l'amule en background (afegint " &" al final de la línia), però seguia fallant. I aquí em vaig quedar.

Salut!

---

### Post by papapep on 2008-07-29
Això poden ser moltes coses diferents, que hauries de verificar:

- Permisos dels fitxers, directoris implicats.
- Que els paths que poses siguin tots correctes.
- Que alguna variable d'entorn que està correctament definida quan executes l'script al terminal no estigui accessible a cron (entenc que l'has posat al cron de l'usuari regular).
....


Jo el que faria és partir l'script i anar provant trocets, a veure quins funcionen i quins no, per aïllar el problema. Seria el més pràctic, i més amb un script petitó com aquest.

---

### Post by _iridium_ on 2008-07-29
Hola nois:

He trobat el que passava.........adjunto l'script final per si algú també vol automatitzar l'amule......  :roll: 

```

#!/bin/bash
#Busquem si l'amule s'està execuant
#set -xv
if [ -z "$(ps -A | grep amule)" ]
then {
       # Al tractar-se d'una aplicació gràfica, l'executem amb el "display" de l'usuari en curs
       DISPLAY=:0.0 /usr/bin/amule &
       echo "S'està iniciant l'amule" >> /home/fran/Scripts/log_amule  
       date >> /home/fran/Scripts/log_amule
       id >> /home/fran/Scripts/log_amule
}
    else {
       echo "El procès amule està executant-se" >> /home/fran/Scripts/log_amule 
       date >> /home/fran/Scripts/log_amule
       id >> /home/fran/Scripts/log_amule
}
fi

```


A millorar...........i que no sé com.  8)  8) 

Ara mateix està en "hardcode" DISPLAY=:0.0..........si l'usuari no fa servir aquest Display, llavors segueix sense funcionar.....alguna idea de com millorar l'script?

Estava provant de fer

```

prova=$DISPLAY
$prova /usr/bin/amule &

```
però no acaba d'anar bé.

Salut i bones vacances!!
(Vaig a fer bones acciones per l'Índia.)
Francesc.

---

### Post by patrickfromspain on 2008-07-29
home, esta prou be. Pero no li veig massa sentit. Que pasa si l'amule es queda pillat? Es a dir, no s'ha tancat i s'ha quedat parat. L'script no faria res no?

---


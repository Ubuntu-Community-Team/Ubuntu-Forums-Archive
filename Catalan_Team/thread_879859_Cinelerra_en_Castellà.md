---
title: "Cinelerra en Castellà"
date: 2008-08-04
forum: Catalan Team
---

### Post by Pablitus on 2008-08-04
Salut!! Molt bones!!

Estic aprofitant dies de vacances que estic per Barcelona per editar uns vídeos de la banda on toco amb cinelerra, i no he aconseguit fer-lo anar en castellà. Bé, si, posant el castellà com a llengua predeterminada en el suport d'idioma, però això em passa tot el sistema al castellà. He provat do fer en el terminat, sense saber ben bé què vol dir: "export LANG es_ES", i després "cinelerra", i diferents combinacions d'això, i no m'ha funcionat res. 

També he trobat un arxiu que sembla que hi tingui a veure, però no l'entenc per poderlo editar:


#!/bin/bash



if cat ca_ES.UTF-8 | grep ru; then code=KOI8-R; else code=ISO-8859-15; fi
if [ "$UID" = "0" ]; 
  then 
  env LIBXCB_ALLOW_SLOPPY_LOCK=true LANG=$(echo $LANG | sed -e s/UTF-8/$code/g) nice -n -15 /usr/bin/cinelerra $@

  else 
  env LIBXCB_ALLOW_SLOPPY_LOCK=true LANG=$(echo $LANG | sed -e s/UTF-8/$code/g) /usr/bin/cinelerra $@

fi 

exit 0


Teniu alguna idea? Aquest arxiu que poso hi té a veure? Gràcies per avançat!!

---

### Post by LitusMayol on 2008-08-05
Bones **Pablitus**!

Jo diria que si que hi té a veure: i molt. Però no sé exactament què...xD

Diria que el que necessites fer és:
```
$ localedef -c -i es_ES -f ISO-8859-15 es_ES.ISO-8859-15

```
i després
```
$ env LANG=$(echo $LANG | sed -e s/UTF-8/ISO-8859-15/g) cinelerra
```
Això te l'hauria de posar en castellà (em sembla que en català encara no hi ha traducció).


Proba-ho, ja diràs si funciona ;)

---

### Post by Pablitus on 2008-08-05
Gràcies **Litus**, però no ha funcionat. Entenc que el que em dius és que posi aquestes ordres al terminal, no? Doncs així he fet i res, continua en anglès. Per cert, si no et fa pal em podries dir més o menys què vol dir:> $ localedef -c -i es_ES -f ISO-8859-15 es_ES.ISO-8859-15i> $ env LANG=$(echo $LANG | sed -e s/UTF-8/ISO-8859-15/g) cinelerra. 

Remenant remenant he trobat un altre fitxer anomenat *cinestart* a /etc/init.d que diu així:> #!/bin/bash
 
if ! localedef --list-archive | grep de_DE | grep iso885915 &> /dev/null
then localedef -c -i de_DE -f ISO-8859-15 de_DE.ISO-8859-15
fi

if ! localedef --list-archive | grep es_ES | grep iso885915 &> /dev/null
then localedef -c -i es_ES -f ISO-8859-15 es_ES.ISO-8859-15
fi

if ! localedef --list-archive | grep fr_FR | grep iso885915 &> /dev/null
then localedef -c -i fr_FR -f ISO-8859-15 fr_FR.ISO-8859-15
fi

if ! localedef --list-archive | grep it_IT | grep iso885915 &> /dev/null
then localedef -c -i it_IT -f ISO-8859-15 it_IT.ISO-8859-15
fi

if ! localedef --list-archive | grep pt_BR | grep iso885915 &> /dev/null
then localedef -c -i pt_BR -f ISO-8859-15 pt_BR.ISO-8859-15
fi

if ! localedef --list-archive | grep sl_SI | grep iso885915 &> /dev/null
then localedef -c -i sl_SI -f ISO-8859-15 sl_SI.ISO-8859-15
fi

if ! localedef --list-archive | grep eu_ES | grep iso885915 &> /dev/null
then localedef -c -i eu_ES -f ISO-8859-15 eu_ES.ISO-8859-15
fi

if ! localedef --list-archive | grep eu_FR | grep iso885915 &> /dev/null
then localedef -c -i eu_FR -f ISO-8859-15 eu_FR.ISO-8859-15
fi

# this add koi8 ru_RU exception
if ! localedef --list-archive | grep ru_RU | grep koi8
then localedef -c -i ru_RU -f KOI8-R ru_RU.KOI8-R
fi

# this try to add iso-8859-15 to your lang ( usefull to build new lang)
if ! localedef --list-archive | grep ca_ES | grep iso885915 &> /dev/null
then localedef -c -i ca_ES -f ISO-8859-15 ca_ES.ISO-8859-15
fi

echo "0x7fffffff" > /proc/sys/kernel/shmmax He provat d'editar-lo però no m'ha funcionat, i també té pinta de tenir-hi a veure, no? :confused:

Vamos, d'això se'n diu en castellà dar palos de ciego. Ah, lo de posar-lo en castellà és perquè no té traducció al català...

Seguirem remenant...

---

### Post by LitusMayol on 2008-08-05
**Pablitus**!

A veure, ho sento és que abans t'he escric des de la feina i he anat molt "*a saco*".


```
$ localedef -c -i es_ES -f ISO-8859-15 es_ES.ISO-8859-15
```
Amb aquesta comanda, el que fas és crear el *charset* (que em sembla que era *char*acter-*set*) per a l'idioma determinat que escriguis, en aquest cas el Castellà (es_ES) amb el ISO-8859-15.

```
$ env LANG=$(echo $LANG | sed -e s/UTF-8/ISO-8859-15/g) cinelerra
```
Amb aquesta el que fas és dir-li que utilitzi aquest "*charset*" que hem creat.


Però si això no et va...

Jo provaria d'entrar a la consola:
```
$ gksu gedit /etc/init.d/cinestart
```

Et demanarà la contrasenya de *root*. Això el que farà serà obrir-te l'arxiu "*cinestart*" amb el Gedit (per poder editar de l'estil **Bloc de notas**), però en mode d'Administrador (per això et demana la contrasenya).

Aleshores a aquesta línies:
```
# this try to add iso-8859-15 to your lang ( usefull to build new lang)
if ! localedef --list-archive | grep ca_ES | grep iso885915 &> /dev/null
then localedef -c -i ca_ES -f ISO-8859-15 ca_ES.ISO-8859-15
fi
```
Li esborraria el "#" de la primera. 

Aleshores guarda l'arxiu (a d'alt a l'esquerra et surt el simbolet del disquet per desar). I probar d'engegar-lo de nou.



Si així no et va, proba de fer (també a la consola):
```
export LANG=es_ES LANGUAGE=es_ES
```
i tot seguit:
```
cinelarra
```


Si tampoc funciona, torna a posar el "#" a on estava (per si de cas) de la mateixa manera que l'has tret. I digues que et diu.


Seguirem investigant!

---

### Post by Pablitus on 2008-08-05
Noooop. Res. Acabo de provar les diferents solucions proposades i no han donat resultat. En iniciar Cinelerra al terminal hi surt el següent missatge> [COLOR="Red"]cat: ca_ES.UTF-8: No such file or directory[/COLOR]
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on lun giu 30 11:09:09 UTC 2008
 i s'inicia cinelerra en anglès.

Segur que es deu poder fer (qui sap com...), perquè posant com a llengua per defecte del sistema el castellà a suport d'idioma bé que l'obre en castellà. O sigui que la traducció bé que la tinc. El problema és que funcioni en castellà tenint l'ordinador en català. 

Per avui s'han acabat les provatures. Continuarà...

Ah, alguna de les ordres que he provat les he de desfer?, o sigui, amb> localedef -c -i es_ES -f ISO-8859-15 es_ES.ISO-8859-15
> export LANG=es_ES LANGUAGE=es_EShe canviat algo que hagi de tornar a posar tal com estava?

Gràcies!!

---

### Post by LitusMayol on 2008-08-07
Bones **Pablitus**!


A veure això:```
if ! localedef --list-archive | grep es_ES | grep iso885915 &> /dev/null
then localedef -c -i es_ES -f ISO-8859-15 es_ES.ISO-8859-15
fi
```
vol dir que té el castellà, i per això quan poses el sistema en castellà te'l posa. 

Ara el tema és aconseguir que es posi en castellà tot i que el sistema no hi estigui,no?

Proba aquestes tínies
```
$ localedef -c -i ca_ES -f KOI8-R ca_ES.KOI8-R
```
i després
```
cinelerra
```
si així et seguís sense funcionar... 
;)

---

### Post by Pablitus on 2008-08-08
Gràcies Litus!

Ho acabo de provar i tampoc...

De totes maneres he trobat una solució alternativa que em satisfà: en 8 Gigues que tenia lliures en el disc dur hi he instal·lat l'Ubuntu Studio versió per a 64 bits, que crec que aprofita millor l'arquitectura del processador que tinc (AMD Athlon(tm) 64 X2 Dual Core Processor 4200+), l'he posat en castellà, l'he deixat pelat d'efectes d'escriptori, he desactivat programes i serveis que s'executen a l'inici i que crec que no em calen per deixar-lo el més "lleuger" possible i hi he instal·lat el Cinelerra. Total, quan vull treballar amb el Cinelerra entro en aquest s.o. Dic que també em satisfà perquè la diferència en el rendiment del Cinelerra es nota molt en comparació amb quan hi treballava sota l'Ubuntu normal, i de pas faig el tafaner en les aplicacions per al tractament de sò que porta, que algunes conec (Audacity, Hydrogen) i altres són una marcianada per mi.

De totes maneres no entenc perquè el programa no fa cas en canviar la variable d'entorn Lang (em sembla que es diu així), ja que segons un manual molt currat de la mateixa versió que fai servir hauria de ser tant fàcil com fer```
export LANG es_ES
```i després ```
cinelerra
```Em fa una mica de ràbia haber de tenir l'Ubuntu Studio en castellà per aquesta aplicació, però em dono per vençut, la veritat, no tinc prou coneixements per dedicar-me a remenar, i tenia ganes de seguir editant, que hi ha molta feina!

Per cert, si a algú li interessa el manual no és dificil de trobar, però deixo aquí l'enllaç per si hi voleu donar una ullada:
 
[http://cvs.cinelerra.org/docs/cinelerra_cv_manual_es.pdf]("http://cvs.cinelerra.org/docs/cinelerra_cv_manual_es.pdf")... en pdf o
 [http://cvs.cinelerra.org/docs.php]("http://cvs.cinelerra.org/docs.php")... en altre formats i llengües.

No poso SOLVED al fil perquè realment el dubte o problema no ha quedat resolt, i si hi trobo la solució ja la passaré aquí, (i benvingudes més propostes, es clar), però de moment deixo de barallar-m'hi (m'ha guanyat, ugs!)

Salut, gràcies, i ho sento per la parrafada!:)

---

### Post by LitusMayol on 2008-08-08
**UbuntuStudio**!!!

Jo el tinc funcionant i n'estic enamorat! :) L'únic programa de so que no faig servir (a part del **Rythmbox**) és l'**Audacity**. xD El **Jack** és una passada i l'**Ardour**... pff! No me l'acabo!

Frueix l'**UbuntuStudio** perquè és magnífic!


És una pena que no ho poguem arreglar...

---

### Post by Pablitus on 2008-08-08
Ostres! Doncs ja sé a quí buscar si em llenço a usar aquestes aplicacions de sò! XD

Ahir li vai instal·lar l'UbuntuStudio al teclista de la banda i té intenció d'usarlo per afegir efectes, grabar i afegir sons al seu teclat o amb un tecladet midi, ell segur que l'aprofitarà més que jo quan tingui "la mecànica" d'aquest sistema operatiu més per la mà i es familiaritzi amb les aplicacions. Em preguntava (en Joan, el teclista) si hi havia aplicacions semblants al Finale i al Band in a Box per a Ubuntu o si podia fer anar aquestes amb Wine, i jo no en tinc ni papa. En saps algo? 
Una cosa curiosa: un programa que ell utilitza que es diu Transcribe i que és per windols li funcionava perfecte en UbuntuStudio fent doble clic a "transcribe.exe"!

Fins ara!

---


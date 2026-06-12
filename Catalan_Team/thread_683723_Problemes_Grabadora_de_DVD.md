---
title: "Problemes Grabadora de DVD"
date: 2008-01-31
forum: Catalan Team
---

### Post by Rubunter on 2008-01-31
Hola! Avui intentant grabar una imatge de CD de Kubuntu amb KDE 4.0 m'he adonat que la meva grabadora ha deixat de detectar els CD's verges. I no només això, sino que nomes llegeix els CD's i DVD's que li agraden (pocs). Quan no li ve de gust llegir los em dona el següent error en pantalla:

" No es pot muntar el volum.Opció de muntatge invàlida en intentar muntar el volum 'UDF Volume'." 

Algu te alguna suggerencia? Fins aquesta vegada havia funcionat be i, el pc te encara no 6 mesos, creieu q es un problema de la grabadora o de configuracio? Gràcies

---

### Post by pespin on 2008-01-31
```
o es pot muntar el volum.Opció de muntatge invàlida en intentar muntar el volum 'UDF Volume'.
```

Per mi que té més pinta de ser un problema de programari al intentar muntar el CD que no pas de la gravadora en si. 

Pensa que el KDE 4 encara està en fase inicial i és lògic que algunes coses encara no estiguin bé del tot.

Si tens un gnome o el kde 3 prova de gravar-ho amb algun programa que incorporin aquests, a veure que tal.

---

### Post by Rubunter on 2008-01-31
Ei! no no, si jo utilitzo el Gnome de tota la vida....(ja he vist que el meu post anterior era una mica confus) ja se que el KDE 4.0 pel moment es una mica xusco (ja veurem la 4.1, pero aixo es un altre tema), nomes era per provar. pero es q no m'ha donat ni temps, no he pogut grabar la iso en un CD pel tema de la grabadora. Mirant-m'ho be jo tb penso q es algo relacionat amb la configuració, pero encara no he trobat res satisfactori buscant al google. De fet ara que ho penso, des que vaig reinstal·lar ubuntu (fara un mes) em sembla que no havia provat de fer anar la grabadora, pero sí en la instal·lacio anterior.....no se que pot haver passat.

Una cosa que he estat mirant i q no se si hi pot tenir algo a veure es que al directori /dev no m'hi apareix cap carpeta anomenada sda0, pero si que hi ha 4 fitxers amb noms com cdrw, cdrom, dvd i dvdrw. Quan entro a les propietats d' aquests fitxers, en el destí de l'enllaç hi diu /dev/sda0, pero com he dit abans aquesta carpeta no la he vist per enlloc.

---

### Post by Rubunter on 2008-02-01
no hi ha respostes? suposo q ningu s'haura trobat amb aquesta historia....

---

### Post by Compact on 2008-02-02
Primer pots intentar de mirar si el problema és de configuració o de la grabadora. Prova amb un LiveCD a veure si et funciona.

---

### Post by Rubunter on 2008-02-02
Hola, gràcies per la teva resposta. he provat el live CD (estic escribint aixo des de dins el liveCD) i funciona perfectament. Té algun significat això? quin és el següent pas doncs?

---

### Post by Compact on 2008-02-02
Si la grabadora de DVD funciona amb el LiveCD, això vol dir que no és problema de la grabadora, sinó de la configuració del SO.

---

### Post by Rubunter on 2008-02-02
D'acord, de totes maneres ja havia dit una mica mes amunt que la grabadora em funcionava be amb alguns CD's i DVD's i amb altres no. Pensava que d'això del liveCD en podriem treure més suc jeejej. Bé doncs, ara que ja sabem la font del problema....algu te idea de com posar-hi remei?

---

### Post by mcako on 2008-02-04
Jo també vaig tenir un problema semblant amb la gravadora amb el Windows, de sobte va deixar de llegir-me DVDs i només funcionava 1 de cada 1000 vegades que intentava gravar, vaig provar de tot (actualitzar controladors i demés coses) i al final vaig decidir que la única alternativa que em quedava era comprar-me una gravadora nova, després ja va anar tot bé.

Respecte el teu problema podries especificar si només et falla amb certes marques de CD o et falla amb qualsevol, perquè si és problema de la marca dels CDs potser ho podries solucionar actualitzant el firmware de la gravadora.

Pots trobar el teu firmware a [http://www.rpc1.org/](http://www.rpc1.org/) encara que ara mateix sembla ser que no està operativa.

---

### Post by guillemsola on 2008-02-05
Si funciona des del live cd pq no proves afer un 
> cat /etc/fstab
des del terminal de la live?
hi ha una linia com
> /dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Aquesta línia potser està diferent del fitxer fstab que tens a l'ordinador.

Penso que com la live força el reconeixement de  tot el hardware de nou pots consultar coses per buscar les diferències amb el teu.

Salut!

---

### Post by Rubunter on 2008-02-06
quan faig cat /etc/fstab des del CD em surt el següent:

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

i la linia que em dius no hi apareix per enlloc, mentre que quan ho faig des de la partició si que em surt aquesta linia, un pel diferent a la teva, pero suposo q es normal degut que tenim diferents ordinadors. No se que mes fer!

---

### Post by papapep on 2008-02-06
Jo no entenc què vols dir quan dius "quan ho faig des d'el cd" o "quan ho faig des de la partició".
A més, en tots dos casos tens cd's o dvd's dins l'unitat en el moment de executar el cat?

---

### Post by guillemsola on 2008-02-06
Jo entenc que vol dir que des de la live (des de el cd) el cd no surt a fstab.

Potser que no el mostri a fstab pq no es pot desmuntar el cd del sistema executant la live?

En tot cas mostra'ns la teva línia de l'fstab on fa referència al cd pq molt diferents no han de ser.

---


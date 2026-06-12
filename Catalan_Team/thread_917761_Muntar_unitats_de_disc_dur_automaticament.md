---
title: "Muntar unitats de disc dur automaticament"
date: 2008-09-12
forum: Catalan Team
---

### Post by venusfenix on 2008-09-12
fa uns dies que vaig "postar" un problema i era que tinc un segond disc dur pero no sabia com formatar-lo i inclour-el en ubuntu.
gracies a papapep i al gparted, ja el tinc a punt, pero ara, el problema es que no m'he monta, i el gparted em dona error, m'he monta a la sessio que estic, i put treballar, pero al reinicia, torno a estar al mateix punt.
que tinc que fer??

gracies,

---

### Post by patrickfromspain on 2008-09-12
ho has d'afegir estaticament a l'arxiu /etc/fstab. Pot mirar per internet com fer-ho (google..) o si ens dius la particio que es del disc (/dev/sda1, /dev/sdb4, etc; ho pots mirar al gparted) i el sistema de fitxers en que esta formatejat, et sabrem orientar de com es fa.

Salut

---

### Post by Daerun on 2008-09-12
En aquest tema:

[http://ubuntuforums.org/showthread.php?t=856124&highlight=muntar+disc+dur+d%27inici&page=2](http://ubuntuforums.org/showthread.php?t=856124&highlight=muntar+disc+dur+d%27inici&page=2)

es va postejar una línea-model per al fstab perquè els discos durs es muntin d'inici.

---

### Post by lpargemi on 2008-09-12
Com diu en Patrickfromspain cal modificar el fitxer /etc/fstab. Per entrar-hi has d'obrir el terminal, i fer ```
sudo gedit /etc/fstab 
```
Aleshores has d'afegir-hi unes línies com aquestes on: /dev/sdb1 fora el nom del teu disc dins del gparted 
/media/nom_que_vulguis fora el lloc on vols que se't munti el disc. [En aquest cas el disc es diria nom_que_vulguis].
ext3 és el tipus de formatejat del disc.
La resta de paràmetres son els que tinc jo, però potser algú que en sàpiga més et pot comentar com han d'anar per aconseguir millors rendiments.

> # L'altre disc
/dev/sdb1	/media/nom_que_vulguis	ext3	defaults,dirsync	0	0

També cal crear un directori dins de /media que es digui nom_que_vulguis

Finalment ho proves fent > sudo mount -a

Si arrenca bé també t'arrencarà quan engeguis la màquina.

Per cert, el què jo no sé fer és que t'aparegui el nom_que_vulguis al Desktop... però segur que té una solució fàcil.

salut

Lluís

---

### Post by patrickfromspain on 2008-09-12
si es un sistema de fitxers ext3 o ext2, per fer a que a l'escriptori aparegui el que vulguis es fa servir el programa e2label. La forma d'utilitzar-lo es: sudo e2label /dev/dispositiu-particio nom-que-vols

salut

---

### Post by quitus on 2008-09-13
jo faig servir el disk manager, s'instal·la des de els repositoris i es en mode grafic

---


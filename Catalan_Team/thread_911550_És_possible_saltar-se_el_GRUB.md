---
title: "És possible saltar-se el GRUB?"
date: 2008-09-05
forum: Catalan Team
---

### Post by ktix007 on 2008-09-05
Hola tinc Ubuntu instal·lat en un disc dur extern però cada cop que engego l'ordinador sense el disc dur connectat em surt Error 21 al GRUB perquè no hi ha el disc dur. Com ho puc fer per iniciar Windows sense tenir el disc dur extern connectat? Gracies.

---

### Post by menut on 2008-09-06
Hauries d'esborrar o comentar (posant-hi "#" al davant de les línies) l'apartat del GRUB on hi surt l'Ubuntu.

Després, per tornar a arrancar l'Ubuntu, hauries de desfer i tornar a activar-lo.

---

### Post by papapep on 2008-09-06
Edita el fitxer /boot/grub/menu.lst i esborra de la línia de l'ubuntu les opcions "quiet" i "splash".
A més, edita la línia on posa "timeout" per a que quedi, p. ex, així, si vols que esperi 10 segons abans d'arrencar el primer sistema operatiu de la llista:

```
timeout 10
```

Amb això no "evites" el grub, sinó que el faràs servir com cal. :-)

---

### Post by patrickfromspain on 2008-09-06
gent, a veure si llegim mes enlla del titol :D

El teu problema es que tens el grub instal·lat a la particio del windows pero apunta a una particio que no esta disponible. Es un problema relativament facil de solucionar, amb alguns peros. Hi ha varies possibilitats i maneres.

Una seria esborrar el grub del disc dur de windows i instal·lar-lo al disc dur extern. El problema d'aquesta opció es que per arrancar l'ubuntu, hauries de canviar el dispositiu d'arrancada del pc, ja sigui per BIOS o fent servir el menu d'arranc que tenen algunes BIOS.

La millor opcio, però, es crear una particio nova al disc de windows i montar-la com a /boot a ubuntu. D'aquesta manera, sempre t'apareixera el grub (es pot configurar per a que no aparegui el menu i no esperi gens de temps) i mai tindras l'error 21 que esmentes. El problema es que s'ha de crear aquesta particio nova en el disc de windows, que encara que pot ser molt petita, no se si t'es possible.

Com es fa tot aixo? Diguen's primer que vols fer i despres en parlem, ja que hi ha bastanta feina a explicar totes les opcions i aixi ens estalviem el que d'entrada no t'interessa.

salut!

---

### Post by ktix007 on 2008-09-07
M'estimo més fer l'opció 1 (d'esborrar el grub del disc dur de windows i instal·lar-lo al disc dur extern)

---

### Post by ktix007 on 2008-09-08
Em pots dir com fer l'opció 1. Gracies

---

### Post by patrickfromspain on 2008-09-08
ultimament vaig de bolid, en quan tingui un ratet intento a veure si ser explicar com fer-ho

salut

---

### Post by ktix007 on 2008-09-08
Dacord, gracies.

---

### Post by ktix007 on 2008-09-20
Tens temps ara? :confused:

---

### Post by ktix007 on 2008-09-25
Bé suposu k ja no t'ne recordes... algú em pot ajudar? Gracies.

---

### Post by patrickfromspain on 2008-09-25
perdo!!!!! Ja ni hi pensava, perdo.

Anem per feina. Primer necessito saber alguna coseta. Fes en terminal:
```

sudo grub
find /boot/grub/stage1 

```

i diguem que hi posa alla. Merci

---

### Post by ktix007 on 2008-09-30
Perdó per tardar tant. Hi posa:
```
(hd1,0)

```
Gracies.

---

### Post by patrickfromspain on 2008-10-01
d'acord. A veure, abans de tot, et recomano fer copia de seguretat de les dades importants que puguis tenir.

També dir-te que es possible que el que et dic no sigui 100% correcte, ves amb cura. A

El que has de fer es el següent:

sudo grub
root (hd1,0)
setup (hd1)
quit

a partir d'aqui, prova a arrancar desde el disc USB. Hauras de fer servir el menu d'arrancada de la BIOS, o entrar a la BIOS i posar com a primer dispositiu d'arranc l'usb. Depen dels pcs, en alguns ni es pot (si te alguns anys).

En aquest punt, segurament encara tinguis el disc dur de windows amb el grub. Desconnecta el disc extern i prova a arrancar desde el disc dur de windows, a veure que pasa. Si encara et dona l'error, arranca des d'un disc d'instal·lacio de windows i selecciona reparar en quant t'ho digui. Quan hagis entrat dona-li la ordre fixmbr. Una altra opcio es crear un disc d'inici desde win xp i arrancar el pc amb ell i posar la ordre fdisk /MBR o fdisk /mbr

salut i SOBRETOT: copia de seguretat!

---


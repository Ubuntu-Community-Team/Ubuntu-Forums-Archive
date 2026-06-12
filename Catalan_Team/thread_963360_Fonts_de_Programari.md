---
title: "Fonts de Programari"
date: 2008-10-30
forum: Catalan Team
---

### Post by LitusMayol on 2008-10-30
Bones,

us adjunto una captura de les meves *Fonts de Programari*/*Programari de Tercers*. Jo no sé si es bo que els tingui tots marcats... 

El de *getdeb* el tinc perquè vaig actualitzar el **Gimp**.
El de *openoffice* el tinc perquè vaig actualitzar al **3.0**.

Però els altres no sé ben bé que són.. Algú em recomano desmarcar-ne alguns o quins no? 

Merci

---

### Post by oriolsbd on 2008-10-30
Hola, 

Els que hi posa "awn-testing" són per a les versions de Testing de l'avant windows navigator. Si utilitzes les seves versions de Testing, necessites aquesta font. Si utilitzes la versió oficial, està en els repositoris oficials d'Ubuntu, de manera que els podries treure.

Els que hi posa "WineHQ" suposo que deuen ser per tenir l'última versió disponible del Wine, en comptes de l'última versió que s'ha pujat als repositoris oficials d'Ubuntu. O sigui, amb aquests repositoris hauries de tenir una versió de Wine igual o superior a la que hi ha als repositoris oficials d'Ubuntu.

Una consideració a tenir en compte és respecte de tots aquells repositoris on hi posa "Codi font" (tant aquí com a la pestanya "Programari Ubuntu"). Aquest tipus de repositoris contenen, com indica el seu nom, el codi font dels programes dels repositoris "normals". Si no necessites visualitzar/modificar els codis font dels programes ni tens intenció de fer-ho, els pots desactivar.

La resta de repositoris no em sonen.

Salutacions,

---

### Post by indiosincracia on 2008-11-01
> Jo no sé si es bo que els tingui tots marcats...

Depèn del que vulguis fer, si estàs disposat a actualitzar la intrèpid, deixa només els oficials, desconnecta el programari de tercers, encara que com a mínim amb l'adept de kubuntu ja t'ho fa automàticament, deu ser igual amb ubuntu.

---

### Post by Aljullu on 2008-11-02
La font de programari del Dropbox ([www.getdropbox.net](www.getdropbox.net), o quelcom així) m'imagino que és per actualitzar aquell programa.

---

### Post by open-pitu on 2008-11-03
Les fonts de programari són els repositoris d'on baixarem les actualitzacions del sistema o porgrames i/o instal·larem nou software.
Per veure les fonts que disposem:
[INDENT]$sudo gedit /etc/apt/sources.list[/INDENT]

Les línies que comencen amb "#" són comentaris del fitxer. Si afegiu algun repositori heu d'executar:
[INDENT]$sudo apt-get update
$sudo apt-get upgrade[/INDENT]

---


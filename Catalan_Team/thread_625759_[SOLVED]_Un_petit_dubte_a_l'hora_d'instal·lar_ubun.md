---
title: "[SOLVED] Un petit dubte a l'hora d'instal·lar ubuntu."
date: 2007-11-28
forum: Catalan Team
---

### Post by lo gambusí on 2007-11-28
He d'instal·lar ubuntu a una companya que va amb windows vista, i a l'hora de fer-ho mos ha sortit un dubte. Ella té arxius i carpetes que li interessaria conservar a la sessió del windows. A l'hora d'instal·lar l'Ubuntu i fer una partició (una de windows i l'altra de linux) li conservarà los arxius que té actualment al windows o haurem d'instal·lar-ho de nou? Tinc entès que per defecte ho elimina, però m'agradaria saber si hi ha alguna manera de guardar-ho. Si no és així, farem còpia de seguretat en un DVD i avant.

Moltes gràcies!!:lolflag:

---

### Post by ernestux on 2007-11-28
[ li conservarà los arxius que té actualment al windows o haurem d'instal·lar-ho de nou? Tinc entès que per defecte ho elimina, però m'agradaria saber si hi ha alguna manera de guardar-ho. Si no és així, farem còpia de seguretat en un DVD i avant.]

Hola gambusí,

Durant la instal·lació hi ha un moment -no recordo si abans o després de particionar- que pregunta si de la partició windows (jo tenia xp) vols guardar o importar alguna carpeta de "Documents and Setings" cap a la home que es crearà en la instal·lació.

Tot i això , millor fer una còpia de seguretat abans en un disc extraible.

Ernest

---

### Post by papapep on 2007-11-28
Lo Gambusí, fer es pot fer qualsevol cosa: 

 - Redimensionar la partició windows i muntar un sistema de doble arrancada windows/Linux.
 - Marxacar la partició windows i copiar els fitxers a un suport (CD/DVD) i posar-los posteriorment al nou /home.

La qüestió rau en si a la teva amiga li cal o no executar el windows,
però el particionador et permet fer de tot  ;-)

És important, si s'ha de redimensionar la partició windows, passar-li un parell de cops el checkdisk (o com coi es digui) a fi de que no tingui desfragmentació ni errors el sistema de fitxers NTFS (o FAT), ja que si no, el particionador de Linux no voldrà fer la feina.

---

### Post by RainCT on 2007-11-28
> **lo gambusí said:**
> A l'hora d'instal·lar l'Ubuntu i fer una partició (una de windows i l'altra de linux) li conservarà los arxius que té actualment al windows o haurem d'instal·lar-ho de nou?

Com ja ha dit en papapep, hi ha l'opció de redimensionar i crear una partició per a l'Ubuntu, i aquesta deixarà totes les dades intactes.


> **lo gambusí said:**
> Tinc entès que per defecte ho elimina, però m'agradaria saber si hi ha alguna manera de guardar-ho. Si no és així, farem còpia de seguretat en un DVD i avant.

Si ho recordo bé la opció per defecte és precisament la que vols (la d'esborrar era la predefinida abans, però diria que ho van canviar perquè hi va haver queixes al respecte), però no n'estic segur; llegeix-te bé el que et digui quan arribis a la part del particionat. En quant a les còpies de seguretat, sempre és una bona idea tenir-ne.

---

### Post by lo gambusí on 2007-11-29
Moltes gràcies a tots!!

La cosa està en que vaig instal·lar-me l'Ubuntu fa temps i sense fer particions, i no me'n recordava. Necessita lo windows per uns programes de sociologia, no sé  quins.

Moltes gràcies a tots, una vegada més. ;)

---

### Post by orestesmas on 2007-11-29
Si només és per uns programes concrets "de feina" i no pas per jocs ni cap altra cosa que requereixi acceleració 3D, jo recomanaria seriosament instal·lar windows en una màquina virtual, i no com a arrancada dual.

---

### Post by lo gambusí on 2007-11-29
D'acord,  ho estudiarem. Gràcies. : )

---


---
title: "[SOLVED] Wine i el CDRom"
date: 2008-01-18
forum: Catalan Team
---

### Post by kukat on 2008-01-18
Un petit problema: Quan començo una instal.lació amb Wine (concretament del primer Call of Duty, original) quan hem demana que fique el segon cd, no hi ha manera. 

He probat desmuntant l'unitat a la força (sudo umount -l /dev/scd0) I també he probat un comandament que he trobat per la xarxa ( sudo sysctl dev.cdrom.lock=0) però cap dels dos hem soluciona el problema. 
Al insertar el 2on cd, quan torno a montar-lo, hem torna a montar el primer cd!!! I aixó que no hi es... I amb el comandament del "lock=0" (quan torne a montar-lo) hem tira error, per què tampoc s'ha montat bé.

Alguna suggerència? 

Gràcies

---

### Post by RainCT on 2008-01-18
Pot ser t'ajudaran els comentaris que hi ha a la [base de dades d'aplicacions amb Wine](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1812)...

---

### Post by kukat on 2008-01-18
Gràcies!! He vist a la web on m'has dit que copiant els .pk del segon disc el joc ja funciona... Vaig a probar-ho.

---

### Post by kukat on 2008-01-19
Val, oblideu lo dels arxius .pk. Es més senzill encara. Quan vos demane un cd en la instal.lació i no pugueu traure'l, es tan fàcil com posar a una consola:

**wine eject** + unitat que voleu traure (**d: e:** el que sigui)

---


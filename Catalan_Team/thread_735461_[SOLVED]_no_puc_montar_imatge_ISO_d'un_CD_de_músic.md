---
title: "[SOLVED] no puc montar imatge ISO d'un CD de música"
date: 2008-03-25
forum: Catalan Team
---

### Post by carlesdalmases on 2008-03-25
Hola,

he creat una imatge ISO d'un cd de música des de l'escriptori d'UBUNTU amb: botó dret a sobre el CD (disc d'audio) --> copia el disc --> copia el disc a fitxer d'imatge.

Aquest mètode genera un fitxer ISO i un fitxer ISO.TOC de text pla amb el contingut del CD.

El que vull fer ara és "montar" la imatge ISO per extreure'n les cançons, però no hi ha manera.

Ho he intentat amb GMOUNT-ISO i també des de línia de comanda amb:

sudo mount -t iso9660 -o loop fitxer.iso /mnt/iso 

aquesta última comanda dóna l'error:
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       En alguns casos, es pot trobar informació útil a syslog,
        proveu dmesg | tail o així

i el resultat del dmesg | tail 
[ 2822.864000] Unable to identify CD-ROM format.

He estat buscat pel Google per no he estat capaç de trobar cap fil. Sospito que els CDs de música no es monten igual que els CD de dades o DVDs.

Alguna idea de com puc llegir aquests fitxers ISO (els CD originals ara no els tinc disponibles !)


Nota: també he intentat generar el fitxer ISO amb la comanda dd, però sóc incapaç de descobrir a dins de /dev on es troba el cd de música (cosa que confirma la meva teoria de què els cd de música no es monten "normals" :-)

Gràcies.

---

### Post by menut on 2008-03-25
Prova amb gIsomount:
Instal·la'l:
```
sudo apt-get install gisomount
```
Inicia'l:
```
gksu gisomount
```

Si no te'n surtes, prova a convertir la imatge a un altre tipus d'extensió...:-?

---

### Post by patrickfromspain on 2008-03-25
mm jo tenia entes de que no es pot fer una imatge ISO d'un cd de musica.

salut

---

### Post by menut on 2008-03-25
Això és l'estrany, ja que li permet crear-la.

Carlesdalmases, el tamany de la ISO et coincidia amb el del CD ?

---

### Post by patrickfromspain on 2008-03-25
de totes formes.. perque crear una imatge Iso si pots extreure'n el contingut? Amb el Grip per exemple.

salut

---

### Post by menut on 2008-03-26
> **patrickfromspain said:**
> perque crear una imatge Iso si pots extreure'n el contingut?
Imagina't que has de fer 500 còpies d'un Cd de música. No és més fàcil  grabar la imatge que haver de copiar fitxer a fitxer ?

---

### Post by carlesdalmases on 2008-03-26
Patrickfromspain, vaig crear una imatge ISO perquè no tenia accés a Internet i hem va fer molta mandra picar els noms de les cançons. Vaig pensar que si feia una ISO, més tard quan tingués connexió no caldria fer res. També és cert que vaig llegir en un post de l'any 2005 que això no es podia fer, però vaig pensar que ja s'hauria solucionat.

Menut, ja també penso que és molt estrany que et permeti crear una ISO i després no hi pugui accedir. També he provat d'obrir-la amb K3B i tampoc funciona. De totes maneres provaré amb el programa que dius i amb l'AcetoneISO.

Potser és un tema del format ISO. Algú sap si hi ha altres estàndards a part del ISO9660?

---

### Post by menut on 2008-03-26
Per a fitxers amb extensió .iso, l'estàndard que utilitzes és el correcte.

[http://es.wikipedia.org/wiki/ISO_9660]("http://es.wikipedia.org/wiki/ISO_9660")

[Pàgina oficial de l'estàndard]("http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=17505")

---

### Post by carlesdalmases on 2008-03-28
Hola,

he estat fent algunes proves més, he arribat a les següents conclusions:

* el manual d'ajuda del programa ACETONEISO2, diu

[I]"Generate ISO from CD/DVD feature:

- insert a CD/DVD.
- choose where to save the ISO image

note: it will only work with normal data CD/DVD.
         it won't work with copyprotected cds and audio cd (look under for generating an image of audio cd)"
[/I]

Anem malament ! Si mirem l'apartat de generar una imatge d'un CD d'audio:

[I]Backup Audio CD:

- insert the audio cd
- it will generate a bin/toc image

note: the image is not readable in any way, you can however burn it later with cdrdao command
[/I]

Aquest darrer punt hem va donar una mica d'esperança. Potser canviant l'extensió del fitxer ISO que havia creat el mateix ubuntu per BIN (el TOC ja el tenia creat) funcionaria. Doncs tampoc! No deixa ni gravar en un CD verge.

Resultat: L'ubuntu crea una imatge ISO (sic!) d'un cd d'audio que no serveix per a res. No es pot montar ni gravar-la en un cd verge.
Mala sort. La propera vegada no tindré mandra i escriuré els títols de les cançons :-(

Potser els que teniu més experiència comunicant coses a l'equip de desenvolupadors d'Ubuntu els hi podeu fer notar aquesta "disfunció" (si és que finalment tinc raó)

Dono el fil per tancat (si no és que algú altra s'ha il·luminat i troba la manera).


Gràcies per tot.

---

### Post by menut on 2008-03-28
Fes clic a Thread Tools>Mark this thread as SOLVED, per a marcar aquest fil com a resolt o acabat.

---


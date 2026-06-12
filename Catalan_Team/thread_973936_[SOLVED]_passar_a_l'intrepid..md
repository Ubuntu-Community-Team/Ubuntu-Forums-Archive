---
title: "[SOLVED] passar a l'intrepid?."
date: 2008-11-07
forum: Catalan Team
---

### Post by muleta on 2008-11-07
A mi no se'm permet actualitzar però no sé si és bona idea perque veig que tothom té molts problemes amb l'Intrepid. Hauré de llegir tots els vostres posts per veure si són resolubles o no i, per si em decideixo, què puc fer?. Em surt això, quan ho intento:

"W:No s'ha pogut obtenir cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot usar-se apt-get update per afegir-ne de nousW:No s'ha pogut obtenir cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot usar-se apt-get update per afegir-ne de nous
, W:No s'ha pogut obtenir cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot usar-se apt-get update per afegir-ne de nous
, E:No es poden descarregar alguns fitxers índex, s'han ignorat o en el seu lloc s'han usat els antics.
, W:No s'ha pogut obtenir cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot usar-se apt-get update per afegir-ne de nous
, E:No es poden descarregar alguns fitxers índex, s'han ignorat o en el seu lloc s'han usat els antics."

---

### Post by torracastanyes on 2008-11-07
Si he entès bé el missatge que enganxes, diu que tens comfigurat el synaptic perquè actualitzi només des del CD de Gutsy.
Hauríes d'anar a sistema=>administració=>synaptic=>parametres=>dipòsits
i veure si tens marcades les caselles del camp "descarregable d'internet"
i desmarcar la de "instalable des de CD-ROM".

---

### Post by SiscoGarcia on 2008-11-07
Per què no ens enganxes els teus fitxers "/etc/apt/sources.list" i "/boot/grub/menu.lst" (tot sense cometes, és clar) a veure què hi tens?

---

### Post by muleta on 2008-11-07
He mirt això que em déia Torracastanyes i sembla que era el que li passava. He desactivat totes les opcions però no he vist la de descarregar des d'Internet.
 
He pogut actualitzar però, en reiniciar, no fa res. Després d'introduir-li l'usuari i contrassenya, es queda la pantalla de color beix clar com si volgués iniciar Ubuntu, però no es mou d'aquí i no s'inicia.

---

### Post by SiscoGarcia on 2008-11-07
Quines són les opcions d'arrencada que tens? Per què no proves a entra a mode d'errades?

Ens cal més informació per poder-te ajudar.

---

### Post by muleta on 2008-11-07
Ja està, crec que ara ja funcionará. He entrat a opcions d'inici i he posat Gnome com a predeterminada. Hi tenía "Executa l'script Xclient", que es deu posar per defecte.

Gràcies a tots dos.

---

### Post by SiscoGarcia on 2008-11-08
> **muleta said:**
> Ja està, crec que ara ja funcionará. He entrat a opcions d'inici i he posat Gnome com a predeterminada. Hi tenía "Executa l'script Xclient", que es deu posar per defecte.

Sisplau, explica'ns com t'ha anat quan ho hagis provat, val? I quan et funcioni marques el fil com a resolt ;)

---

### Post by muleta on 2008-11-08
Comprovat i va bé. Gràcies.

---

### Post by SiscoGarcia on 2008-11-08
Me n'alegro que et funcioni, de debò. Però ens deus una explicació que pugui servir per ajudar qui vingui al darrere. És lògic, i a més ho pots veure al "[fil d'iniciació]("http://ubuntuforums.org/showthread.php?t=599965")":
```

12.- Acabeu amb una nota sobre la solució

Com a conseqüència directa dels punts anteriors, és important acabar el fil explicant, si no s'ha fet abans, com s'ha arribat a la solució del problema. De pas, aprofiteu per marcar el fil com a resolt [SOLVED].

Això ho podreu fer un cop us identifiqueu amb el vostre usuari i contrassenya i anant al damunt del fil, fent clic a "Thread tools" i marcant l'opció "Mark this thread as solved". Tingueu present que això només ho podrà fer qui ha creat el fil o un dels moderadors del fòrum.
```

---

### Post by RainCT on 2008-11-09
Ja ha explicat quin era el problema.

> **muleta said:**
> He entrat a opcions d'inici i he posat Gnome com a predeterminada. Hi tenía "Executa l'script Xclient", que es deu posar per defecte.

---

### Post by SiscoGarcia on 2008-11-09
Ups, tens raó, m'ha confós el fet que ella dubtés.
> **muleta said:**
> Ja està, crec que ara ja funcionará. 

Perdó muleta :redface:

---


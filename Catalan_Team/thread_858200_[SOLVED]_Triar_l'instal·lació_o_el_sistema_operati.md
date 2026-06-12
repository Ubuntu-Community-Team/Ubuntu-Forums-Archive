---
title: "[SOLVED] Triar l'instal·lació o el sistema operatiu"
date: 2008-07-13
forum: Catalan Team
---

### Post by Brunilda on 2008-07-13
Com bon "dumingueru" he començat el dia fent bricolatge...

Ja fa dies que volia provar la versió 8.04, que no m'atrevia instal·lar sense provar-la. Doncs bé aprofitant el diumenge he decidit instal·lar-la en una partició de 20 G que tinc especialment creada per aquestes coses.

Quant he acabat he re-iniciat l'ordinador i he vist, amb sorpresa, que el grub només em donava l'opció de carregar la versió 8.04 i no 7.10 que és la que vull seguir fent servir i he deduït que segurament no he fet bé alguna cosa.

Us deixo una imatge de les particions...

---

### Post by orestesmas on 2008-07-13
La imatge està molt bé, però si no ens expliques una mica què hi tens a cadascuna de les particions, costa una mica fer-se'n a la idea i suggerir modificacions al GRUB.

---

### Post by Brunilda on 2008-07-13
Amb una bona dosi de fòrums i un retalla per aquí enganxa per allà he pogut arreglar el tema.

Per començar he descobert, a la guia de l'ubuntu en [castellà,]("http://www.guia-ubuntu.org/index.php?title=Portada") el [super grub disk]("http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2"), que m'ha permès tornar a iniciar la instal·lació de la gutsy 7.10.

A partir d'aquí i seguint (més o menys) alguns dels posts d'aquest fòrum he fet un "retalla/enganxa?" de les opcions menu.lst de la nova instal·lació hardy 8.04 en el menu.lst de la instal·lació 7.10... i sembla que funciona.

Perdoneu la gent sensible d'aquest fòrum si trobeu que no parlo gaire en propietat però del tema d'ordinadors el que faig millor és fer-los malbé...

Per cert, voldria marcar-lo com a "SOLVED" com vaig fer amb algun altre tema però no soc capaç de trobar com es fa.

---

### Post by papapep on 2008-07-13
> Perdoneu la gent sensible d'aquest fòrum si trobeu que no parlo gaire en propietat però del tema d'ordinadors el que faig millor és fer-los malbé...

Aquí no es tracta de sensibilitat, no serveix massa això pel Gnu/Linux. Es tracta de que si no s'entèn bé el teu problema i la teva situació és molt complicat ajudar-te. Símplement.

Per marcar com a resolt has d'anar al menu "Thread tools", damunt del fil.

---


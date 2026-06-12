---
title: "Internet no va"
date: 2008-11-18
forum: Catalan Team
---

### Post by dorcap on 2008-11-18
Internet no em va en un dels dos ordinadors (intrepid ibex), connectats a internet per un commutador que comparteixen.
En resposta a la comanda: dmesg | grep eth0 tinc tres línies: La primera em dóna informació de la tarja ethernet, i el codi MAC.
La segona em diu link down i ls tecera link is not ready.
Això em passa després d'haver configurat internet en el segón ordinador després d'imstal·lar-hi Windows.
Espero saber com reaparar aquest link trencat.
Gràcies.
Francesc

---

### Post by papapep on 2008-11-19
Hola Francesc,

El que ens faria falta és veure el que et diu un "ifconfig", i un "lspci", per tenir clar quina placa tens, i quina configuració tens ara.
Tot i això t'haig de dir que, per no perdre el costum, el nou, flamant i "refurbished" network-manager de la 8.10 hi ha màquines en la que també m'ha portat problemes a mi, i he hagut de configurar la xarxa "a manilla", instal·lar el [wicd]("http://wicd.sourceforge.net/download.php") i eliminar el network-manager. D'aquí en endavant, oli en un llum....

---

### Post by dorcap on 2008-11-19
Bon dia, Papapep i gràcies: Inexplicablement, allò que semblava que era una fallada permanent, s'ha arranjat.
Ara, consultant amb la mateixa comanda la informació d'eth0 em diu link up i la cosa funciona. Encara que m'agraria saber el perquè, em sembla que l'explicació quedarà, com tantes vegades passa, en el garbuix dels misteris no resolts que té la vida.
Repeteix, Moltes gràcies també pels links.
Salutacions,
Francesc

---


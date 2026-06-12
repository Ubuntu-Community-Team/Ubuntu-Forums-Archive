---
title: "gvfs i samba"
date: 2008-05-06
forum: Catalan Team
---

### Post by CarlesOriol on 2008-05-06
Compte.

En aquesta versió d'ubuntu l'accés a recursos de xarxa a servidors windows en domini fent smb://nomordinador no va.

Això amb el gnome-vfs no passava. 

Si algú llegeix cap so&#320;lució per la xarxa em faria un bon favor ja que al launchpad la cosa veig que va per llarg.

---

### Post by SiscoGarcia on 2008-05-06
Hola Carles,

Això mateix que dius m'ha passat a mi també, el que passa és que hi ha hagut vegades que he aconseguit fer la connexió a un recurs compartit de Windows. De fet des de l'ordinador on estic escrivint tinc un accés a una unitat compartida d'un altre ordinador; la diferència que he observat respecte a la versió anterior és que en Hardy cada cop que accedeixes a un recurs compartit el munta, mentre que Gutsy el tenia muntat (o almenys ho feia veure).Adjunto les captures corresponents a aquesta unitat, on pots veure com la tinc, que no és diferent de com tu proposes. Però sento no servir-te de més ajuda.

---

### Post by CarlesOriol on 2008-05-07
> **SiscoGarcia said:**
> ... hi ha hagut vegades que he aconseguit fer la connexió a un recurs compartit de Windows. ...

No, llavors no és el mateix.

Per que alguns que el seu nom comença per O i el seu cognom és un signe aritmètic en castellà diré que amb el konqueror va de perles. 

Llàstima el kde4 encara no funcioni bé per que si no ara em migrava.

---

### Post by SiscoGarcia on 2008-05-21
Carles, no sé si és el mateix que tu vols o què però he trobat que per accedir a un recurs compartit de windows en xarxa me n'estic sortint creant una llançadora de tipus ubicació. Llavors li dones el nom que vols i la ubicació amb samba: "smb://nomdelordinador", evidentment sense cometes. L'única pega és que triga a obrir-lo i pot ser et demana nom d'usuari i contrasenya; funciona posant-li les de l'ordinador des d'on ets.

Espero que et serveixi, o a d'altres.

---

### Post by uidb4056 on 2008-05-21
Carles, no sé si et servirá pero jo tinc muntat un recurs compartit posant aixó al fstab amb 8.04 64 bits

//TAURO64/Musica_Robert /media/XPMusica smbfs guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---


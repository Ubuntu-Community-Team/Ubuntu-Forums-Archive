---
title: "Contalinex:  Locales not supported on X server"
date: 2008-03-14
forum: Catalan Team
---

### Post by sianeu on 2008-03-14
He instal·lat el contalinex i al engegar-lo, al primer pas de configuració s'ha quedat penjat amb aquest missatge (el he engegat per consola) "Qt: Locales not supported on X server". Ara no el puc ni tancar.

No se si pot ser problema d'idioma, potser hauria d'haver instal·lat el castellà ???

Salut

---

### Post by CarlesOriol on 2008-03-14
Aquest programari ja està una mica passat. no? A més està fet en un pascal de la Borland que ja no existeix. I malgrat s'ofereix amb llicència gpl no ho pot ser degut a que els components que requereix no ho son i per tant no pots realitzar una versió moderna ja que les seves parts ja estan caduques en els sistemes actuals.

Jo et recomanaria usar l'abanq

---

### Post by mbtiago on 2009-03-26
> **sianeu said:**
> He instal·lat el contalinex i al engegar-lo, al primer pas de configuració s'ha quedat penjat amb aquest missatge (el he engegat per consola) "Qt: Locales not supported on X server". Ara no el puc ni tancar.

No se si pot ser problema d'idioma, potser hauria d'haver instal·lat el castellà ???

Salut
Hola Sianeu

Igualment tinc problemes amb aquests packages, que no puc ni re-instalar ni desinstalar. Tampoc trobo repositoris que em serveixin, tinc Ubuntu 8.10 Intrepid amd64 i els que he trobat son per i386 ou altres distros.

Per si em pots donar un cop de mà, t'envio a sota el que vaig probar.

Gràcies,
Manuel

manuel@manuel-laptop2:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package facturlinex needs to be reinstalled, but I can't find an archive for it.

manuel@manuel-laptop2:~$ sudo dpkg -r facturlinex
facturlinex   facturlinex2  

manuel@manuel-laptop2:~$ sudo dpkg -r facturlinex2
(Reading database ... 158828 files and directories currently installed.)
Removing facturlinex2 ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex2.postrm: line 42: /etc/init.d/mysql: Permission denied
dpkg: error processing facturlinex2 (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 facturlinex2

manuel@manuel-laptop2:~$ sudo dpkg -r --force-all facturlinex2
(Reading database ... 158756 files and directories currently installed.)
Removing facturlinex2 ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex2.postrm: line 42: /etc/init.d/mysql: Permission denied
dpkg: error processing facturlinex2 (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 facturlinex2

manuel@manuel-laptop2:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package facturlinex needs to be reinstalled, but I can't find an archive for it.

manuel@manuel-laptop2:~$ sudo dpkg -r --force-all facturlinex
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 158756 files and directories currently installed.)
Removing facturlinex ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex.postrm: line 41: /etc/init.d/mysql: Permission denied
dpkg: error processing facturlinex (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 facturlinex
manuel@manuel-laptop2:~$ 

En aptitude tengo (i have)
H	contalinex		1.2.0
Hd 	facturlinex   		1.6.2
Bd	facturlinex2  -13.4MB	2.0.0
H 	nominalinex		1.0.0




tengo contalinex 1.2, facturlinex 1.6.2, nomin 1.0 - remove facturlinex2

---

### Post by sianeu on 2009-03-26
Prova amb el que deia en Pespin a l'altre fil:

$ sudo chmod 777 /etc/init.d/mysql
$ sudo aptitude purge facturlinex

Al Rajoar li va funcionar, i tu també tens aquesta linea 

> /var/lib/dpkg/info/facturlinex2.postrm: line 42: /etc/init.d/mysql: Permission denied

Salut

---

### Post by mbtiago on 2009-03-26
Gràcies per la teva resposta. Acabo de provar-lo i no em funciona. Haig de seguir buscant-lo...

---

### Post by marteljorge on 2009-03-29
> **sianeu said:**
> Prova amb el que deia en Pespin a l'altre fil:

$ sudo chmod 777 /etc/init.d/mysql
$ sudo aptitude purge facturlinex

Al Rajoar li va funcionar, i tu també tens aquesta linea 



Salut
sudo mkdir /etc/init.d/mysql
sudo rm -rf /etc/init.d/mysql
sudo touch /etc/init.d/mysql
sudo chmod 777 /etc/init.d/mysql
$ sudo aptitude purge facturlinex
i tot a tornat a la normalitat...
(de vegades el bosc no ens deixa veure els arbres!...)
Moltes gràcies a tots!

---


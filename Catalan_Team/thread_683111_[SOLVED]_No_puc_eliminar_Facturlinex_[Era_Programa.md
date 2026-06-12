---
title: "[SOLVED] No puc eliminar Facturlinex [Era: Programa que no puc eliminar!]"
date: 2008-01-30
forum: Catalan Team
---

### Post by rajoar on 2008-01-30
Vaig trobar el programa de facturació Facturlinex i vaig voler probar-lo. Em va trencar paquets al instal·lar-lo i no hi ha manera de desinstal·lar-lo...
Provi el que provi, sempre em dona el mateix missatge, per exemple:

sudo apt-get --purge remove facturlinex
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'ELIMINARAN els següents paquets:
  facturlinex
0 actualitzats, 0 nous a instal·lar, 1 a eliminar i 0 no actualitzats.
1 no instal·lats o eliminats completament.
Es necessita obtenir 0B d'arxius.
Després de desempaquetar s'alliberaran 19,2MB d'espai en disc.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 117456 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant facturlinex ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex.postrm: line 41: /etc/init.d/mysql: No such file or directory
dpkg: s'ha produït un error en processar facturlinex (--remove):
 el subprocés post-removal script retornà el codi d'eixida d'error 127
S'han trobat errors en processar:
 facturlinex
E: Sub-process /usr/bin/dpkg returned an error code (1)

Que puc fer per eliminarlo del tot?...

---

### Post by papapep on 2008-01-30
Podriem començar amb un:

```
sudo apt-get install -f 
```

a veure si et resol el tema.

Després intentes el:

```
sudo aptitude purge nom_del_paquet
```

---

### Post by rajoar on 2008-01-30
Doncs no papapep,
Sempre em contesta el mateix:
ramon@JOU-TORRAS:~$ sudo apt-get install -f
[sudo] password for ramon:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'ELIMINARAN els següents paquets:
  facturlinex
0 actualitzats, 0 nous a instal·lar, 1 a eliminar i 0 no actualitzats.
1 no instal·lats o eliminats completament.
Es necessita obtenir 0B d'arxius.
Després de desempaquetar s'alliberaran 19,2MB d'espai en disc.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 117456 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant facturlinex ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex.postrm: line 41: /etc/init.d/mysql: No such file or directory
dpkg: s'ha produït un error en processar facturlinex (--remove):
 el subprocés post-removal script retornà el codi d'eixida d'error 127
S'han trobat errors en processar:
 facturlinex
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by papapep on 2008-01-30
Bé, ja em semblava que no seria tan fàcil....:-D

Comencem. Crearem "a manilla" el directori que busca i no troba:

> /var/lib/dpkg/info/facturlinex.postrm: line 41: /etc/init.d/mysql: No such file or directory

```
sudo mkdir /etc/init.d/mysql
```

Després fes un:

```
sudo aptitude update
```

A veure si és capaç de refer la base de dades de paquets.

---

### Post by rajoar on 2008-01-30
Bé..., continuem sense poder eliminar-lo...

---

### Post by patrickfromspain on 2008-01-30
i probant amb sudo dpkg --purge --force-all facturlinex?

EDITO: NO se si es segur

---

### Post by rajoar on 2008-01-30
ramon@JOU-TORRAS:~$ sudo dpkg --purge --force-all facturlinex
(S'està llegint la base de dades ... hi ha 117456 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant facturlinex ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex.postrm: line 41: /etc/init.d/mysql: is a directory
dpkg: s'ha produït un error en processar facturlinex (--purge):
 el subprocés post-removal script retornà el codi d'eixida d'error 126
S'han trobat errors en processar:
 facturlinex
ramon@JOU-TORRAS:~$

---

### Post by patrickfromspain on 2008-01-30
proba a fer:

sudo rm -rf /etc/init.d/mysql
sudo touch /etc/init.d/mysql

---

### Post by rajoar on 2008-01-30
ramon@JOU-TORRAS:~$ sudo touch /etc/init.d/mysql
ramon@JOU-TORRAS:~$ sudo dpkg --purge --force-all facturlinex
(S'està llegint la base de dades ... hi ha 117456 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant facturlinex ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex.postrm: line 41: /etc/init.d/mysql: is a directory
dpkg: s'ha produït un error en processar facturlinex (--purge):
 el subprocés post-removal script retornà el codi d'eixida d'error 126
S'han trobat errors en processar:
 facturlinex
ramon@JOU-TORRAS:~$

---

### Post by patrickfromspain on 2008-01-30
he editat el meu post, perdo. Proba! ;) xD

---

### Post by papapep on 2008-01-30
Doncs baixes els paquets de mysql-server, l'instal·les i després t'ho carregues tot plegat.

---

### Post by rajoar on 2008-01-30
ramon@JOU-TORRAS:~$ sudo rm -rf /etc/init.d/mysql
ramon@JOU-TORRAS:~$ sudo touch /etc/init.d/mysql
ramon@JOU-TORRAS:~$ sudo dpkg --purge --force-all facturlinex
(S'està llegint la base de dades ... hi ha 117456 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant facturlinex ...
Haciendo una copia de su BBDD en /root...
/var/lib/dpkg/info/facturlinex.postrm: line 41: /etc/init.d/mysql: Permission denied
dpkg: s'ha produït un error en processar facturlinex (--purge):
 el subprocés post-removal script retornà el codi d'eixida d'error 126
S'han trobat errors en processar:
 facturlinex
ramon@JOU-TORRAS:~$

---

### Post by rajoar on 2008-01-30
*Doncs baixes els paquets de mysql-server, l'instal·les i després t'ho carregues tot plegat.*

papapep,
No entenc que és el que haig de fer...¿...?

---

### Post by ilku on 2008-01-31
Hola company:
Crec que el papapep vol dir que facis un sudo apt-get install mysql-server. I un cop insta.lat facis el purge dels altres facturlinex i despres et carreguis el mysql. per deixar-ho net.

---

### Post by papapep on 2008-01-31
No podrà. Ha de descarregar els paquets via [http://packages.ubuntu.com](http://packages.ubuntu.com), instal·lar-los i després si, fer el que tu has comentat.

---

### Post by CarlesOriol on 2008-01-31
Rajoar... passa un moment pel fil de benvinguda i presenta't que tinc una explicació de què pots fer però com que no veig si ets gaire nou si ho poso a sac et pot sonar a xines.

---

### Post by pespin on 2008-01-31
> /etc/init.d/mysql: Permission denied

Si canvies els permisos del arxiu jo diria que se solucionarà tot.

Jo provaria:
$ sudo chmod 777 /etc/init.d/mysql

i tornaria a provar de desinstal·lar amb el aptitude :)

---

### Post by rajoar on 2008-01-31
Efectivament Pespin:
$ sudo chmod 777 /etc/init.d/mysql
$ sudo aptitude purge facturlinex
i tot a tornat a la normalitat...
(de vegades el bosc no ens deixa veure els arbres!...)
Moltes gràcies a tots!

---

### Post by mbtiago on 2009-03-26
Hola tothom

Estic amb el mateix problema. A la cap i a la fi com s'ha de fer per remoure aquest facturlinex? cal afegir algun directori (que no en trobo) a les sources?

Per si em podeu ajudar, us indico les sources que tinc (però que no hem serveixen) i els meus intents. Tinc Unbuntu 8.10/Intrepid amd64.

Gràcies

---


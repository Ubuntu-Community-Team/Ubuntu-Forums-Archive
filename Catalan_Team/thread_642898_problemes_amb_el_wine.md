---
title: "problemes amb el wine"
date: 2007-12-17
forum: Catalan Team
---

### Post by hakd0c on 2007-12-17
Tinc la gutsy instal·lada i tinc problemes amb el wine (hostres aquesta frase m'ha recordat els grups d'autoajuda :-p)

si executo el wine em dona el següent error.

wine: error while loading shared libraries: /usr/bin/../lib/libpthread.so.0: invalid ELF header

---

### Post by papapep on 2007-12-17
Has instal·lat el paquet dels repositoris, o has compilat desde el codi font? Sembla que no sap trobar una de les llibreries que fa servir...
Igual un:

```
dpkg-reconfigure wine 
```

t'ho arregla.

---

### Post by hakd0c on 2007-12-18
Hola,

Fins ara havia afegit al meu llistat de repositoris, els repositoris d'ubuntu que aporta wine.

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

Al preguntar-me des d'on ho havia instal·lat he caigut en la compte de que no provenia dels repositoris oficials per tant l'hi he dit que mel desinstal·li completament (a traves d'entorn gràfic), també he buidat la cache de deb que es guarda en local.

Un cop fet això he eliminat de la llista de repositoris els del wine, he actualitzat la llista de repositoris i he demanat que em em torni a instal·lar el wine.
Però em continua donant el mateix error

No tinc cap directori al meu home que es digui .wine.

Si ho executo amb un sudo l'error es el mateix

El dpkg-reconfigure també l'he fet un parell de vegades.

acabo de fer un sudo find / -iname '*libpthread*' i entre altres em surten els següents

/lib/libpthread.so.0
/lib/libpthread-2.6.1.so
/usr/lib/libpthread.so.0
/usr/lib/libpthread.a
/usr/lib/libpthread.so

---

### Post by papapep on 2007-12-18
Prova a afegir el camí de les llibreries al fitxer **/etc/ld.so.conf**

Després executa:

```
sudo ldconfig
```

Si et segueix fallant, fes:

```
ldd /cami_al_executable/wine 
```

---

### Post by hakd0c on 2007-12-18
edito el /etc/ld.so.conf i afegeixo aquestes dues linias.

```

include /lib/libpthread.so.0
include /usr/lib/libpthread.so.0

```

executo el sudo ldconfig

```

david@david-desktop:~$ sudo ldconfig
/sbin/ldconfig.real: L is not a known library type
david@david-desktop:~$ 

```

dona error i provo el pas d'emergència :-p

```

david@david-desktop:~$ ldd /usr/bin/wine
/usr/bin/wine: error while loading shared libraries: /usr/bin/../lib/libpthread.so.0: invalid ELF header
david@david-desktop:~$ 


```

O sigui que continuo allà on estava

---

### Post by papapep on 2007-12-18
L'últim no era un pas d'emergència, era per saber quines llibreries dinàmiques demana el wine :-)

Sembla que tens un error al ld.so.conf. Fes:

```
cat /etc/ld.so.conf
```

i enganxa el resultat.

---

### Post by hakd0c on 2007-12-19
Després d'escriure el missatge he anat a buscar què feia la comanda i ja m'he adonat que no era la d'emergència :-p

```

david@david-desktop:~$ cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf
include /lib/libpthread.so.0
include /usr/lib/libpthread.so.0

david@david-desktop:~$ cat /etc/ld
ldap/         ldap.conf     ld.so.cache   ld.so.conf    ld.so.conf.d/

david@david-desktop:~$ cat /etc/ld.so.conf.d/
i486-linux-gnu  libc.conf       

david@david-desktop:~$ cat /etc/ld.so.conf.d/libc.conf 
# libc default configuration
/usr/local/lib

david@david-desktop:~$ cat /etc/ld.so.conf.d/
i486-linux-gnu  libc.conf       

david@david-desktop:~$ cat /etc/ld.so.conf.d/i486-linux-gnu 
# Multiarch support
/lib/i486-linux-gnu
/usr/lib/i486-linux-gnu

david@david-desktop:~$ 

```

---


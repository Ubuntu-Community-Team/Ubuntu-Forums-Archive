---
title: "No em deixa dessar cap arxiu al disc dur"
date: 2008-10-15
forum: Catalan Team
---

### Post by lluisalguero on 2008-10-15
La veritat es que hi ha lloc de sobres, i a més son arxius de entre 3 i 8 Mb.

Quan clico per baixar-me l'arxiu em surt la imatge de dalt, i quan vaig a buscar el KSnapshot, em surt la de baix. No sé si estàn relacionades entre si...si de cas m'ajudeu només amb la primera, però es que he fet una captura conjunta o si no no em deixava...

[CENTER][[IMG]http://img171.imageshack.us/img171/1255/snapshot51qh8.png[/IMG]](http://imageshack.us)[/CENTER]

Si us serveix d'alguna cosa faig servir l'Ubuntu 8.04.


P.D.: de fa uns dies cap aquí, que no va gaire fi tot plegat...

---

### Post by _DarkEagle_ on 2008-10-15
podem veure un df -h ?

Igual tens més d'una partició al disc dur i en una t'has quedat sense espai ..

Salut !

---

### Post by lluisalguero on 2008-10-15
Tinc 3 particions.

- Una amb Ubuntu 8.04
- Un altra amb el finestres
- i una tercera per guardar arxius, basicament fotos

```
lluis@portatil-ubuntu:~$ df -h
S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/sda4              20G  9,8G  8,5G  54% /
varrun                506M  240K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   56K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1              48G   22G   27G  45% /media/sda1
/dev/sda2              46G   39G  7,7G  84% /media/sda2
lluis@portatil-ubuntu:~$ 

```

---

### Post by kukat on 2008-10-15
es el disc on guardes les fotos??? mmmm....com diuen que la solució mes senzilla sempre es la correcta i coses així....A mi em va passar que no tenia prou espai i era......Per que tenia la paperera plena!
Has provat de fer un CTRL + H per veure els arxius ocults? Igual tens alguna carpeta ".Trash" que està plena!!! No se...es l'únic que se m'ocurreix...Al Gutsy Gibbon, en els disc durs on NO està el sistema, es guarda en la carpeta .Trash, no en la paperera habitual (¿??¿?)

Salut!

---

### Post by _DarkEagle_ on 2008-10-15
Si problema d'espai no és ... només se'm acut algun tipus de problema amb els permisos. En el cas del /tmp es molt extrany .. però podries mirar els permisos d'aquest directori, per defecte haurien de ser:

drwxrwxrwt  19 root root

Salut !

---

### Post by papapep on 2008-10-15
Quina versió de KDE fas servir? 3 o 4?

---

### Post by orestesmas on 2008-10-16
A mi no em sembla que estiguin relacionades entre sí, almenys no en primera instància. L'una et diu que et manca espai en un directori temporal i l'altra que no troba un servidor DCOP.

Però és cert, no veig pas que et manqui espai en disc, per la qual cosa no entenc el primer missatge.

A mi el que se m'acut és anar fent proves petites per mirar d'aïllar el problema: crear un fitxer al directori /tmp, mirar si dóna algun missatge d'error als logs que denoti una arrencada defectuosa de l'entorn gràfic, etc... Sense més informació és difícil de dir res més, a no ser que t'hagis trobat mai amb un problema molt semblant.

---


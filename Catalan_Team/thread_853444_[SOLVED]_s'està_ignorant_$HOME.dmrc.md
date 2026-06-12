---
title: "[SOLVED] s'està ignorant $HOME/.dmrc"
date: 2008-07-08
forum: Catalan Team
---

### Post by diablessamariken on 2008-07-08
Hola

des que l'altre dia, buscant un directori ocult per fer anar l'amule, vaig seleccionar l'opció "mostra els directoris ocults" del navegador de fitxers, cada cop que inicio l'ubuntu em surt el següent missatge:

"El directori $HOME/.dmrc s'ignorarà. Això no permet que es desi la sessió predeterminada i la llengua."

Algú té alguna idea sobre què vol dir? per què? i com solucionar-ho?

Gràcies!

Astrid

---

### Post by patrickfromspain on 2008-07-08
fa no molt em va passar. Fes el següent, en terminal:

gksudo nautilus /home i alla mira les propietats de la carpeta del teu usuari. A permisos has de tenir: 

Propietari - el teu usuari: Crear i suprimir fitxers

Grup: el teu usuari, Accedir als fitxers

Altres: accedir als fitxers, accepta i ja hauria d'estar arreglat.

compte, no facis aplicar als fitxers i subcarpetes.

salut

---

### Post by diablessamariken on 2008-07-09
Hola

he utilitzat el codi que em vas dir al terminal i he mirat les propietats de la carpeta del meu usuari.

Tinc tots els permisos tal i com dius que han d'estar. De fet fa uns dies ja havia mirat aquesta finestra, però justament aquell dia vaig seleccionar l'opció que dius que no seleccioni... és a dir, li vaig dir APLICA ALS FITXERS, ETC...

Què faig?? aix... això em passa per novata :)
Alguna altra suggerència doncs?

Gràcies!

Astrid

---

### Post by RainCT on 2008-07-09
Per a arreglar aquest problema concret, obre una terminal i fes:

```
chmod 600 ~/.dmrc
```

Però no és un bon error a cometre aquest de canviar els permisos de tots els fitxers del teu home, segurament també se't queixarà d'altres fitxers.

---

### Post by diablessamariken on 2008-07-10
mooooltes gràcies! introduint aquest darrer codi al terminal s'ha solucionat! 

De moment no presenta problemes amb d'altres fitxers, creuem els dits :)

Gràcies doncs!

Astrid

---


---
title: "[SOLVED] PAth, com modificar-lo?"
date: 2008-10-07
forum: Catalan Team
---

### Post by tanreb20 on 2008-10-07
Hola, m'interessaria poder afegir una carpeta

```
/home/bernat/scripts/
```

al meu PATH de tal manera que pugui posar el nom d'un dels scripts (en el meu cas un que es diu actualitzar*, o obrir_motion.sh*)

*: cal que els scripts portin el .sh al final? o  amb que portin el
```
#!/bin/bash
``` i siguin executables?

---

### Post by papapep on 2008-10-07
El [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)") i el camí del bash (#!/bin/bash) és imprescindible, així com que tingui els permisos d'execució. El tema de l'extensió .sh és recomanable a fi de no fer un batibull de fitxers irreconeixibles a simple vista.

Respecte el que dius de modificar el path, és bastant més pràctic ficar l'script dins d'un dels directoris que ja és dins del path, així seràs coherent i els executables estaran tots junts.

Fes:

```
echo $PATH
```

i veuràs quins són actualment aquests directoris. Un d'aconsellable per coses que fa un és **/usr/local/bin**.

---

### Post by oriolsbd on 2008-10-08
Si, de tota manera, vols posar aquest fitxer en el teu PATH, edita fitxer /home/nom_usuari/.profile i afegeix la següent línia:

```
export PATH=$PATH:/home/bernat/scripts/
```

Així afegeix el directori que has dit al PATH que ja tens, i te'l posa al final (primer els directoris del sistema).

Salut!

---


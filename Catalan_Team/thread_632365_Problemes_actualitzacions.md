---
title: "Problemes actualitzacions"
date: 2007-12-05
forum: Catalan Team
---

### Post by Asus4 on 2007-12-05
Salut!
Últimament he tingut algun problema les actualització que em van apareixent. Resulta que havia d'actualitzar alguns programes, i al aparèixer la llista em sortia un missatge dient que alguns paquets estaven malament i només podia fer o una "Actualització Parcial" o "Tancar".
D'aquesta manera, anava fent fins que a l'actualitzar el gimp-data, se'm va borrar el gimp (sona raro però és així). Aleshores, ara tinc el gimp-data instalat però el gimp no, i precisament és el que vaig intentar. Al posar per instalar el gimp, el Synaptic em diu que no ho pot fer:
> **No s'ha pogut marcar tots els paquets per a instal·lar o actualitzar.**
Els següents paquets tenen dependències que no es poden resoldre. Assegureu-vos que tots els repositoris requerits estan afegits i habilitats en les preferències.


Aleshores, em surt aquest llistat:

> gimp:
  Depén: libart-2.0-2 (>=2.3.18) però s'instal·larà 2.3.17-1
  Depén: libc6 (>=2.6-1) però s'instal·larà 2.5-0ubuntu14
  Depén: libdbus-1-3 (>=1.1.1) però s'instal·larà 1.0.2-1ubuntu4
  Depén: libdbus-glib-1-2 (>=0.74) però s'instal·larà 0.73-1
  Depén: libfreetype6 (>=2.3.5) però s'instal·larà 2.2.1-5ubuntu1.1
  Depén: libgimp2.0 (>=2.4.2) però s'instal·larà 2.2.13-1ubuntu4.3
  Depén: libglib2.0-0 (>=2.14.0) però s'instal·larà 2.12.11-0ubuntu1
  Depén: libgtk2.0-0 (>=2.12.0) però s'instal·larà 2.10.11-0ubuntu3
  Depén: libpango1.0-0 (>=1.18.2) però s'instal·larà 1.16.2-0ubuntu1
  Depén: libpoppler-glib2 (>=0.6) but it is not installable
  Depén: librsvg2-2 (>=2.18.1) però s'instal·larà 2.16.0-0ubuntu2
  Depén: libxdamage1 (>=1:1.1) però s'instal·larà 1:1.0.3-3
  Depén: zlib1g (>=1:1.2.3.3.dfsg-1) però s'instal·larà 1:1.2.3-13ubuntu4


Exactament què és el que haig de fer?
Gràcies!!

---

### Post by CarlesOriol on 2007-12-06
copia'ns el /etc/apt/sources.list

---


---
title: "ajuda GMT (Generic Mapping Tools)"
date: 2008-04-11
forum: Catalan Team
---

### Post by autista on 2008-04-11
Hola a tothom, he instal·lat el GMT per questions de treball.
Després de la instal·lació em demana el següent:

GMT installation complete. Remember to set these:

-----------------------------------------------------------------------
For csh or tcsh users:
setenv NETCDFHOME /home/sergi/gmt
set path=(/home/sergi/gmt/bin $path)

For sh or bash users:
export NETCDFHOME=/home/sergi/gmt
export PATH=/home/sergi/gmt/bin:$PATH

For all users:
Add /home/sergi/gmt/man to MANPATH
Add /home/sergi/gmt/www/gmt/gmt_services.html as browser bookmark
-----------------------------------------------------------------------

Això de export ja ho he fet, el que no sé fer és el del manpath aquest
Si algú em pot ajudar li estaria molt agraït

---

### Post by papapep on 2008-04-11
Hauries d'afegir aquests path a la variable d'entorn MANPATH que segurament tindràs a /etc/environment.
Si no hi fos, l'hauries de posar.

---

### Post by autista on 2008-04-11
no entenc què em dius, a dins /etc hi ha un arxiu que es diu environment que diu el següent

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="ca_AD.UTF-8"

que he de fer? afegir una nova linia que digui MANPATH="/home/sergi/gmt/man" 
o afegir-ho a dalt on posa PATH? :S

---

### Post by papapep on 2008-04-11
Correcte. Has de crear una nova línia que comenci per MANPATH, tal i com et diu el programa 

```
Add /home/sergi/gmt/man to MANPATH
```

Com que no existeix, crees la línia de cap i de nou. Tant PATH, com LANG, com MANPATH són variables d'entorn que es poden declarar aquí.

---


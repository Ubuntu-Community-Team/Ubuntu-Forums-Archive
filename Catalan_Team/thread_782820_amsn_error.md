---
title: "amsn error"
date: 2008-05-05
forum: Catalan Team
---

### Post by lo gambusí on 2008-05-05
salut!!

he anat a iniciar l'amsn i em diu: *Loading TkCximage failed. This module is needed to run amsn. Please complie aMSN first, instructions on how to compile are located in the file INSTALL.*

Lo cas és que no trobo l'arxiu en qüestió...

---

### Post by papapep on 2008-05-05
[http://rubisf.wordpress.com/2007/09/11/error-de-amsn/](http://rubisf.wordpress.com/2007/09/11/error-de-amsn/)

[http://www.pctux.com.ar/2007/10/solucionar-el-problema-del-amsn-con.html](http://www.pctux.com.ar/2007/10/solucionar-el-problema-del-amsn-con.html)

---

### Post by lo gambusí on 2008-05-05
He provat amb > sudo mv /usr/bin/wish /usr/bin/wish-bak
sudo ln -s /usr/bin/wish8.4 /usr/bin/wish i no m'arregla res. I quan li dóno a > update-alternatives --config wish em diu això: > Només hi ha 1 programa que proveeixi wish
(/usr/bin/wish8.5). No hi ha res a configurar.
update-alternatives: no es pot obrir /var/lib/dpkg/alternatives/wish.dpkg-new per a l'escriptura: Permission denied
oriol@oriol-laptop:~$ 


---

### Post by patrickfromspain on 2008-05-06
sudo update-alternatives --config tclsh

salut!

---

### Post by lo gambusí on 2008-05-06
> Hi ha 2 alternatives que proveeixin «tclsh».

  Selecció     Alternativa
-----------------------------------------------
          1    /usr/bin/tclsh8.3
*+        2    /usr/bin/tclsh8.5

Premeu retorn per a mantenir l'opció per defecte[*], o introduïu un número de selecció:


Al web que m'ha passat el papapep parla del tclsh8.4, he provat amb el 3 i el 5 i seguix igual...

---

### Post by patrickfromspain on 2008-05-06
quin amsn es? d'on l'has tret?

---

### Post by lo gambusí on 2008-05-06
patrick, de fet (no me'n recordava...) tinc l'amsn personalitzat que vas penjar [aquí]("http://ubuntuforums.org/showthread.php?t=649356&highlight=amsn+personalitzat")

---

### Post by patrickfromspain on 2008-05-06
estas segur de que tens aquest instal·lat? Ho veig estrany, ja que esta compilat usant el tcl/tk 8.5. El cas es que aquell amsn ja no et fa falta, ja que als backports d'ubuntu hi es tot, ho vaig explicar fa no res en un altre post:

[http://ubuntuforums.org/showpost.php?p=4861004&postcount=8](http://ubuntuforums.org/showpost.php?p=4861004&postcount=8)

si el que t'agrada es la pell i/o algun plugin, pots descomprimir el "meu" deb i hi trobaras 2 arxius, un d'ells es el data.tar.gz. Descomprimeix-lo y busca per alla la carpeta amb les pells i/o plugin i ho copies tot al seu lloc a .amsn

salut!

---

### Post by lo gambusí on 2008-05-06
hai esborrat los tcl, tk i companyia i he reinstal·lat l'amsn, i ara sí me va...

---


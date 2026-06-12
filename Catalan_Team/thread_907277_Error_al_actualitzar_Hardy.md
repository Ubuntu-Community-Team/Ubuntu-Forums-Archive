---
title: "Error al actualitzar Hardy"
date: 2008-09-01
forum: Catalan Team
---

### Post by slink on 2008-09-01
Quan intento actualitzar Hardy, els següents móduls

linux-generic
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic
tzdata

em dóna el seguent error:

```
S'ha produit un error.
Es proveeixen els detalls següents:

W: No s'ha pogut obtenir http://es.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.24.20.22_i386.deb
  404 Not Found


W: No s'ha pogut obtenir http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.24.20.22_i386.deb
  404 Not Found


W: No s'ha pogut obtenir http://es.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.24.20.22_i386.deb
  404 Not Found
```

Abans de tocar res volia demanar consell. Que haig de fer? Necessito comprovar el sources.list ?

---

### Post by papapep on 2008-09-01
L'[error 404 d'HTTP]("http://ca.wikipedia.org/wiki/Error_404") és un error de connexió client-servidor, normalment que s'ha posat malament una url o que el contingut que abans havia "darrera" una url correcta ha estat esborrat. Aleshores, el que jo provaria és a verificar que el contingut de l'/etc/apt/sources.list és correcte i, també, provaria a canviar de repositoris a veure si funciona correctament amb un altre servidor.

Per cert, no expliques amb quina ordre o procediment has intentat actualitzar de versió.

---

### Post by slink on 2008-09-02
Un altre módul ha donat el següent error:

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages)

Així que ja he sabut quina linia comentar al sources.list. 

> ...no expliques amb quina ordre o procediment has intentat actualitzar de versió

Ho provava de fer amb el Gestor d'actualitzacions. Vaig suposar que el missatge d'error era independent del mètode. 

Moltes gràcies.

---

### Post by papapep on 2008-09-02
El missatge d'error pot ser igual, o no, però saber què s'ha fet abans ajuda a pensar en la possible solució. Quantes més pistes dónes, més ajudes a trobar el perquè. Recorda que nosaltres no som davant el teu ordinador :-)

---


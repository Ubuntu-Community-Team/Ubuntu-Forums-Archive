---
title: "Arxiu de configuració de K3B"
date: 2008-04-06
forum: Catalan Team
---

### Post by cortsenc on 2008-04-06
Això del K3B em te força preocupat. Fa molt de temps, i vaig jugar molt i vaig treure barres imprescindibles sense voler (barres d'eines, espais de treball i altres coses de dins el programa). Be, doncs ara esta impracticable i no se com recuperar la configuració per defecte.

Treballo amb l'entorn d'escriptori Gnome i el K3B no et guarda una carpeta a la **/home** del tipus **.k3b/**, o sigui que buscant dins la carpeta **.kde/** i anant a **/share/apps/k3b** i vaig borra tot el seu contingut, però no ha servit de res. Dins la meva** /home** no he trobat cap altre arxiu relatiu al **k3b**, i entenc que tots els arxius de configuració han d'estar dins de la **/home**, no?

Be, algú se li acut una solució per tornar a restablir els valors per defecte?

Gràcies

---

### Post by papapep on 2008-04-06
Jo ho provaria amb un aptitude purge i tornar a reinstal·lar després. Entre mig, m'asseguraria d'esborrar tots els fitxers ocults i demés que poguessin quedar sense esborrar pel purge (que no hauria de passar, però)

---

### Post by cortsenc on 2008-04-06
Ostres, quina por.
Hem borra com 100 paquets que diu que no utilitzo, però que jo no vull borrar!!

tot i que poso "**sudo aptitude purge k3b**"

---

### Post by patrickfromspain on 2008-04-06
EDITO: rm -rf ~/.kde/share/config/k3brc

salut!

PD: un altre cop probar amb ap-get remov --purge

---

### Post by papapep on 2008-04-06
Sí, és el que tenen alguns paquets que tenen 3 milions de dependències...l'apt-get a vegades normalment és menys agressiu (tot i que no controla tant, clar :-D)

---

### Post by cortsenc on 2008-04-06
> **patrickfromspain said:**
> EDITO: rm -rf ~/.kde/share/config/k3brc


VISCA!!
Moltes gràcies als dos!

---

### Post by orestesmas on 2008-04-08
Ja se m'han avançat...

Bé, per si et torna a passar, el "locate" és una eina força útil: t'enumera nots els fitxers el nom dels quals contingui una cadena concreta.

Llavors pots fer:

```

locate k3b

```

i per tal de filtrar només els que estiguin dins del directori ".kde" fas:

```

locate k3b | grep "\.kde"

```

A mi me'n surten 3, però 2 d'ells són noms de directoris. Llavors em fixo en el "k3brc" perquè els fitxers acabats en "...rc" tradicionalment són fitxers de configuració i/o scripts d'inici en GNU/Linux.

Apa, salut.

---


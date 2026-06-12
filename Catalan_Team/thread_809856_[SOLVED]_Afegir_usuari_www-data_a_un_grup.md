---
title: "[SOLVED] Afegir usuari www-data a un grup"
date: 2008-05-27
forum: Catalan Team
---

### Post by lpargemi on 2008-05-27
Hola

Voldria afegir un usuari a un grup, però no es tracta d'un dels que tinc definits com a persona que pot fer un login al sistema. En concret es tracta de l'usuari que per defecte es genera amb el servidor apache2, anomenat www-data.

El cas és que des de *Sistema>Administració>usuaris i grups* la interfície gràfica només deixa afegir als grups usuaris *de login*.
He vist que a /etc hi ha el fitxer group, on hi ha els grups, però no m'he atrevit a modificar-lo a pel. més que res perquè a cada grup li assigna un número, que no sé què representa ni com ha de quedar després de la modificació.

Perquè necessito aquestes coses rares? El cas és que vull donar dret a veure i modificar uns fitxers (fotos) des de apache - php. Els fitxers estan a un segon disc, al qual apache hi té accés des d'un link a /var/www. La forma que el sistema em funcioni és donant a apache l'usuari lluis enlloc del www-data que hauria de ser. Però això segurament és un forat de seguretat i segur que hi ha una manera més diguem-ne elegant de fer-ho. [El tema de seguretat té importància relativa: dubto que hi hagi cap aprenent de hacker amb interès en entrar a la màquina de casa per demostrar res o amb tan poca feina com per voler-me destruir coses.]

Salut

Lluís

---

### Post by vila-seca on 2008-05-28
> El cas és que des de *Sistema>Administració>usuaris i grups* la interfície gràfica només deixa afegir als grups usuaris *de login*.
He vist que a /etc hi ha el fitxer group, on hi ha els grups, però no m'he atrevit a modificar-lo a pel. més que res perquè a cada grup li assigna un número, que no sé què representa ni com ha de quedar després de la modificació.

Si vols modificar un usuari des de la consola, tens l'ordre usermod, que serveix per a modificar el que necessitis . Aquest numero que s'assigna és el UID del l'usuari i el grup

> Perquè necessito aquestes coses rares? 

Bé, seria una definició dir-ho raro ;), però és el funcionament natural dels Linux, on per evitar problemes, s'assigna a diferents serveis, diferents usuaris, amb permisos diferents.

 > El cas és que vull donar dret a veure i modificar uns fitxers (fotos) des de apache - php. Els fitxers estan a un segon disc, al qual apache hi té accés des d'un link a /var/www. La forma que el sistema em funcioni és donant a apache l'usuari lluis enlloc del www-data que hauria de ser. 

Si vols fer això, hauries d'indicar-li a l'apache que l'usuari que n'és el propietari és el lluis. Ara mateix amb la versió 2 de l'apache no recordo quin és el fitxer de configuració però entenc que ha d'estar a /etc/apache2

Per a canviar el propietari en un fitxer/carpeta des de la consola has de fer servir l'ordre chown per exemple: chown lluis:www-data /carpeta_amb_les_fotos

---

### Post by RainCT on 2008-05-28
Si ho he entés bé, vols afegir l'usuari www-data al grup lluis?

```

sudo adduser www-data lluis

```

---

### Post by lpargemi on 2008-05-28
Hola de nou

Aquesta instrucció m'ha funcionat, i és la que no sabia on trobar.

```

sudo adduser www-data nomdelgrup

```

Agraït 


> Si vols fer això, hauries d'indicar-li a l'apache que l'usuari que n'és el propietari és el lluis. Ara mateix amb la versió 2 de l'apache no recordo quin és el fitxer de configuració però entenc que ha d'estar a /etc/apache2

Això és el què faig fins ara dient-li a l'apache que el seu usuari és lluis (i efectivament és al directori etc/apache2 i associats), però és que l'usuari lluis -que sóc jo- té molts drets a coses que per entendre'ns apache no ha de fer-hi res.

De tota manera suposo que aquests comentaris haurien de ser d'un altre fil.

Agraït

lluís

---

### Post by papapep on 2008-05-28
Si el grup *lluís* té massa permisos, segons dius tu, el que pots fer és crear-ne un de nou, donar-li els permisos que vulguis respecte al disc extern que parles, i el seu contingut, i afegir l'usuari *www-data* de la mateixa manera que has fet a l'altre grup.

---

### Post by lpargemi on 2008-05-28
> **papapep said:**
> Si el grup *lluís* té massa permisos, segons dius tu, el que pots fer és crear-ne un de nou, donar-li els permisos que vulguis respecte al disc extern que parles, i el seu contingut, i afegir l'usuari *www-data* de la mateixa manera que has fet a l'altre grup.

I això és el què he fet: per manipular les fotos (que és del què es tracta) tinc un grup que he anomenat fotograf i que de moment hi érem la meva dona i jo. Les meves filles (set i nou anys) no, i així si s'equivoquen mirant les fotos no es poden carregar res. El què he fet -i no podia- és afegir al grup fotograf a www-data, perquè tinc muntada una aplicació amb php i mysql per buscar, seleccionar i ordenar les fotos amb moltes dades procedents de quan vivia al costat fosc... 

Gràcies per l'interès.

Lluís

---


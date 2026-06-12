---
title: "Odbc amb MS SQL Server"
date: 2008-03-31
forum: Catalan Team
---

### Post by tet_11 on 2008-03-31
Bon dia,
En primer lloc comentar que soc un usuari novell que he coençat a utilitzar l'Ubuntu.
Em preguntaba si existia una manera com la que hi ha en el windows de crear un dns de sistema en l'OBDC ja que utilitzo un programa que conecta amb el servidor a on hi ha el Sql server.
Gracias per tot

---

### Post by CarlesOriol on 2008-03-31
El odbc.ini i odbcints.ini que hi ha a la carpeta /etc/ son globals i equivalens als origens de dades de sistema de windows.

(Vols dir DSN el DNS és el sistema de traducció de noms per IPs)

---

### Post by tet_11 on 2008-03-31
Bones Carles,
Merci perla teva rapida resposta. Perdona pero com que he comentat soc novell, pero sempre hi ha un moment per començar. Tens rao amb lo DNS. El tema es que he entrat en el drive c e wine i a etc i no trobo el que em comentes. Em podries tirar un cap?
Merci
Esteve

---

### Post by papapep on 2008-03-31
Bones i benvingut al fòrum, Esteve.

Abans que res, convidar-te a passar pel fil de benvinguda i explicar-nos una mica la teva vida: [http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)

També estaria bé que fessis una llegida al fil que tenim pels nouvinguts:
[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

Respecte el que preguntes, crec que seria bo que ens expliquessis una mica més en detall com penses fer el que comentes, ja que es dedueix que penses executar una aplicació Windows a través de Wine, i això no ho has dit de sortida ;-)

---

### Post by tet_11 on 2008-03-31
Bones papapep,
Ja he explicat un xic la meva vida en el fil de benvinguda.
Explico una miqueta l'historia. A la feina ara per ara estic treballant amb wiindows, i m'agradaria canviar a ubuntu. El problema que tinc, es que utilitzo un programa de gestio que va conectat a un servidor a on te el sql server, per això demanava si havia alguna possibilitat de poder conectar-ho amb l'ubuntu.
Aquest programa quan el instalo a windows haig de afegir un DSN de sistema.
Pensaba fero amb el wine.
Espero haver-me explicat, torno a recalcar que soc un novell de cap a peus, però m'agradaria començar a introduirme dintre aquest mon.
Gracies per tot.

---

### Post by CarlesOriol on 2008-03-31
Mmmf... 

No t'auguro grans èxits usant gestió i odbc amb el wine.

Sempre pots usar-lo amb el VirtualBox en mode seamless. 
L'altra opció és conservar un sol ordinador en la xarxa amb windows on hi pots posar un programa com el xp-unlimited per accedir en diferents sessions i tota la resta d'usuaris amb linux. Així limites tots els problemes a un sol punt.

Nota al fil de benvinguda. D'on de l'alt empordà? La meva familia per part de pare ve del Port de la Selva.

---

### Post by tet_11 on 2008-04-01
Ara mateix estic a Empuriabrava

---


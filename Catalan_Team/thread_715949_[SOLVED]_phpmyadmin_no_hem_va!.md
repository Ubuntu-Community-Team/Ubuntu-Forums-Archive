---
title: "[SOLVED] phpmyadmin no hem va!"
date: 2008-03-05
forum: Catalan Team
---

### Post by kukat on 2008-03-05
Salutacions!

Bé, que estic molt liat amb el LAMP! Ho he provat ja tot. Primer com ens va dir el professor, a la consola, i he configurat el fitxer del apache afegint-li la linia del phpmyadmin, i res. 

Després he vist que es pot instalar tot el necessari des dels repositoris de Synaptic. A "Edita" "Marca els paquets per tasques", i he vist que hem faltava alguna cosa... Però continua sense anar. Quan pose [http://localhost/phpmyadmin](http://localhost/phpmyadmin) se m'obri una finestra del firefox per demanar-me que vullc fer amb eixe fitxer.....Ja no se el que fer...

Gràcies, es per a un treball per al divendres! :confused:

---

### Post by papapep on 2008-03-05
Has d'anar al php.ini i ficar-li el mòdul i les extensions que vols que el php interpreti com a documents per mostrar-te i no com a fitxers.
A internet hi ha milers de documents amb la mateixa consulta, és la típica del primer cop que configures php sota apache:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by kukat on 2008-03-05
Ep! Gràcies!

Solament he fet açó:

$ gksudo "gedit /etc/php5/apache2/php.ini"

Look for the 'extension_dir' property. It should be by default '/usr/lib/php5/ext'. If it's not, change it for this value.

-Now create the default directory for extensions:

$ sudo mkdir /usr/lib/php5/ext

El que ve després no ho he fet, per que m'he rallat, però ja funciona!!! Moltes gràcies. Xé, es un poc complicat açò del LAMP. En l'institut no sé que faré, per que allò si que és per a flipar....:)

---

### Post by papapep on 2008-03-05
No ho és pas de complicat però, com tot, la primera vegada, quan no tens experiència, fa una mica d'impressió ;-)

---

### Post by kukat on 2008-03-06
Jejejejej... El millor de tot es que avui vaig a explicar-li-ho al professor. L'home es complica massa la vida. Instalar-ho tot es més senzill amb el Synaptic, però ell no...jajajajaj:) Si consegueix fer-ho a l'Insti ( amb el Feisty Fawn amb 205 actualitzacions per a fer, ja que la connexió es realment patètica) ho comentaré per aci, per que es una"odisea"!

Salut!

---


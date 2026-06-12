---
title: "[SOLVED] Fer servir Nokia N95 com a router per Ubuntu"
date: 2008-11-12
forum: Catalan Team
---

### Post by Frealof on 2008-11-12
Hola a tothom!

Fa un temps vaig instal·lar Ubuntu Hardy Heron al PC del meu oncle. Com que no té connexió a la xarxa hi ha paquets que no se'ls pot baixar per tenir el PC en condicions. 

El fet es que fa poc es va canviar el mòbil que tenia per un Nokia N95 (de vodafone), a la botiga li varen dir que el podria fer servir per connectar-se a la xarxa amb una tarifa plana, i realment es així. Però clar, la pantalleta del mòbil més aviat no es com la del PC... i la navegació es fa un xic complicada. La meva pregunta es saber si hi ha alguna manera de fer servir aquest telèfon com a router, tenim clables USB, connexió bluetooth, etc.

---

### Post by papapep on 2008-11-12
Juntament amb [aquest]("http://public.warp.es/wader") programari, hauria de funcionar correctament. Amb l'[antecessor]("https://forge.betavine.net/projects/vodafonemobilec/"), un amic meu el va fer anar de módem sense més que instal·lar-lo.

---

### Post by Frealof on 2008-11-13
Moltes gràcies per la resposta Papapep, així que ho hagi pogut provar ja us diré com ha anat.

---

### Post by CarlesOriol on 2008-11-14
Amb l'intrepid no cal absolutament res.

Connecta el telèfon a l'usb, obres les connexions de xarxa i tries vodapone a l'estat espaniol... i ja et pots connectar clicant a la icona del network manager.

---

### Post by papapep on 2008-11-14
Això si pots fer anar el Gnome-Network-Manager...:-)

---

### Post by quitus on 2008-11-14
jo ho vaig provar amb un sony ericsson 530 i nomes vaig haver de configurar el telefon. connectivitat/usb/internet usb/activar.

salut.

---

### Post by CarlesOriol on 2008-11-15
Jo tinc un Sony Ericsson w880 i com diu en quitus... :-) brutal.

---

### Post by SiscoGarcia on 2008-11-15
Jo tinc un Nokia N73, i pel que esteu dient també hauria de funcionar, no?

Ara bé, el dubte és la tarifa que m'aplicaran,... suposo que això ja depèn de la gent de la companyia i no serà com qualsevol trucada...

... ho miraré.

---

### Post by Frealof on 2008-11-17
Bones a tothom,

O sigui que amb l'Intrepid ja ve "de série", amb la iso normal i corrent o s'ha de descarregar alguna cosa més? Ho dic perquè si s'ha de descarregar alguna cosa... a través del PC aquell, nanai de la xina... 

En tot cas primer provarem el programa que va proposar en Papapep, i si veig que la cosa es massa complicada per mi suposo que passaria a fer servir la imatge de CD... dilluns vinent ja us podré donar una resposta.

Salut!!

---

### Post by oriolsbd on 2008-11-17
Hola, Frealof.

No sé la resposta a la teva pregunta de si "va de sèrie", però quant al que comentes de "si s'ha de descarregar alguna cosa... a través del PC aquell, nanai de la xina...", sí que hi hauria alternatives.

Si calgués instal·lar-hi algun paquet sense tenir xarxa, sempre pots fer des d'un altre ordinador que sí tingui xarxa:
sudo apt-get install -d nom-paquet

El paràmetre "-d" fa que només et baixi el paquet (sense instal·lar-lo). Això et deixarà un fitxer ".deb" (que es dirà "nom-paquet_num-versio.deb") al directori /var/cache/apt/archives del PC que sí té xarxa. Aquest fitxer el pots portar (amb un disquet, CD, USB, etc.) al PC que no té xarxa, i instal·lar-lo anant al directori on tens el fiter i fent:
sudo dpkg -i nom-paquet_num-versio.deb

Salut! :-)

---

### Post by quitus on 2008-11-17
> **oriolsbd said:**
> Hola, Frealof.

No sé la resposta a la teva pregunta de si "va de sèrie", però quant al que comentes de "si s'ha de descarregar alguna cosa... a través del PC aquell, nanai de la xina...", sí que hi hauria alternatives.

Si calgués instal·lar-hi algun paquet sense tenir xarxa, sempre pots fer des d'un altre ordinador que sí tingui xarxa:
sudo apt-get install -d nom-paquet

El paràmetre "-d" fa que només et baixi el paquet (sense instal·lar-lo). Això et deixarà un fitxer ".deb" (que es dirà "nom-paquet_num-versio.deb") al directori /var/cache/apt/archives del PC que sí té xarxa. Aquest fitxer el pots portar (amb un disquet, CD, USB, etc.) al PC que no té xarxa, i instal·lar-lo anant al directori on tens el fiter i fent:
sudo dpkg -i nom-paquet_num-versio.deb

Salut! :-)

això està molt bé, però... i les dependències? Passarà el mateix que amb el fitxer?

---

### Post by ilku on 2008-11-18
Hola:
Si tens un ordinador amb la mateixa versió d'ubuntu que el que vols instal.lar, hi ha una aplicació que se'n diu aptoncd que et permet descarregar en un cd tots el paquets que tinguis a la maquina i gravar-los en un cd, amb això pots anar a un altre ordinador i instal.lar un paquet i les seves dependències que tinguis en el primer ordinador sense tenir connexió amb el segon ordinador.

Bufffffff que malament que ho explico.

---

### Post by oriolsbd on 2008-11-18
Hola, Quitus.

Clar, això que jo comento és només una mesura excepcional si necessites instal·lar algun paquet a un PC sense xarxa (se suposa que per aconseguir que hi funcioni la xarxa). Si el paquet té dependències, cal traspassar tots els seus fitxers .deb. Com a mètode excepcional funciona, però lògicament no es pot tenir (o mantenir) un ordinador permanentment amb aquest mètode. Seria de bojos... :-)

Jo ho he utilitzat en algun cas per passar a un ordinador que no té xarxa el Wicd o el Ndiswrapper. Un cop ja funciona la xarxa, a utilitzar el mètode habitual. :-)

Salut!

---

### Post by CarlesOriol on 2008-11-20
> **Frealof said:**
> O sigui que amb l'Intrepid ja ve "de série", amb la iso normal i corrent o s'ha de descarregar alguna cosa més? 

No et cal instalar RES DE RES.

---

### Post by quitus on 2008-11-20
suposo que la millor opció per instal·lar ubuntu totalment actualitzat es crear el meu propi live cd, em tornare a llegir els innumerables fils que hi ha sobre aquest tema.

salut

---

### Post by quitus on 2008-11-20
suposo que la millor opció per instal·lar ubuntu totalment actualitzat es crear el meu propi live cd, em tornaré a llegir els innumerables fils que hi ha sobre aquest tema.

salut

---

### Post by Frealof on 2008-11-24
Molt bones a tothom!!

Com ja vaig dir que faria, avui es dilluns, i toca dir alguna cosa ;)

Comencem pel principi. Vaig provar d'instal·lar el programa que va recomanar en Papapep, afegint les adreces que a la plana posava al sources.list. 

Actualitzo l'apt, provo d'instal·lar el programa i... problemes amb les dependències amb tres mòduls Python, provo de descarregar-los en la seva versió .deb per a hardy i... com que em dona errors opto per descarregar els tar-bz..., transformar-los mitjançant l'Alien i instal·lar-los però sembla que els meus coneixements no son suficients i tot i crear els arxius, aquests no s'instal·len, em dona problemes... veient que no me'n acabava de sortir i que els PC's de la universitat anaven bastant buscats dooncs vaig optar per la opció 2, passar a Intrepid i provar a veure si furul·lava o no... la resposta es SI. Vaig actualitzar el PC del meu oncle a l'Intrepid Ibex i de moment em diu que tot li va com una seda. Esperem que continuï així.

Gràcies a tots per els consells.

Salut!

---


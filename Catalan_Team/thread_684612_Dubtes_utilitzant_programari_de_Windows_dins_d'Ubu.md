---
title: "Dubtes utilitzant programari de Windows dins d'Ubuntu"
date: 2008-02-01
forum: Catalan Team
---

### Post by mcako on 2008-02-01
Llegint el tema sobre VirtualBox m'ha vingut una pregunta sobre el tema i m'agradaria que m'aconselléssiu: he muntat un ordinador per un local social de Tarragona on hi he instal·lat **Windows XP** i **Ubuntu**. La meva il·lusió seria que la gent arribés a utilitzar únicament Ubuntu sense haver de recòrrer a Windows, el problema ve a l'hora d'utilitzar certs programes com Photoshop i demés que només estan per windows.

Llavors la meva pregunta és, pot el VirtualBox solucionar aquesta mancança? es ralentitza molt quan obres programes grans estil Photoshop? quin emulador creieu que es millor **VMware** o **VirtualBox**? podria solucionar-se simplement executant les aplicacions amb el **Wine**?

Per últim volia preguntar sobre si seria possible (si no hi hagués més remei i l'usuari volgués utilitzar Windows) que la gent hagués de **passar per collons** sempre per Ubuntu abans de carregar el SO Windows XP per així d'aquesta manera obligar forçosament a la gent a que es vagi familiaritzant amb Ubuntu..:mrgreen:

---

### Post by pespin on 2008-02-01
Crec que amb la última versió del wine vaig llegir que el photoshop ja funciona. De totes maneres et recordo que disposes del GIMP tant a Ubuntu com a Windows. Potser hauries de plantejar-te aquesta posibilitat :)

---

### Post by Daerun on 2008-02-01
No sé si passarà amb tots els programes, però jo tinc emule instal·lat amb wine, i em trobo que els carácters es mostren amb un tamany molt més petit del que seria normal, en un to gris clar, i a més sense accents (mostrant carácters del tipus "Â" en comptes "à"). Ho comento perquè si això mateix passa amb un programa com Photoshop, pots acabar amb maldecap de mirar el monitor en aqueste condicions...

---

### Post by papapep on 2008-02-01
Daerun: i perquè no fas servir l'amule en vers del que tens muntat???

Mcako: Jo el que crec que és bastant efectiu, sempre que és possible, és el que et diu en Pespin. Se'ls posa el firefox, thunderbird, gimp i totes les aplicacions lliures que es pugui sota windows. Un cop s'hi han acostumat els importa ben poc quin sistema operatiu les fa córrer (a nosaltres no, però ;-))

---

### Post by Daerun on 2008-02-01
> **papapep said:**
> Daerun: i perquè no fas servir l'amule en vers del que tens muntat???


Per la sencilla raó que -de moment- no he trobat un client p2p que m'ofereixi EXACTAMENT les mateixes prestacions que emule (ni millors tampoc, és clar). Amule s'hi acosta bastant, però té un parell de cosetes que no m'acaben de convèncer. Per no dir que sóc bastant gelós dels meus crèdits actuals d'emule, que només es poden importar parcialment a amule :biggrin: (i no sé si es poden importar a cap altra alternativa... però com dic, de moment no n'he trobat cap).

---

### Post by patrickfromspain on 2008-02-01
Llavors deus ser un usuari molt avançat en el tema P2P... perque jo no veig molta diferencia entre un i altre.

salut!

---

### Post by lluisanunez on 2008-02-01
Totalment d'acord amb Patrickfromspain... no recordo gaires diferències.
Per altra banda, els teus crèdits, copiant els fitxers d'usuari d'emule a amule, s'importen sencers

---

### Post by mcako on 2008-02-05
Com que em vau  recomanar utilitzar el Wine, el vaig instal·lar i vaig estar provant d'executar alguns programes d'entorn Windows i no va resultar de cap manera, vai estar mirant el tema llibreries des del winecfg però no em va donar cap resultat. Ara m'he posat a buscar dins aquest fòrum si hi havia algun comentari al respecte i m'he trobat amb la següent cita d'en papapep:
> **papapep said:**
> El wine permet que instal·lis programes Windows al teu sistema Gnu/Linux i els executis amb l'emulador. **No permet que executis programes ja instal·lats a una altra partició on tens el windows**.
Doncs ara me n'entero, ja podia anar provant.. El que passa es que tinc una partició per Ubuntu i una altra per Windows, llavors jo intentava executar programes de la partició Windows.
 Així que per poder utilitzar qualsevol programari Windows he d'instal·lar-lo a Ubuntu mitjançant el Wine? em sembla una mica redundant haver d'instal·lar un mateix programa a dos llocs.
Suposo que ara em direu què lo absurd es que estigui utilitzant Photoshop tenint el Gimp, però es que ja estic molt acostumat al programari d'Adobe i em fa certa peresa acostumar-me a utilitzar Gimp, qüestió de gustos..

---

### Post by Daerun on 2008-02-05
Jo vaig estar buscant també si es podia accedir a la partició Windows d'alguna manera a través del VirtualBox o el vmware, perquè vull deixar enrere tant com pugui el finestres, però volia fer servir el photoshop mentre m'acabo acostumar al Gimp, que encara no manejo gaire bé. Però vaig trobar dit a molts llocs que no era GENS recomamable. És per això que vaig comentar allò del problema dels caràcters estranys que es veuen en pantalla amb el Wine.

Et recomano que busquis tutorials del Gimp, que n'hi ha molts per la xarxa, i després de tot, si saps com fer-lo anar, fa el mateix que el photoshop.

---

### Post by guillemsola on 2008-02-06
Jo us recordaria que el 9 dels 10  manaments del linux que diu que "no recrearàs Windows"

 [http://www.vivalinux.com.ar/articulos/10-mandamientos.html](http://www.vivalinux.com.ar/articulos/10-mandamientos.html)

Realment el finestres ens té molt marcats per segons quines coses. I el wine és un bon placebo per perdre la por al linux. De totes formes si heu de fer 
servir el wine jo casi recomenaria passar del que ve de sèrie amb l'ubuntu i passar a repositoris propis de wine. 

Molt fàcil de fer: 
[http://www.guia-ubuntu.org/index.php?title=Wine#Desde_repositorios_oficiales_del_proyecto_Wine](http://www.guia-ubuntu.org/index.php?title=Wine#Desde_repositorios_oficiales_del_proyecto_Wine)

Salut!

---

### Post by Daerun on 2008-02-06
És el punt més dificil de complir per als novells :lol:

Però "ho estic deixant" :P

---


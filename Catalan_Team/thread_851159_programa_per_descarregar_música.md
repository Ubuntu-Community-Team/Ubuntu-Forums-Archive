---
title: "programa per descarregar música"
date: 2008-07-06
forum: Catalan Team
---

### Post by diablessamariken on 2008-07-06
Hola

tinc l'Ubuntu Hardy i m'agradaria poder descarregar-me música sense necessitat d'haver d'utilitzar windows amb l'emule. Em podeu recomanar algun programa? 

Gràcies
Astrid

---

### Post by Kosimo on 2008-07-06
> **diablessamariken said:**
> Hola

tinc l'Ubuntu Hardy i m'agradaria poder descarregar-me música sense necessitat d'haver d'utilitzar windows amb l'emule. Em podeu recomanar algun programa? 

Gràcies
Astrid

Dóna un cop d'ull a l'aMule (La versió Linux d'emule)

obre el terminal i escriu:   ```
sudo apt-get install amule 
```

Tot i que si vols l'última versió pots descarregar-te un .deb ben senzill d'instal·lar des d'aquest enllaç: [http://getdeb.net/release/2784](http://getdeb.net/release/2784)  Són dos, i hauras d'instal·lar primer l'amule-common i després l'altre.

---

### Post by diablessamariken on 2008-07-06
Moltes gràcies! 

m'he descarregat la versió antiga seguint la comanda del terminal que m'has recomanat.

Gràcies

Astrid

---

### Post by diablessamariken on 2008-07-06
HOla

he instal·lat l'amule i he descarregat un parell o tres de fitxers però tinc un problema. 

El directori de descàrrega dels fitxers em resulta inaccessible. És un directori creat automàticament per l'amule que s'anomena:

.incomming

I des del navegador de fitxers no hi puc accedir. 

Fins i tot he provat de canviar-lo i posar-hi un directori diferent creat per mi, però les descàrregues continuen fent-se al directori anterior... 

Alguna suggerència?

Gràcies
Astrid

---

### Post by patrickfromspain on 2008-07-06
diria que el lloc on es descarreguen els arxius es /home/el-teu-usuari/.aMule/Incoming si poses ~/.aMule/Incoming al nautilus segur que hi podras entrar.

Si el canvies el directori de les descarregues, el arxius ja descarregats no es mouen de lloc automaticament.

salut!

---

### Post by Kosimo on 2008-07-06
> **diablessamariken said:**
> HOla

he instal·lat l'amule i he descarregat un parell o tres de fitxers però tinc un problema. 

El directori de descàrrega dels fitxers em resulta inaccessible. És un directori creat automàticament per l'amule que s'anomena:

.incomming

I des del navegador de fitxers no hi puc accedir. 

Fins i tot he provat de canviar-lo i posar-hi un directori diferent creat per mi, però les descàrregues continuen fent-se al directori anterior... 

Alguna suggerència?





Gràcies
Astrid


Hola!
Obre la carpet home (no sé com es diu en català, però és la general on tens tots els documents) I apreta CONTROL + H d'aquesta manera veuras els arxius ocults. La carpeta .amule (comença amb un punt) alla dins tindràs la carpeta (incoming) que és on desa els arxius per defecte. 

Sàpigues però que pots configurar-ho per que te les desi allà on tu vulguis.

---

### Post by oriolsbd on 2008-07-07
Hola, Àstrid.

He vist el teu primer missatge, i volia donar-te una altra opció. El Mldonkey. Només has d'instal·lar el paquet "mldonkey-server", i un cop arrancat tot es gestiona des del navegador d'internet que utilitzis (el Firefox, el Konqueror, etc.) a través de l'adreça "http://localhost:4080/".

Potser no és tan fàcil d'utilitzar com l'aMule (tampoc no és molt complicat), però suposo que pel fet de no tenir GUI és molt lleuger i gairebé no es nota quan s'està executant.

Salut!

---

### Post by diablessamariken on 2008-07-08
Hola

ja he trobat la carpeta incoming, no la veia perquè és una de les protegides o amagades.

Però encara que modifico el directori d'arribades de les baixades, a la practica no funciona, i continuen produint-se al directori incoming... estrany...

De totes maneres, gràcies per les aportacions!

Astrid

---

### Post by CarlesOriol on 2008-07-09
Sempre pots fer un enllaç a incoming on vulguis, o eliminar incoming i convertir-lo en un enllaç.

---

### Post by lluisanunez on 2008-07-09
Si no t'agrada emule, prova Frostwire. És en Java i no falla mai, ni firewalls ni routers ni PnP, tot li és igual

---

### Post by kefort on 2008-07-09
Hola Astrid, jo tinc també instal.lat l'amule i li vaig canviar la carpeta on volia que es fes la descàrrega i cap problema; només tens d'anar a 
Opcions->Directoris i al box d'Arxius entrants poses la nova direcció tipus:
/home/usuari/entrades

Salut.

---

### Post by dafaktor on 2008-07-10
També pots provar de descarregar música mitjançant el protocol bittorrent i cercant a [Pirate Bay]("http://thepiratebay.org"), [Mininova]("http://www.mininova.org") o [Isohunt]("http://isohunt.com").

La Hardy Heron ja porta un client de bittorrent, el Transmission, però a mi m'agrada més el Deluge.

Siau !

---


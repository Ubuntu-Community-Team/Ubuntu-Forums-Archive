---
title: "[SOLVED] problemes amb el wifi"
date: 2008-08-03
forum: Catalan Team
---

### Post by motor25 on 2008-08-03
acabo d'instalar el ubuntu en el ordinador i el problema que tinc esque al conectar em demana la clau moltes vegades i amb sort unes tres vegades despres vaig al firefox i no s'em conecta es un usb i la senyal es molt bona sta sempre entre el 98% i el 100%
em podeu ajudar gracies es que també sóc nou 
gracies adeu

---

### Post by papapep on 2008-08-03
Hola motor25 "queetsnou" :-)

Benvingut al fòrum. T'aconsello, abans que res, fer-te una bona llegida al fil de capçalera pels més novells, a banda de fer una petita presentació de tu mateix al Fil de benvinguda.

Entendràs que si no ens dones més pistes sobre el teu ordinador, placa wifi, que hi tens instal·lat/què has fet fins ara, etc, no tenim gaires eines per poder valorar què pots fer ;-)

---

### Post by motor25 on 2008-08-03
el que tinc es el ordinador que tenia amb el xp li he instalat el ubuntu dins d' ell amb el cd d'instalacio que te una opcio que et dona que es instalar ubuntu a xp pero es separat 
no se si m'explico a més la targeta es un usb que et bé amb el roter

---

### Post by papapep on 2008-08-03
Molt bé Aleix. Mira, necessitem saber, per a poder-te ajudar, quin model de dispositiu wifi usb és en concret el que "et venia amb el router". Per a poder-ho saber, si no porta una etiqueteta que ho posi ben claret, sovint cal executar la següent ordre a un terminal:

```
lsusb
```

Fent això et sortirà un piló de text com a resposta de la ordre. Talla'l i enganxa'l després al fòrum per a que veiem què diu (sobretot que el dispositiu wifi estigui endollat al port usb quan ho facis).

L'ordinador és algun model i marca concret? és un clònic? es fix? és portàtil?

---

### Post by motor25 on 2008-08-03
espera k he trobat el cd d'instalacio de windows i posa que es un comtrend HG/CT-536+(C03_r14)
aquest es el model que posa en el cd

---

### Post by torracastanyes on 2008-08-03
Segons la pàgina de Comtrend

[http://www.comtrend.com/cgi-bin/db-search.cgi?template=News&dbname=product&key2=21&action=searchdbdisplay](http://www.comtrend.com/cgi-bin/db-search.cgi?template=News&dbname=product&key2=21&action=searchdbdisplay)

el CT-536+ es un router wifi ADSL2+

---

### Post by motor25 on 2008-08-03
he mirat per la web i el unic usb es el  CT-WN4322Z
http://www.comtrend.com/links/30$product.htm
el de la foto es igual al que tinc jo

---

### Post by torracastanyes on 2008-08-03
Si es aquest, sembla que el xip és zydas, però caldría estar-ne segurs. De vegades les aparences enganyen.

Segueix les instruccions d'en papapep i posa tota la imformació que puguis.

---

### Post by motor25 on 2008-08-03
no ho puc fer ja que no tinc internet en el linux i per escriure en el forum estic en windows

---

### Post by torracastanyes on 2008-08-03
Pots copiar el text en una pagina del writer i portar-la al windows amb un pendrive o un disquet?

---

### Post by motor25 on 2008-08-04
no puc per que noentinc i la botiga del poble esta tancada per vacances

---

### Post by papapep on 2008-08-04
Com algú pot haver vist ja, la calor m'ha fos la neurona (la única que em quedava) i he creuat fils....res, oblida el que he posat...

---

### Post by motor25 on 2008-08-04
esperat tinc un amic que en te un i m'ha la deixat 
però fins demà no el puc tenir demà ja intentaré penja el que pugui

---

### Post by motor25 on 2008-08-05
aleix@aleix-desktop:~$ lsusb

Bus 005 Device 006: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller

Bus 005 Device 005: ID 0ace:1215 ZyDAS WLA-54L WiFi

Bus 005 Device 003: ID 14aa:0160 AVerMedia (again) or C&E 

Bus 005 Device 001: ID 0000:0000  

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 002: ID 045e:00ce Microsoft Corp. Generic PPC Flash device
aqui el resultat
Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 004: ID 0c45:608f Microdia 

Bus 001 Device 001: ID 0000:0000

---

### Post by papapep on 2008-08-05
Quina encriptació té el senya wifi: wep,wpa, wpa2?

Pel que dius, i el dispositiu que és, sembla que sigui més un problema de configuració, o del network-manager, que del dispositiu usb en sí.

Com has configurat el gestor de xarxes (network-manager)?

---

### Post by motor25 on 2008-08-05
la encriptacio es wep
i la configuracio es automatica 
el que faig es al engegar vaig a les conexions al costat del regotje i apreto el boto dret i clico la conexio inalambrica meva
em demana la clau la poso i al cap d'una estona igual aixo de demansr la clau ho fa uns cinc o sis cops i després para

---

### Post by papapep on 2008-08-05
Entenc...en aquest cas, intentant delimitar la font de l'error, els punts a avaluar són tres:

 1- el router
 2- el dispositiu usb
 3- el gestor de xarxes

(podríem posar-ne més, però deixem-ho aquí per ara).

l'1 i el 2 entenc que els podem eliminar, ja que sota windows et funcionen, si no recordo malament.

Per tant, el que jo faria (i la meva pràctica corrobora) és canviar el gestor de xarxes. Podries provar amb un que es diu wicd.

Hauries d'aprofitar una estona d'aquestes que et funciona el wifi i instal·lar-lo.

Et caldrà afegir un repositori al synaptic. Si dins el Synaptic vas a Preferències> Dipòsits> Afegeix, fica el següent:

Tipus: binaris
URI: [http://apt.wicd.net](http://apt.wicd.net)
Distribució: hardy
Components: extras

Un cop fet aixó, acceptes i actualitzes la base de paquets (Refresca). Busques el paquet pel seu nom "wicd" i li dius que el vols instal·lar.

**[COLOR="Red"]COMPTE! Si et proposa de desinstal·lar l'ubuntu-desktop NO ho has d'acceptar!!![/COLOR]**

Un cop hagi acabat d'instal·lar-se, al menú Aplicacions>Internet tindràs una icona amb el programa per a poder-lo configurar. Ja veuràs que és semblant a la majoria de programes de gestió de xarxes però aquest, a més, funciona ;-)

---

### Post by motor25 on 2008-08-05
es que em el linux no em funciona pero cap estona

---

### Post by oriolsbd on 2008-08-05
Hola, per fer aquesta actualització, tens la possibilitat de connectar el PC amb el router Wifi directament amb un cable "ethernet"? (és el cable "normal" de xarxes, com el de telèfon, però amb el connector més ample). Si pots, fes-ho, segueix les instruccions d'en Papapep i, un cop tinguis instal·lat el Wicd ja pots reiniciar el sistema (desconnectant el cable ethernet) i provar si la xarxa funciona (bé, després de configurar el Wicd, clar). :-)

Salut!

Oriol.

---

### Post by motor25 on 2008-08-05
em costara una mica ja que em costa canviar el roter per el lloc on el tinc i el lloc on l'haig de posar
però ho intentare

---

### Post by patrickfromspain on 2008-08-05
> **papapep said:**
> Entenc...en aquest cas, intentant delimitar la font de l'error, els punts a avaluar són tres:

 1- el router
 2- el dispositiu usb
 3- el gestor de xarxes

(podríem posar-ne més, però deixem-ho aquí per ara).

l'1 i el 2 entenc que els podem eliminar, ja que sota windows et funcionen, si no recordo malament.

Per tant, el que jo faria (i la meva pràctica corrobora) és canviar el gestor de xarxes. Podries provar amb un que es diu wicd.

Hauries d'aprofitar una estona d'aquestes que et funciona el wifi i instal·lar-lo.

Et caldrà afegir un repositori al synaptic. Si dins el Synaptic vas a Preferències> Dipòsits> Afegeix, fica el següent:

Tipus: binaris
URI: [http://apt.wicd.net](http://apt.wicd.net)
Distribució: hardy
Components: extras

Un cop fet aixó, acceptes i actualitzes la base de paquets (Refresca). Busques el paquet pel seu nom "wicd" i li dius que el vols instal·lar.

**[COLOR="Red"]COMPTE! Si et proposa de desinstal·lar l'ubuntu-desktop NO ho has d'acceptar!!![/COLOR]**

Un cop hagi acabat d'instal·lar-se, al menú Aplicacions>Internet tindràs una icona amb el programa per a poder-lo configurar. Ja veuràs que és semblant a la majoria de programes de gestió de xarxes però aquest, a més, funciona ;-)
nomes una petita puntualitzacion: ubuntu-desktop nomes es un "metapackage", es pot desinstal·lar sense gaires problemes.

salut

---

### Post by papapep on 2008-08-05
Clar que és un metapaquet (un paquet que realment no és tal, sinó que en representa un grup més o menys gran per a simplificar certes instal·lacions i no ha ver de fer moltes passes), però el problema és si l'aplicació que gestiona els paquets intenta esborrar-lo juntament amb tots els seus "representats". I més quan qui està executant la ordre és molt novell i no veu els perills encara. ;-)

---

### Post by lo gambusí on 2008-08-05
ànims aleix!! ja voràs com te'n sortiràs!!

un altre de les colònies.. estic flipant xD

---

### Post by motor25 on 2008-08-06
jo tamble flipo per trobar gent de les colonies a part de tu que ja sabia que estaries aqui

---

### Post by motor25 on 2008-08-07
ho sento molt pero no ho puc provar cuant ho vaig intentar provar-ho no hem anava el ubuntu i despres l'he tingut que instalar de nou a ra veurem que pasa ara l'estic instalant

---

### Post by motor25 on 2008-08-07
no puc a més no se com fer el que em veu dir ja que no trobo la opcio d'afegir he intentat amb un altre pero tampoc em deixa ja que diu que la clau no es la correcte pero es la correcte perque la he copiat del roter
buno doneume alguna solucio siusplau
gracies

---

### Post by tanreb20 on 2008-08-07
Anims aleix! jajaja
(sóc el bernat.. laltre profe)


Jo estic tenint el mateix problema!!!!

He provat instalant el wicd i ni aixi

i ara el network-manager no rutlla com avans i fa molt el tonto!


No e sproblema del programa diria.. a mi em passa també que he de posar 34 cops la contrasenya pero ni aixi....

I a vegades es comnecta(bé... u feia avans) cuan volia i llavors anava bé pero ara ni aixo em fa!

---

### Post by jaume69 on 2008-08-07
No serà que teniu el Router mal configurat o algo així..

Jo entraria a la **web** del Router i em sembla hi ha una opció per restaurar-lo per defecte o fer (reset).

Sort!!.:)

_______________________________________

Jo amb **Gutsy** tenia aquest problema i ara amb **Hardy** ja es connecta directament.
Passa que,quan estic ja connectat no segueix buscant Wifis veïnes.

---

### Post by torracastanyes on 2008-08-08
Per tornar el router a la comfiguració per defecte, generalment, només cal pitjar el botó de reset, però aneu amb compte, perquè això desactiva totes les mesures de seguretat de la xarxa wifi.
Feu-ho només si esteu segurs que el sabeu tornar a comfigurar correctament.

---

### Post by jaume69 on 2008-08-09
[QUOTE="Torracastanyes"]Per tornar el router a la comfiguració per defecte, generalment, només cal pitjar el botó de reset, però aneu amb compte, perquè això desactiva totes les mesures de seguretat de la xarxa wifi.
Feu-ho només si esteu segurs que el sabeu tornar a comfigurar correctament. [/QUOTE]

Vols dir si hi poses contrasenya **WPA**,pot ser si t'esborra les dades,contrasenyes.
Però entran amb **WEB(ASCII)**,com jo entro,no et canvia la configuració,que és la de fàbrica.

Però tampoc sé si les altres companyies o routers ho fan,ja que jo no he probat instalar un altre router que no fos de la companyia,(Tel..ica)

---

### Post by torracastanyes on 2008-08-09
Efectivament, esborra qualsevol configuració que hagueu fet tú o qui va instal.lar la xarxa.

Evidentment, si utilitzes la configuració de fabrica no tindràs contrassenya ni password ni autenticació.

Alguns routers "de companyía" estan blocats només per a la companyia que els ven, però això no s'arregla amb el "reset", s'han de lliberar com els mobils.(No sé si et referíes a això).

---

### Post by motor25 on 2008-08-10
no es problema del roter ja que n'he tingut pero el eindows a mi em va i amb el ubuntu no pero un portatil que també tinc que es windows tampoc li va el wifi pero en el meu quan tinc cnectat el windows amb va i no se que li pasa en l'altre ordinador ni el que li pasa el ubuntu

---

### Post by torracastanyes on 2008-08-10
Per al portàtil, fas servir el mateix adaptador o porta wifi intern?

Abans et conectaves o no ha funcionat mai?

Em fa l'efecte que no sigui problema de l'adaptador ni de l'Ubuntu, sino que la xarxa està configurada amb alguna mena de restricció. Si saps qui la va instalar, pregunta'l-hi, i si va ser algú de la companyia, truca al servei tècnic (per al portàtil, si els parles de linux no en voldran saber res!) i que t'indiquin com l'has de configurar. Després, amb el que t'hagin dit configures l'Ubuntu.

---

### Post by motor25 on 2008-08-12
tranquils he pogut solucionar el problema era un errar del ubuntu ja que ell posaba un format de clau incorrecta 
gracies per a tot

---

### Post by papapep on 2008-08-12
Doncs estaria  bé que compartissis amb nosaltres la solució a fi de que si algú s'hi troba no hagi de començar de 0, oi? ;-)

---

### Post by motor25 on 2008-08-13
el errar era que em dectectava que era una clau wep normal i amb el windows es aixi  pero am el ubuntu es una clau wep ascii de 128 bites i em va anar també cal dir que aquest cop el ubuntu es instalat amb el cd oficial, ara mateix em detecta la clau com a wep hex de 128 pero ara mateix em va 
gracies per tot

---

### Post by papapep on 2008-08-13
Molt bé. Doncs apa, ara ja pots anar al capdamunt del fil a "Thread tools" i marcar l'opció "Mark this thread as solved" per donar el fil per resolt.

---


---
title: "Adaptador wifi USB [Era:novell wifi catlà]"
date: 2008-04-28
forum: Catalan Team
---

### Post by dani-blanes on 2008-04-28
Avui és el meu primer dia de Linux i m'he encallat només començar instal·lant l'adaptador USB per a wifi (el que va entregar-me Jazztel), instal·lant el router (comptrend) i configurant la xarxa per connectar-me a internet, impressores, disc multimèdia i altres PCs amb Windows. Probablement és molt obvi però no ho sé trobar. Algú em pot guiar?

A més he instal·lat la versió anglesa. Per passar a la catalana l'he de reinstal·lar de nou o bé puc afegir el "pegat" per passara a català.

gràcies

---

### Post by lo gambusí on 2008-04-28
Per canviar la llengua vés a Sistema/Administració/Suport d'idioma i allí tries català.;)

---

### Post by jmaspons on 2008-04-28
Per canviar a català segurament necessitaràs internet ja que et caldrà descarregar alguns paquets.

Així que millor que primer solucionem el tema de la connexió o provisionalment pots conectar-te amb cable.

Pel tema de l'usb mira si te'l reconeix. Ves a la consola i penja la sortida que et dona si li dius "lsusb".

Jo he provat algun adaptador wifi per usb i me'l reconeixia automàticament. Si és així tan sols cal que configuris la connexió amb el networkmanager.

Salut i benvingut a la comunitat!

---

### Post by patrickfromspain on 2008-04-28
Aplicacions -> Accesoris -> Terminal
i poses aixo:

cd
dmesg > dmesg.log
lsusb > lsusb.log

ara al teu home tindras 2 arxius, dmesg.log i lsusb.log. Fes-ne un zip y enganxan'l aqui

---

### Post by dani-blanes on 2008-04-29
Hola a tots,

gràcies per l'ajuda.

Ja vaig poder connectar-me. No havia trobat el botó de "connect", ja imaginava que devia ser quelcom d'obvi... ara el K-Torrent treballa a tota màquina.

Amb el tema de l'idioma no me n'he sortit encara...En el Kubuntu anglès no trobo el camí "Sistema/Administració/Suport d'idioma", fins a "System" hi arribo però no més...

Lo del...

cd
dmesg > dmesg.log
lsusb > lsusb.log

no ho entenc. Quina és la finalitat?

Ara tinc un nou problema: m'he baixat un parell de jocs infantils (tot això ho estic fent el l'ordinador del meu fill de 5 anys i l'he de compensar...) i em trobo un munt de carpetes i arxius on no identifico l'equivalent del "setup.exe" per instal·lar-los. Un cop més segur que és més obvi del que sembla però un cop de mà no m'anirà malament.

A part d'això, algú em pot recomanar un emulador de windows per fer-hi anar jocs?

salut!

---

### Post by papapep on 2008-04-29
Benvingut al fòrum Dani! (i encara una mica més per la proximitat geogràfica que tenim :-))

Una altra cosa, seria interessant _quan es tenen dubtes tan diferents intentar-los tractar en fils diferents_, ja que, sinó, es torna caótic el tema i la gent que ve al darrera li costa molt més  aprofitar el que ha fet altra gent abans per resoldre problemes semblants.
Sigui com sigui, sigues de nou benvingut, i quedes convidat a passar-te pel fil de benvinguda ([http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)) a fi de que ens expliquis una mica de la teva vida i miracles ;-)

Un Lloretenc adoptat.

---

### Post by jmaspons on 2008-04-29
Hola de nou,

Veig que ets kubuntaire. Si et poses l'etiqueta al perfil del fòrum serà més fàcil que et donem les solucions orientades al kde.

Per instal·lar l'idioma català cal que vagis a "System and settings", concretament a l'apartat Languages o similar (no recordo com era en anglès però hi ha dues bandaretes). Allà trobaràs l'opció que busques: Install new language.

---

### Post by jmaspons on 2008-04-29
Ui, veig que ja no es mostra la distribució que utilitza cada usuari. :(

Mal canvi. S'hi pot fer alguna cosa??

---

### Post by SnowTDM on 2008-05-06
Hola dani-blanes,

Jo també tinc problemes per a instal·lar la wifi de Jazztel, però a mi m'anava be amb la versió 7.10. Pots provar a arrencar l'ordinador amb el live CD de la 7.10?

També prova a fer "lsusb" amb la versió actual i poses el resultat aquí. Si resulta que tenim la mateixa tarja pots seguir el fil que he posat aquí:

[http://ubuntuforums.org/showthread.php?t=774774](http://ubuntuforums.org/showthread.php?t=774774)

Salutacions

---

### Post by pespin on 2008-05-06
> cd
dmesg > dmesg.log
lsusb > lsusb.log

no ho entenc. Quina és la finalitat?

Això mostra un llistat dels dispositius que el sistema reconeix i dóna informació sobre ells (programari, controladors, etc.)

> m'he baixat un parell de jocs infantils (tot això ho estic fent el l'ordinador del meu fill de 5 anys i l'he de compensar...) i em trobo un munt de carpetes i arxius on no identifico l'equivalent del "setup.exe" per instal·lar-los. Un cop més segur que és més obvi del que sembla però un cop de mà no m'anirà malament.

A part d'això, algú em pot recomanar un emulador de windows per fer-hi anar jocs?

l'Ubuntu està basat en debian, això entre altres coses vol dir que utilitza un sistema de paqueteria per a programes concreta, amb arxius ".deb".
 Aquests arxius fent doble-clic a sobre s'instal·len i ja estan llestos per funcionar. Pots trobar tots els paquets/programes disponibles per instal·lar (un munt i més) obrint l'eina "Adept" que trobaràs al menú.
Et recomano que et miris a l'Adept la categoria de jocs, ja que hi trobaràs moltíssims jocs per la canalla i la no tan canalla xD Molts jocs infantils/d'educació privatius de windows tenen programes similars lliures a GNU/Linux.

Si tot i així no trobes el que busques, el programa wine és l'emulador per windows que busques. El trobaràs també a l'Adept.

---


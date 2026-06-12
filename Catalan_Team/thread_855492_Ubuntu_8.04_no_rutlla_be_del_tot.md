---
title: "Ubuntu 8.04 no rutlla be del tot"
date: 2008-07-10
forum: Catalan Team
---

### Post by Turituri on 2008-07-10
Hola
He instalat el ubuntu 8.04 al meu pc i hi ha coses que no van massa be, per exemple no s'executa el Gestor de paquets synaptic, ni tampoc les proves de harware, i no se com solventar-ho.
En pricipi tinc el sistema actualitzat. Tampoc conseguiexo configurar els altaveus i no escolto res. per això volia descarreegar-me el alsa utils pero no em deixa executar el gestor de paquets synaptic, que puc fer, gracies

---

### Post by oriolsbd on 2008-07-11
Hola. Per obrir el Synaptic, en comptes de fer-ho des del menú obre un Terminal i escriu:
sudo synaptic

Així, si hi ha algun error et sortirà per pantalla.

Salut!

---

### Post by Turituri on 2008-07-13
Gracies aquest tema del synaptic ja el tinc solventat ara ja em deixa
perño en tic d'a'altres que no se solventar porto tot el dia d'avui provant i llegint coses per internet però sense exit. pricipalment son 3 coses
1ª, no soc  capaç de possar el firefox en català, si poso el ubuntu en català no tinc cap problema llavors, ja que m'ho fa sol, però si poso el ubuntu en castella llavors no se com cambiar el idioma del firefox a català. Tinc vaixat el complement d'idioma catala valencià, pero aquest es queda instalat a la pestanya estensions i no a la de llenguatges i no se com solventar-ho.
2ª al pc no hi ha manera de configurar el so. El meu pc te una Creative SB live, i no el deu detectar perquè he provat de anar tocant les configuracions del so i no hi ha manera de sentir res i tampoc se on mirar els dispositius per veure si ha detectat be la tarja o no.
3ª estic provat de compartir carpetes entre el pc que el tinc amb ubuntu i el portàtil que també el tinc amb ubuntu, tots dos la versio 8.04, el pc esta conectat per cable de red al router i el portàtil amb wifi. He creat una carpeta a cada ordinador amb noms diferents he activat les opcions per a compartir carpetes i s'ha instalat els programes necesaris que feien falta. també he baixat el samba, hi he configurat a tots dos una xarxa amb el mateix nom als dos ordinadors, ho he configurat tot tal i com he llegit a varis manuals , i inclús si vaig a xarxa arrivo a veure una xarxa amb el nom que jo he creat, pero tant al pc com al portàtil quan entro no hi veig res,i a les carpetes que comparteixo hi tinc arxius dins. La major part dels manuals que he trobat son per compartir arxius entre ubuntu i windows, però no trobo res per fer-ho amb dos ordinadors amb ubuntu. De moment avui ho deixo a veure si em podeu ajudar una mica i anar avançant. Gracies per tot.

---

### Post by orestesmas on 2008-07-13
No entenc això "del mateix nom als dos ordinadors". En una xarxa tots els ordinadors han de tenir noms diferents, altrament com podràs distingir-los?

EDITO: Ah, potser vols dir que has configurat un mateix grup de treball per als dos ordinadors...

D'altra banda, per compartir fitxers entre 2 màquines Ubuntu probablement és molt millor fer servir un protocol natiu de Unix, com ara NFS, que no pas usar el Samba. Llegeix una mica sobre NFS i, si decideixes usar-lo i no te'n surts amb la configuració (no és pas tan complicat), torna a preguntar.

---

### Post by Turituri on 2008-07-14
Hola, primer de tot donar-te les gracies per respondre.
Sobre lo de la xarxa he estat cercant informació sobre això de NFS, he trobat moltes coses pero no n'he tret l'aigua clara.
Tinc la versio 8.04 i no se quin paquet m'haig de descarregar. Si saps d'algun manual que pugui seguir pasam l'enllaç, tot el que he trobat no es correspon amb la meva situació. Explico la meva situació si et falta alguna dada m'ho dius.
Tinc 2 ordinadors tots 2 amb ubuntu 8.04.
Tinc un router de ya.com que va per ethernet(m'ho van canviar fa poc)
el pc esta conectat al router via cable i ho tinc configurat manualment així:
Direccio IP: 192.168.2.35
Mascara subred: 255.255.255.0
porta d'entrada: 192.168.2.1
i a la pantalla de DNS tinc això 192.168.2.1, ja que si posava les DNS que tenia a Windows(62.151.2.8 i 62.151.8.100), no em funciona, en canvi amb (192.168.2.1) si.
el portatil es concta via wifi, i la xarxa desde el primer dia la va detectar sola i només vaig posar la contrasenya i tal.
Si conecto el portatil via cable, tinc la mateixa configuracio que el pc canviant la Direccio Ip que hi tinc : 192.168.2.33, i també funciona be.

Dons amb aquestes dades no se com configurar-ho, si em podeu fer u cop de ma?. Gracies

---

### Post by Miquel Ubuntero on 2008-07-15
Hola TuriTuri!
Jo tambè tinc ya.com i recientment amb ethernet. Comentes que fas servir com ha Porta d'entrada 192.168.2.1 ; caldria que verifiquesis aquesta dada.
La porta d'entrada o GateWay ha de ser la mateixa IP del teu Routter. Tan en el actual domicili com el anterior, amb ya.com sempre he tingut la mateixa IP al Routter, la 192.168.1.1 (mira-ho per si de cas).

Tambè et comento que las DNS 62.151.2.8 i 62.151.8.100 les tinc configurades al Routter i tot hem funciona be. La xarxa amb DHCP.

Per acabar, jo de moment hem quedo amb Ubuntu 7.10 donat que amb 8.04 vaig tindre unes quantes incidencies. Esperare una mica abans de tornar a pujar de versió.

Be, no se si he ajudat gaire, si vols pregunta el que vulguis ;)

Sort!

---

### Post by srsiempre on 2008-08-03
Turituri,

curiosament m'he trobat els mateixos problemes al instal·lar ubuntu en un PC Antic. Per una banda la tarjeta de so Sound Blaster, i que no tot està traduït per defecte al català. Si descobreixo alguna cosa, la escric aquí.

:guitar:

---

### Post by CarlesOriol on 2008-08-03
srsiempre: El tema del català no cal repertir-lo a tots els fils. Si tens cap dubte crees un fil especific, però en qualsevol cas si haguessis cercat a d'altres missatges del fòrum veuries que el tema ja estava tractat i solucionat de fa temps.

Hi ha una norma bàsica del fòrum que és un tema per fil per evitar converses creuades.

Aquest cop et responc aquí però intenta no fer-ho més.

Comprova que no tinguis activada a placa base (a la bios) alguna altra targeta de so que estigui entrant en conflicte amb la targeta sound blaster.

---


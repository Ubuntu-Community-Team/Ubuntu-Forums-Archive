---
title: "[SOLVED] Problemes amb els Updates"
date: 2007-12-27
forum: Catalan Team
---

### Post by TotAmbA on 2007-12-27
Bona Tarda.
Fa un parell de dies que vaig formatar el pc on hi tenia l'Ubuntu per instal.lar-hi el Xubuntu. El motiu va ser que l'ubuntu començava a anar una mica lent amb el PII.
Doncs vaig baixar-me el Xubuntu 7.10 desktop i el vaig poder instal.lar sense problemes.
El problema ve alhora d'instal.lar updates tant per interficie gràfica com per terminal.
Un cop instal.lat el xubuntu, em va detectar que hi havia 60 actualitzacions i les vaig seleccionar totes per descarregar-les. 
Totes es va instal.lar correctament excepte una, que em dona constantment aquest error:

E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.46_i386.deb: el subprocés seqüència post-removal nova retornà el codi d'eixida d'error 9

i resulta, que si vull descarregar qualsevol programa amb el Synaptic em surt constantment aquest error. De totes maneres, el programa que desitjo descarregar s'instal.la correctament però al final de tot em surt l'error indicat.

El terminal no el domino gaire però he intentat fer:
apt-get update
apt-get upgrade
apt-get install -f

i no hi ha manera que s'instal.li aquest paquet.

Salutacions i les gràcies anticipades per perdre uns minuts llegint aquest post.

---

### Post by papapep on 2007-12-27
I quins missatges et mostren, de fer-ho, les tres ordres?

---

### Post by TotAmbA on 2007-12-28
Error amb  **apt-get update** i **apt-get upgrade**

E: no es pot resoltre el fitxer de blocat /VAR/lib/apt/lists/lock -open (13 permission denied)
E: No es pot blocar el directori de la llista

amb **apt-get install -f** em surt una parrafada que no se copiar-la ja que accedeixo al terminal amb CTRL+ALT+F1 perquè desde l'interficie gràfica em treu forçosament de la sessió quan intento iniciar-lo.

---

### Post by papapep on 2007-12-28
Quan obres un terminal al Gnome, se't tanca sense més si executes un "apt-get install -f"???

---

### Post by TotAmbA on 2007-12-28
M'he explicat malament. Desde XFCE no puc obrir el terminal. Quan vaig a "aplicacions>terminal", es posa la pantalla en negre com si intentes obrir el terminal en pantalla completa i finalment em tanca la sessió.
apt-get install -f l'executo accedint al terminal fent CTRL+ALT+F1

M'estic fent amb una altra iso, no fos cas que la que tinc fos corrupta.

---

### Post by jodufi on 2007-12-28
Abans de baixar una altra ISO, millor si comproves que la ISO que tens és corrupta.  Es pot comprovar fàcilment si una ISO és corrupta, aquí t'explico dues maneres:
[LIST=1]
[*]La primera manera, es calcular el md5 de la ISO i comprovar que correspon amb la que et proporciona la pàgina d'Ubuntu. Hi ha mols programes per a calcular el md5, o des d'un terminal fent "md5sum".
[*]L'altra manera és fer servir l'opció "comprovar d'integritat del CD", o alguna cosa per l'estil, que apareix en arrencar l'ordinador mitjançant el CD.
[/LIST]

---

### Post by papapep on 2007-12-28
TotAmbA: i si prems Alt+F2 i, un cop et surt el diàleg que et demana què vols executar, hi fiques "xfterm4" (sense cometes), tampoc s'obre el terminal?

---

### Post by TotAmbA on 2007-12-28
He fet més coses.
He canviat el disc dur de l'equip i he tornat a instal.lar xubuntu 7.10, una iso que he baixat aquesta tarda.
Instal.lació neta, he executat xfterm4 tal com m'has dit i fa el mateix, m'expulsa i em retorna a la pantalla usuari/contrasenya.

Ara vaig a veure si les actualitzacions s'instal.len correctament.

---

### Post by TotAmbA on 2007-12-28
He deixat que es descarreguessin totes les actualitzacions i s'han instal.lat correctament ( tema solucionat).
Després d'actualitzar-se completament he hagut de re-instal.lar el firefox perquè no s'executava. Un cop re-instal.lat, ha funcionat correctament ( tema solucionat)
El que no funciona és el terminal desde la XFCE, continua expulsant-me a l'inici de la sessió.

---

### Post by papapep on 2007-12-28
Aquesta tarda he instal·lat la Xubuntu 7.10 a una màquina Virtual Box i va perfecte, fins i tot el tema de l'emulador de terminal. És curiós això que et passa...
Buscaré a veure si hi ha antecedents.

---

### Post by TotAmbA on 2007-12-29
Jo he trobat això:

[http://www.ubuntu-es.org/index.php?q=node/51473](http://www.ubuntu-es.org/index.php?q=node/51473)
[http://rubensa.wordpress.com/2006/09/08/xubuntu-terminal/](http://rubensa.wordpress.com/2006/09/08/xubuntu-terminal/)

Lo bo, es que fa poc vaig instal.lar un xubuntu per fer proves en un altre equip que tinc en desús i funciona bé.

---

### Post by TotAmbA on 2007-12-29
**PROBLEMA SOLUCIONAT**

Buscant, buscant, sembla ser que hi ha un bug:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849)

Solució:

1.- Premem ALT+F2
2.- escrivim "xterm" (per executar el terminal)
3.- sudo su  (perqué ens deixi realitzar modificacions als fitxers)
4.- cd /etc/X11 (per localitzar el fitxer xorg.conf)
5.- Escrivim mousepad xorg.conf (que ens obrirà l'arxiu en l'editor)
6.- Busquem la linea on posa això:

Section “Screen”
Identifier “Default Screen”
Device “Intel Corporation 82810E DC-133 CGC

Monitor “Monitor genérico”
**DefaultDepth 24**
SubSection “Display”
Modes “1280×1024&#8243; “1024×768&#8243; “800×600&#8243; “720×400&#8243; “640×480&#8243;

7.- Modifiquem el DefaultDepth 24, per DefaultDepth 16.
8.- Tanquem l'editor Mousepad guardant els canvis
9.- Reiniciem l'equip (a mi m'ha fet falta) i llestos

Motius per fer aquesta modificació?
Sembla ser que el terminal no s'obre perqué la tarja de video no suporta 24bits, i canviant a 16 es soluciona el problema.

---

### Post by papapep on 2007-12-29
Enhorabona per haver trobat la sol·lució! T'ho has currat.

Ara només et falta marcar el fil com a "solved" ;-)

---

### Post by TotAmbA on 2007-12-29
Gràcies per l'ajuda, a veure si a algú li pot servir en un futur.

---


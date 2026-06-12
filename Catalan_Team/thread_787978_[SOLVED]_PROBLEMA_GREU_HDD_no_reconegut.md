---
title: "[SOLVED] PROBLEMA GREU: HDD no reconegut"
date: 2008-05-09
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-09
Bones,

amb aquesta magnifica pluja que cau avui m'han saltat els ploms de casa. El problema és que hi havia l'ordinador (i per tan l'HDD) encès. Pràctiment ni m'he n'he adonat. Però al tornar a engegar l'ordinador m'he trobat que el meu HDD tot i està encès no apareix a */media/disk* (la seva localització normal). Per ser exactes no apareix i no sé com trobar-lo. 

Em té preocupat. Són 32oGb de les quals 17o estàn en ús i en les que hi ha coses molt i molt importants (tan música com còpies *.pdf* de documents legals). A més a més no puc comprobar si està bé el HDD perquè l'Innombrable (aquell OS d'en Guillem Portes) no l'ha reconegut mai i per tan no m'hi puc posar i mirar-ho. 


Si us plau algú em pot ajudar!? 


Moltes gràcies, de debò.

---

### Post by papapep on 2008-05-09
Hem d'entendre que estàs parlant d'un disc extern USB?

---

### Post by LitusMayol on 2008-05-09
> **papapep said:**
> Hem d'entendre que estàs parlant d'un disc extern USB?

Si perdona, si si. És un disc extern connectat per USB alimentat a través de corrent (no per USB) MAXTOR.

---

### Post by papapep on 2008-05-09
El que primer hauries de saber és si el que s'ha mort és el disc, la placa que el controla dins la caixa o l'alimentador que connectes a la corrent.
Si tens, o algú et pot deixar, un multímetre (tester pels amics) pots verificar la tensió que arriba al connector que poses al disc. Si no el tens, doncs no. Independentment d'això, amb un live-CD podries intentar muntar el disc a veure si és accessible i fer còpia dels fitxers que et cal recuperar.

Sobretot, facis el que facis, és interessant no modificar el sistema de fitxers (no escriure-hi) de cara a una posterior recuperació de dades per passar-les a un disc nou i íntegre.

Per últim, si els documents que hi tens són "tan i tan importants", no en tens una còpia de seguretat???

---

### Post by LitusMayol on 2008-05-09
> El que primer hauries de saber és si el que s'ha mort és el disc, la placa que el controla dins la caixa o l'alimentador que connectes a la corrent.
Si tens, o algú et pot deixar, un multímetre (tester pels amics) pots verificar la tensió que arriba al connector que poses al disc. Si no el tens, doncs no. Independentment d'això, amb un live-CD podries intentar muntar el disc a veure si és accessible i fer còpia dels fitxers que et cal recuperar.

No hi ha *tester*. Per tan re. No sé muntar manualment. Vull dir que si poso la LiveCD no sabré que fer.

> 
Sobretot, facis el que facis, és interessant no modificar el sistema de fitxers (no escriure-hi) de cara a una posterior recuperació de dades per passar-les a un disc nou i íntegre.

Ja m'ho imaginava, però ho tindré en compte.

> 
Per últim, si els documents que hi tens són "tan i tan importants", no en tens una còpia de seguretat???

És que els originals ja els vaig perdre potinejant l'ordinador i aquests eren les còpies de seguretat... Ho sé: és molt "*cafre*" no haver-ne fet la còpia de nou.

---

### Post by papapep on 2008-05-09
Doncs si no saps muntar manualment tens dues opcions: o n'aprens, que no és res de l'altre món o algú que en sap t'ajuda. Simple.
Si vols potser serà més fàcil fer-ho per irc, donat que és més àgil que aquí.

Probablement a aquesta hora i dia de la setmana hi hagi algun pardal voltant per allà. Jo ara hi sóc, si vols ja saps.

---

### Post by LitusMayol on 2008-05-09
AAAhhh...Sóc un autèntic novell. 

No sé exactament que és l'IRC i no el sé fer anar... :(

---

### Post by CarlesOriol on 2008-05-10
Mira: [https://wiki.ubuntu.com/CatalanTeam/IRC](https://wiki.ubuntu.com/CatalanTeam/IRC) a més s'explica com usar el wiki al kopette.

Jo uso **xchat** i algun cop **xchat-gnome** però quan vegis com va a les instruccions del kopette ja veuras més o menys com configurar qualsevol altre programa d'irc.

---

### Post by LitusMayol on 2008-05-10
Per cert,

el disc dur dóna senyals de vida en tan que el LED funciona normalment i fa soroll de girar.

Per si serveix a trobar alguna coseta...

merci :'(

---

### Post by LitusMayol on 2008-08-28
Mesos després...

Segueixo preocupat pel meu disc dur extern. El tinc en coma a l'habitació esperant la cura final.

El vaig portar a una informàtica(si si UNA) i em va dir que hi havia un 80% de possibilitats de recuperar les dades (està clar, pagant 180&#8364;, el disc em va costar 120&#8364;. No sé si em val la pena...). Em va dir que el problema no era físic sinó electrònic, era que s'havien... canviat els camins? Tenia els camins corruptes?(*mecatxis*...!). Ara no m'enrecordo del nom. Ve a ser, que tan el disc en sí com l'elèctrònica funcionen, però que no estan ben conectats entre ells (no físicament, sinó electrònicament).


[LIST=1]
[*]**Algú sap com "refer els camins"?**: aleshores m'estalvio el pas 2.
[*]**[RIPLinux]("http://www.somgnu.cat/riplinux-25/") em pot servir?** L'altre dia llegint per [Somgnu]("http://www.somgnu.cat"), vaig buscar algun article que no hagués llegit. I va i hi trobo [això]("http://www.somgnu.cat/recuperacio-de-dades-a-gnulinux/"). No sé si em serveix, perquè el meu HDD no tenia el GNU/Linux instal·lat: era un disc dur extern típic i tòpic.
[/LIST]


Per probar...!

---

### Post by Curial on 2008-08-28
Idea via hardware:

No se si et servirà això que et diré ni tampoc si és viable a l'hora de fer-ho però:

Has pensat a comprar-te el mateix model i intercanviar el disc dur?
Si hi ha avaria provablement la tinguis a part electrònica que governa el disc, no en el disc en si.

Tanmateix em sembla que existeixen unes "caixes" que serveixen per connectar un disc dur i poder-lo fer servir de disc extern via usb.(no se si són cares). Fa poc que n'he sentit a parlar.

Salut.

---

### Post by patrickfromspain on 2008-08-28
has provat a treure el disc dur fisic que hi ha dins la caixa i connectar-lo directament a un pc?

Jo treballo en una tenda de pcs i quan ens ve un client amb un disc dur extern petat el que fem, si la garantia del catxarro li es igual, treure el disc dur de la caixa externa i mirar si podem accedir al disc des de un pc normal i correct, connectanlo directament al canal IDE o SATA. Hi ha varies possibilitats:

- Al connectar-lo per IDE o SATA la BIOS no el reconeix, només queda una possibilitat: empresa de recuperacio de dades, que val molts $$$$$.
- La BIOS el reconeix, pero windows diu que no te format. Provem algun programa com el file recovery pro i si no va: empresa de recuperacio de dades $$$.
- El connectes, el detecta i s'hi pot accedir. Si el disc dur funciona correctament, capsa nova i a correr. Si el disc dur fa sorollets, volquem les dades a un HDD nou i ho montem tot en una caixa nova.
- El connectes i el detecta. Te errors en el sistema de fitxers, windows els repara i funciona. Caixa nova i a correr.

Sigui com sigui: canviat els camins? Que co__ons es aixo? A mi me huele a timo, 180&#8364; son moltissimes hores de feina, tenin en comptre que segons ella tant la caixa com el disc estan be.

Salut

---

### Post by LitusMayol on 2008-08-28
> **patrickfromspain said:**
> Sigui com sigui: canviat els camins? Que co__ons es aixo? A mi me huele a timo, 180€ son moltissimes hores de feina, tenin en comptre que segons ella tant la caixa com el disc estan be.


Gràcies **patrickfromspain**! necessitava sentir-ho. Jo també ho vaig pensar i de fet per això no ho he fet. ;) Probaré de conectar-lo directament al PC a veure que...

---

### Post by patrickfromspain on 2008-08-28
> **Curial said:**
> Idea via hardware:

No se si et servirà això que et diré ni tampoc si és viable a l'hora de fer-ho però:

Has pensat a comprar-te el mateix model i intercanviar el disc dur?
Si hi ha avaria provablement la tinguis a part electrònica que governa el disc, no en el disc en si.

Tanmateix em sembla que existeixen unes "caixes" que serveixen per connectar un disc dur i poder-lo fer servir de disc extern via usb.(no se si són cares). Fa poc que n'he sentit a parlar.

Salut.

Es que precisament, TOTS els disc durs extern son una caixa on s'hi connecta un disc dur normal i corrent. Vindrien a ser totes un conversor IDE/SATA a USB.

De fet, no cal ni buscar el mateix model, ja que en principi aquestes caixes no fan servir cap sistema especial ni res: NTFS estandar, normal i corrent. O inclus FAT32. N'he vist unes quantes i de marques diferents i mai he tingut problemes per intercanviar una caixa per una altra.

---

### Post by patrickfromspain on 2008-08-28
Litus, important: abans de connectar res internament al pc, cal que aquest estigui completament apagat si i esta sense alimentacio, molt millor.

M'imagino que ja ho sabies, però t'ho dic perque ha passat algun cop que algu ha intentat un hot-plug amb un HDD IDE i.. pof

---

### Post by LitusMayol on 2008-10-12
Brutaaaaaaaaaaaaaaaaaaal!!!

Ara mateix estava trastejant per aquí l'ordinador. Penjant algun post, tancant algun fil, mirant el correu... I de cop he dit, proba l'HDD mort...

Com per art de màgia. S'ha engegat i aquest ordinador (diferent de on havia "mort") l'ha reconegut sense cap problemaa!!! Fantàstic!!! Al cap de sis mesos ell sol ha resucitat! ue uee!


Ho sento necessitava dir-ho. No podeu imaginar-vos que exaltat que estic!

---


---
title: "Migrant a hardy, encallat a &quot;ca-ES.UTF-8&quot; i estavellat a !queuelen' failed"
date: 2008-08-22
forum: Catalan Team
---

### Post by lpargemi on 2008-08-22
Finalment he convençut a l'Eva de migrar la versió gutsy del seu portàtil a hardy, que és LTS, i a ella que li va bé una cosa estable li ha d'anar millor. Quan s'estava acabant el procés va i apareix un problema amb els locale, i es queda penjat així:

```
ca-ES.UTF-8...
```

Busco al fòrum i a tot arreu, i sembla que l'opció més recomanable és fer, des del terminal quan torno a engegar la màquina. 

```
dpkg --configure -a
```

I es torna a encallar allà mateix. Segueixo mirant i veig per aquests fòrums que caldria arrencar el darrer nucli que anava i fer el mateix. Els gràfics del nucli anterior ja no van, però des de l'usuari root a l'arrencada d'emergència si que es pot. Hi torno. Supero els locale... i es para amb enigmàtic missatge: 

```
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.

```
I no en surto més. Miro als fòrums, com per exemple aquest que recomana en manelfus

[http://ubuntuforums.org/showthread.php?t=865679]("http://ubuntuforums.org/showthread.php?t=865679")

i res. Buscant arribo a aquest altre, que va pel mateix camí, i en Pumalite diu que nasti de plasti, que no ell no té solució per aquest problema.

[http://ubuntuforums.org/showthread.php?t=868274]("http://ubuntuforums.org/showthread.php?t=868274")

Igual que la víctima no m'ho vull creure i provo tota mena de conjurs: dpkg, apt-get, aptitude i qualsevol cosa que trobo, però en Pumalite deu tenir raó. Sembla ser que la base de dependències està fulminada, i no hi ha manera.

Finalment engego una instal·lació des d'un live CD. Resulta que des del live CD, com que no vull formatar, puc restaurar l'usuari que ja hi ha. I s'instal.la tot més o menys bé, recuperant sense fer res més les dades, i els correus, i tot el què hi ha, a falta d'algunes cosetes menors. Enlloc de les dues horetes previstes pel canvi n'han estat sis o set... però un, dos, tres salve!

El comentari de l'Eva quan va arribar al vespre: Vaja veig que això segueix igual de malament que sempre: no pots llançar-t'hi sense ningú que et doni suport directe... i té raó. Com pot ser que un paquet de llenguatge mal instal.lat doni tants problemes? No es podria tenir una opció de saltar-lo i endavant?

Bé us foto el rotllo per si algú pot orientar a qui vingui al darrera del què no he fet bé, i si la caga com jo, d'una possible solució.

Salut

Lluís

---

### Post by papapep on 2008-08-22
El problema és que ens has explicat què has fet un cop tenieu l'error, però no tenim la més menor idea de què el pot haver causat. Sense això, és molt complicat poder emetre cap valoració.
La base de dades de paquets, si realment és aquest el problema, pot trencar-se per ben poques coses (en els anys que porto remenant Linux mai m'ha passat que no es pogués recuperar), i la majoria són problemes de maquinari: disc dur, RAM, fluctuacions del fluït elèctric, talls de connexió en moments crítics, etc.

També és cert, que el tema de les actualitzacions és un dels temes que sembla que més problemes porta en les últimes versions d'Ubuntu (tot i que, novament, mai he tingut cap problema gran a cap dels ordinadors que administro).

En conclusió, que és difícil de dir, però que sí, que encara fa falta algú amb recursos a vegades pel Linux.
En contraposició, i com a resposta a aquesta última qüestió que t'ha comentat l'Eva (parles d'ella com si la coneguéssim, però jo no tinc el plaer :-D), quan un ordinador amb Windows té problemes la solució més habitual és reinstal·lar, ja que jo no conec ningú que tingui coneixements de "baix nivell" ni cap comunitat decent a on recòrrer quan un sistema amb aquest OS peta, o es farceix de virus o, símplement, surt per peteneres.

---

### Post by papapep on 2008-08-22
Ja que estem en el tema, quan fas el "sudo dpkg --configure -a" quins són els missatges que mostra? no només el final.

---

### Post by lpargemi on 2008-08-22
[QUOTE papapep] El problema és que ens has explicat què has fet un cop tenieu l'error, però no tenim la més menor idea de què el pot haver causat. Sense això, és molt complicat poder emetre cap valoració.[/QUOTE]

Tens raó, però el problema és que quan et passa difícilment saps què has fet per mereixer-ho. Buscant per resoldre-ho (he afegit alguns fils, però en vaig visitar molts més) he vist que és una errada si no comuna almenys recorrent. I que a més gent se li ha quedat tirat al mateix punt. La sort és que des d'un live cd es pot recuperar gairebé tot. L'objecte del post també era una mica aquest: si a algú li passa que sàpiga que l'opció de reinstal.lar enlloc de gastar hores intentant reconstruir les dades funciona prou bé.

[QUOTE papapep]l'Eva (parles d'ella com si la coneguéssim, però jo no tinc el plaer )[/QUOTE]

L'Eva és la meva dona, que estudia a la UOC. Es va comprar un portàtil per fer els cursos, i va venir amb Vista. Gràcies a això va caure pel seu propi pes passar-se a Linux. Com a usuària li va molt bé, però quan cal renovar programes, o instal.lar una impresora, etc ja no tant. D'aquí el seu comentari.

Salut i gràcies per la paciència.

Lluís

---

### Post by papapep on 2008-08-22
> L'objecte del post també era una mica aquest: si a algú li passa que sàpiga que l'opció de reinstal.lar enlloc de gastar hores intentant reconstruir les dades funciona prou bé.

Entenc per què ho dius, però, ho sento, no puc estar més en desacord.

Si la comunitat, o sigui nosaltres, no ajuda a resoldre els problemes, identificar-los i eliminar-los, això no millorarà mai. Entenc que hi ha casos puntuals per necessitat personal, urgències, etc, on s'ha de tirar pel dret, però si sempre féssim així mai s'arreglaria res i el programari no milloraria, _i mai de la vida seriem on som_. I, evidentment, "des-recomano" fervorosament la reinstal·lació com a solució fàcil i ràpida.

Espero haver-me sapigut explicar ;-)

---

### Post by lpargemi on 2008-08-22
> **papapep said:**
> Ja que estem en el tema, quan fas el "sudo dpkg --configure -a" quins són els missatges que mostra? no només el final.

Els missatges que surten son els que us he enganxat, però no tinc la ristra completa, seria similar a:  

```
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-games:
gnome-games depends on python-gtk2 (>= 2.10.0); however:
Package python-gtk2 is not configured yet.
dpkg: error processing gnome-games (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
python-gnome2-desktop depends on python-gtk2; however:
Package python-gtk2 is not configured yet.
python-gnome2-desktop depends on python2.4-gtk2; however:
Package python2.4-gtk2 is not installed.
Package python-gtk2 which provides python2.4-gtk2 is not configured yet.
python-gnome2-desktop depends on python2.5-gtk2; however:
Package python2.5-gtk2 is not installed.
Package python-gtk2 which provides python2.5-gtk2 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
fast-user-switch-applet depends on gnome-panel; however:
Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-vte:
python-vte depends on python-gtk2; however:
Package python-gtk2 is not configured yet.
dpkg: error processing python-vte (--configure):
dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)
```

Compte! que no és el meu cas exacte, els missatges que sortien eren similars a aquests (i el trec d'un dels fils visitats) però no vaig pensar en fer-los escriure en cap fitxer.

Agraït

Lluís

---

### Post by lpargemi on 2008-08-22
> **papapep said:**
> Entenc per què ho dius, però, ho sento, no puc estar més en desacord.

Si la comunitat, o sigui nosaltres, no ajuda a resoldre els problemes, identificar-los i eliminar-los, això no millorarà mai. Entenc que hi ha casos puntuals per necessitat personal, urgències, etc, on s'ha de tirar pel dret, però si sempre féssim així mai s'arreglaria res i el programari no milloraria, _i mai de la vida seriem on som_. I, evidentment, "des-recomano" fervorosament la reinstal·lació com a solució fàcil i ràpida.

Espero haver-me sapigut explicar ;-)

Anem a contrapeu! (en l'ordre dels posts).

Tens raó, però hi ha vegades que cal tirar endavant com sigui; o que almenys t'ho sembla. Després mirant-ho de més lluny tens raó tu.

lluís

---

### Post by papapep on 2008-08-22
Ah, pensava que encara no havies reinstal·lat de fet. Doncs res.

I sí, ja he dit que hi ha casos puntuals on cal fer el que sigui, però el problema és en plantejar-ho com una bona "solució". Això no.

Apa, ja ens hem entès. :-)

---

### Post by patrickfromspain on 2008-08-23
MIra que diuen aqui [http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/the-painful-upgrade](http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/the-painful-upgrade)

> 
So in the middle of the night I decided to get fetch my other laptop. Fortunately traffic was light at 02:00 so 30 minutes later I found some similar problems which where fixed by removing:

rm /usr/local/lib/libz.so.1*
ldconfig

From now on there was no more core dump in dpkg but I still needed to purge, reinstall a few packages by hand in order for the apt-get upgrade and apt-get dist-upgrade to finish installing and configuring the packages.


Aqui [http://blogaddins.blogspot.com/2008/08/ubuntu-upgrade-from-710-to-804-hardy.html](http://blogaddins.blogspot.com/2008/08/ubuntu-upgrade-from-710-to-804-hardy.html) sembla que tambe hi han trovat solucio

---

### Post by lpargemi on 2008-08-24
Bé, és una possibilitat. El primer post no el vaig saber trobar, però quan parla d'instal.lar a mà uns poc paquets a mi m'hagués deixat ben fotut... no tinc ni remota idea de quins son els paquets principals que em permetrien remuntar la situació. A l'ordinador en qüestió n'hi ha més de 1000 instal.lats.

La segona solució si que la vaig trobar documentada a més d'un lloc, però malauradament no va funcionar.

Agraït

lluís

---


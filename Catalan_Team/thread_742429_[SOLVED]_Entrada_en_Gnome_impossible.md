---
title: "[SOLVED] Entrada en Gnome impossible"
date: 2008-04-01
forum: Catalan Team
---

### Post by Druiling on 2008-04-01
Hola tothom,
M'he carregat l'entrada en Gnome. M'explico. Vaig estar enredant amb xorrades d'aquestes d'efectes de pantalla (pantalles tremoloses, la barreta que imita apple, etc) i no sé què he fet que (i porto ja quatre dies així i funcionant amb kde i amb windows) que abans podia entrar a la sessió de gnome i, encara que amb una configuració que em donava la una visió de com si tingués les coses enganxades a la retina de tan grosses, però podia anar mirant si trobava què havia configurat malament. 
Aquesta tarda, he reinstal.lat tot el tema aquell del compiz i el xorg perquè he llegit en algun fil que a algú li ha passat alguna cosa semblant i ara al final, reinicio amb l'esperança de poder seguir mirant i remirant i em trobo que entro en una pantalla com de màtrix però en línies que es mouen avall i que haig de parar a lo burro ja que no veig res. He reiniciat en kde i perfecte, però jo vull el meu gnomeeeeeeee.
Estic farta de windows!
No, ara de debó, a algú se li acut què puc haver destrossat?
Moltes gràcies a tots.:confused:

---

### Post by niculau on 2008-04-01
jo en els meus inicis amb ubuntu vaig estar trastejant molt amb l'acceleració 3D i vaig cometre molts errors, al final vaig trobar una solució possible per arreglar aquelles desfetes, recomanen guardar una copia del xorg original i substituir-lo, en cas de no tenir-lo el pots crear arrencant des de el livecd i substituir el xorg generat pel livecd que serà el bo.

salut

---

### Post by Druiling on 2008-04-01
> **niculau said:**
> jo en els meus inicis amb ubuntu vaig estar trastejant molt amb l'acceleració 3D i vaig cometre molts errors, al final vaig trobar una solució possible per arreglar aquelles desfetes, recomanen guardar una copia del xorg original i substituir-lo, en cas de no tenir-lo el pots crear arrencant des de el livecd i substituir el xorg generat pel livecd que serà el bo.

salut

D'acord niculau però exàctament com ho faig això, substituir el xorg generat pel del live?

Gràcies

---

### Post by niculau on 2008-04-01
perdona si he trigat molt a contestar, però estava iniciant amb el live per comprovar-ho.

inicies amb el live. Desde el terminal engeges el nautilus com a root 

 "sudo nautilus"

ves a   sistema de fitxers/etc/X11

copies l'arxiu xorg.conf   (aquest es el generat pel live)

ves a la partició (volum) on tens instal·lat l'ubuntu i substitueixes en la mateixa adreça etc/X11 l'arxiu abans copiat.

espero que et funcioni.

---

### Post by Druiling on 2008-04-02
No t'hi amoïnis.
Gràcies pel teu esforç. Aquest vespre ho provo.

---

### Post by CarlesOriol on 2008-04-02
espera... atura el carro... que si et va el kde no crec que sigui el xorg.

Fes una prova. engega amb gnome  i fas alt+f2 -> metacity --replace

i ens expliques si pots funcionar sense efectes xulos.

---

### Post by niculau on 2008-04-02
ups!!!! L'he cagat?

en qualsevol cas no crec que substituint-lo s'espatlles més.

---

### Post by Druiling on 2008-04-02
> **niculau said:**
> ups!!!! L'he cagat?

en qualsevol cas no crec que substituint-lo s'espatlles més.

Tranqui niculau que no he fet res encara. Provo això que diu en Carles i us comento.
Gràcies.

---

### Post by Druiling on 2008-04-02
Boneees.
Què va, no hi ha manera, i no la hi ha perquè no sóc capaç de veure res de res. He entrat normal, en mode a prova d'errors i tampoc no veig res, sols la pantalla tota plena de ratlles en tots dos. He entrat en recovery mode també i aquí em diu el següent, on em quedo clavada:
unable to open X display 
Se us acut res més abans de tocar el live que llavors si que no responc de mi mateixa? Ai quina creu...](*,)

---

### Post by niculau on 2008-04-02
al final has provat això de substituir el xorg? perquè si et diu que no pot iniciar el X display... potser el kubuntu no es només l'escriptori, potser es tot el kubuntu instal·lat en un altre partició?

---

### Post by Druiling on 2008-04-03
Bon dia, no ho he provat encara, però em sembla que serà el proper que faré aquest vespre. 
Ja us dic alguna cosa.
Moltes gràcies per tot!

---

### Post by Druiling on 2008-04-11
Hola tots,
Com que no vull atabalar i un cop amb el live posat no entenc ben bé què haig de fer (dic rollo com els nens petits, per passes), les estonetes que tinc les dedico a buscar informació perquè m'oloro que amb la poqueta cosa que sé, m'ho carregaré tot i no ho voldria.
Per tant, sols vull que, niculau, no et pensis que he passat de tot, que no.
Ja us aniré dient què.

Bon cap de setmana a tothom.


PD: enyoro el meu gnome...uuuuuuuuuuu:(

---

### Post by niculau on 2008-04-12
Es més fàcil que no et penses, intentaré explicar-ho millor.

---

### Post by niculau on 2008-04-12
> **Druiling said:**
> Hola tots,
 un cop amb el live posat no entenc ben bé què haig de fer :(



El que et passa es que tens l'arxiu xorg.conf malament. Doncs farem servir el livecd de ubuntu, perquè quan arrenqui, crearà el seu propi xorg depenent del hardware del teu ordinador
Un cop arrencat el live, anem a buscar el xorg generat pel live, que esta situat en "sistema de fitxers" dins de la carpeta "etc/x11" i el copies.
Ja tenim el xorg bo, ara l'únic que has de fer es anar a buscar el xorg de la instal·lació i substituir-lo, enganxant l'arxiu.

PD: Ara llegint-ho no sembla que ho hagi explicat millor,

---

### Post by Druiling on 2008-04-14
Si, perdona la tardança de la resposta però és que ara mateix vaig fatal de temps.
Sols una cosa, interpreto que un cop generat el xorg pel live, haig de llançar un terminal i buscar el xorg que tinc jo i substituir-lo?
És així o no ho he entès?

Bona nit i gràcies.

---

### Post by papapep on 2008-04-14
Ho has entès bé. Un cop tinguis la live funcionant, has de muntar el disc dur on tens instal·lat l'ubuntu i substituïr el xorg.conf que hi tens amb el del live-cd.

---

### Post by Druiling on 2008-04-14
Bones,

> **papapep said:**
> Ho has entès bé. Un cop tinguis la live funcionant, **has de muntar el disc dur on tens instal·lat l'ubuntu** i substituïr el xorg.conf que hi tens amb el del live-cd.

Ho provaré així que pugui. Què pot passar? Que em peti tot? jajajaja
Gràcies i bona nit.

---

### Post by papapep on 2008-04-14
....home, doncs l'objectiu primari és que no quedi pitjor del que ja ho tens :-)
Si tens qualsevol dubte de com fer-ho no t'estiguis de preguntar. Nosaltres donem, sovint, molt per suposat ;-)

---

### Post by patrickfromspain on 2008-04-15
una altra opcio es moure l'xorg.conf que ja tens i crear-ne un de nou amb sudo dpkg-reconfigure xserver-xorg.

---

### Post by Druiling on 2008-04-15
Hola,
He fet això, però m'he trobat amb tot el "mogollón" que us poso en una captura que he fet en kde.
M'he quedat despistada creient que només n'hi hauria un de xorg i no hi he fet res per por a carregar-m'ho.
Com segueixo, nois?
Gràcies.

PD: Quan dieu moure és esborrar?

---

### Post by papapep on 2008-04-15
Tots els que es diuen xorg.conf.x (essent x un número) són antigues versions que es conserven com a còpies de seguretat. Aleshores, assumint que la imatge que ens has penjat és del disc destí, cal que substitueixis el xorg.conf (sense res més al darrera) amb el que tinguis funcionant correctament (amb el mateix nom) al sistema live.

---

### Post by Druiling on 2008-04-15
Vols dir que l'esborri i que enganxi el del live?, i tot aquest fotimer de xorgs que em surten? s'han d'esborrar o els deixo? 
Ho he mirat a l'ordinador d'un col·lega fa una estona i ell sols en té un. Perquè en dec tenir tants?:-k

---

### Post by niculau on 2008-04-15
tens tants per la quantitat de proves que has fet. Enganxa el del live i veuràs que bé

---

### Post by Druiling on 2008-04-15
Ah, d'acord.
Així esborro aquestes proves que dius i el xorg que tinc i enganxo el del live.
Ok

---

### Post by patrickfromspain on 2008-04-15
mm per cert, que ja no hi pensava. Ja estem segurs de que l'xorg.conf hi te alguna culpa si a KDE pot entrar??

---

### Post by niculau on 2008-04-15
> **niculau said:**
> al final has provat això de substituir el xorg? perquè si et diu que no pot iniciar el X display... potser el kubuntu no es només l'escriptori, potser es tot el kubuntu instal·lat en un altre partició?

si, encara estàvem esperant la resposta.

---

### Post by Druiling on 2008-04-15
Hola, 
estic ara mateix en live intentant aix[o de substituir el xorg i la veritat 'es que no puc.
ni esborra res, ni em deixa fer res. He intentat fer/ho copiant el que hi ha a l-interior i enganxant/ho en el del disc per[o em diu que no tinc permisos.
Miro de passar una captura.

PD>
He notat que hi ha moltes difer[encies en les l'inies d-un i d-altre, podria editar/les directament a m[a_ esborrar i escriure_
Dispenseu el circ que estic muntant amb el teclat!!

Gr[acies.

---

### Post by papapep on 2008-04-15
En un terminal:

```
sudo cp /etc/X11/xorg.conf /media/disk/etc/X11/xorg.conf
```

i ja ho tindràs fet.

---

### Post by Druiling on 2008-04-15
No em fa res. que no faig be_

---

### Post by papapep on 2008-04-15
Tu saps allò que diu: "l'absència de notícies és bona notícia"? :-D

En aquest cas, la manca de missatge significa que ho ha fet. Ara hauries de provar a reiniciar l'ordinador (sense el cd posat, clar)

---

### Post by Druiling on 2008-04-15
Ah.
vale voy pall'a

---

### Post by Druiling on 2008-04-15
Bé, us informo que dec tenir un mal karma o algo semblant. M'he quedat condemnada a windows.
El tema és que ara ja no fa ratlles, prova d'entrar, em demana l'usuari i la contrasenya, tot bé, quan pensava que ja estava solucionat, es queda una estona pensant, amb el cursor i la pantalla en el color aquell salmó de l'ubuntu i em torna a la pantalla de la clau i la contrasenya. Intento en kde i em passa exactament igual.
Sóc al dia de la marmota en linux ara mateix.
Suposo que s'ha arreglat alguna cosa, però hi deu haver alguna altra que no pita.
Suggerències?
Us espero en el llimb de windows...
Gràcies i si no és avui, bona nit companys.

---

### Post by papapep on 2008-04-15
Vaja, vaja, quina aventura aquesta teva amb les X's.... :-)

A veure, a veure....primer hauriem de matar el servidor de les X's i arrencar-lo des d'un terminal per veure quin missatge d'error ens dóna:

En un terminal (en un de real, no en un emulador: ves-hi amb Ctrl+Alt+F1, per exemple):

```
ps -e|grep Xorg
```

Això et mostrarà un número, per exemple en el meu cas:

```
 5186 tty7     00:57:34 Xorg

```

Després fas:

```
sudo kill -9 5186
```
Substituint el 5186 pel teu número, clar.

(de fet podries para el servidor amb "sudo /etc/init.d/Xnoséqué stop", però mira, m'ha picat per aquí perquè no recordo quin és el nom del dimoni i ara em fa mandra buscar-ho :-))

un cop fet això, si tornes al terminal virtual 7 (CTrl+Alt+F7) ja no hauries de tenir la pantalla gràfica d'entrada a l'Ubuntu.

Ara executa manualment l'entorn gràfic. Des del terminal 7 mateix::

```
startx
```

I a veure on es queixa.

EDITO: Fent a un terminal "sudo /etc/init.d/gdm stop" també te l'hauria d'aturar (d'una manera un pèl més civilitzada :-D)

---

### Post by Druiling on 2008-04-15
Holaaa,
Tot bé fins al moment de fer Ctrl+Alt+F7 (tot i que encara tenia la pantalla gràfica), que ha passat de tot i no ha fet res. Així que he tornat a fer Ctrl+Alt+F1 altre cop i m'ha tornat a llençar la primera pantalla, li he posat startx i m'ha dit coses molt lletges, entre les que s'entenien "if this server is no longer running, remove /tmp/ .x0 -lock" and start again, però com que no sabia si faria bé de fer-lo el remove aquest, doncs no ho he fet.
Que us sembla? l'he mort?
Bona nit!

---

### Post by papapep on 2008-04-15
hhehehe, no , no l'has mort. Fes el sudo /etc/init.d/gdm stop :-) i torna a provar l'startx. T'ha dit que ja en tenies un de funcionant i que no pensa executar-ne un altre.

---

### Post by CarlesOriol on 2008-04-16
Druiling:

Esperem veure't el dissabte 26 a Caldes... ja veuras com en un moment ho tenim tot arreglat. (i si no ho arreglem com a mínim plorarem tots junts)

---

### Post by Druiling on 2008-04-16
En principi tenia previst de venir (i em funcionava bé, eh)!!
De fet ja us vaig amenaçar en el post corresponent, jajaja.

PD. Ara mateix no estic a la meva màquina. A veure si després puc fer això que diu en Josep.

Salutacions.

---

### Post by Druiling on 2008-04-16
Bones, he fet això:

> **papapep said:**
> Fes el sudo /etc/init.d/gdm stop :-) i torna a provar l'startx. T'ha dit que ja en tenies un de funcionant i que no pensa executar-ne un altre.

I el molt desagraït m'ha dit això:

**waiting for x server to shut down FreeFrontPath:  FPE "/usr/share/fonts/X11/ misc" refcount is 2, should be 1; fixing**

Abans d'això però, s'ha estat una estoneta, uns 20 segons amb una pantalla molt puntejada amb aquella X de cursor, després tirava una tirallonga de coses i això que he posat.

Ah i em tornava a posar l'entrada del sudo.

Allò d'ahir ho vaig entendre una mica, això ja no. Estem en les vostres mans, gurus!:frown:

Salut!

---

### Post by niculau on 2008-04-16
Jo, com haureu notat m'he retirat discretament:-\"

---

### Post by Druiling on 2008-04-16
Gràcies igualment, has fet el que has pogut!

> **niculau said:**
> Jo, com haureu notat m'he retirat discretament:-\"

Ens veiem el 26 a Caldes dels lleons?

Salut!

---

### Post by CarlesOriol on 2008-04-17
Uf... Aquest fil és molt llarg i costa seguir el fil de tot el que s'ha fet.

Has provat el sudo dpkg-reconfigure xserver-xorg ?

---

### Post by Druiling on 2008-04-17
Hola no, no ho he provat, crec.
A veure si demà m'hi poso i si no funciona ho deixem pel 26, si voleu. És veritat que això ja s'allarga molt. Comprenc que és un pal. En qualsevol cas, gràcies.
Salut!

---

### Post by patrickfromspain on 2008-04-19
Proba el següent:

ctrl+alt+F1 (per estar en mode consola)
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.copia
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg

```

A partir d'ara t'anirà fent preguntes. Has de saber que si tens una ati, el driver que has de posar ha de ser ati (lógic no? xD) i si tens una nvidia, l'nv (no posis l'nvidia encara que el tinguis).

Quan et pregunti per memoria de la grafica, no hi posis res i posa endavant. Vaja, aixi amb tot: deixa sempre el que hi ha per defecte, fins que arribes a un punt on et pregunti pel  monitor i et donara 3 opcions: Simple, medium i advanced (em sembla). Diferencies:

Si poses simple, et preguntara la mida del monitor i ell s'ho fara sol posant la resolucio que calgui i tot aixo. M'ha donat problemes amb monitors panoramics, per tant no t'ho aconsello.
Si poses medium em sembla que et pregunta freqüència horitzontal i vertical (deixa les que venen per defecte) i la resolució del monitor. Agafa aquesta opció. Si et pregunta d'escriure les freqüències al fitxer de configuració, jo sempre trio no.
Advanced: no se el que et demana, no l'agafis perque et deu preguntar mes coses encara.

Quan el procediment s'acabi, tornaras a la terminal i hauràs de posar:
> sudo /etc/init.d/gdm start

A veure que pasa.

Salut!

---

### Post by Druiling on 2008-04-19
Bones a tothom!

Dóna això:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; 
backup in  /etc/X11/xorg.conf.20080419202729
maria@maria-laptop: (el símbol aquell de mig infinit que no sé on tinc en el teclat) i $
```

Tot això quan demana la profunditat de color després del teclat, el ratolí, detectar perfectament ell solet el driver i tot plegat.

Jo crec que està endimoniat!![-o<

Fins ara.

---

### Post by patrickfromspain on 2008-04-19
ostres ostres... ja no entenc res! Enganxa'ns el teu xorg.conf, si us plau. M'agradaria que saber que coll__s hi posa. Amb tot lo que s'ha tocat, pot ser maco veure-ho.

salut!

---

### Post by Druiling on 2008-04-19
JAJAJA
Quin el xorg.conf pelat o algun altre del fotimer que tinc, aquells que acaben amb número?
D'això...una pregunta que potser semblarà d'aquelles que no em funciona mitja part del cervell. 
Podria ser que amb tanta mandanga fes petar també windows? o el grub? i amb el grub l'entrada a windows?
Ho dic perquè això ja si que no pot passar-me ara mateix, a l'estiu si però ara no, que tinc molta feina i no puc perdre tot el que porto fet!
Ah! per cert, com faig per enganxar el que hi hagi al xorg.conf? és que ara com no entro ni en kde, no sé què haig de fer...
Fins ara.

PD: no us desespereu, que els que no en sabem un dia d'aquests ens il·luminarem i podrem ajudar més que no pas enredar! Ho PRONOSTICO!!

---

### Post by patrickfromspain on 2008-04-19
si no toques res del grub, no es pot espatllar, aixi que tranquil. Amb això del xorg.conf nomes toques coses del servidor gràfic, per tant.. com a molt pots cargar-te el servidor gràfic (que ja el tens trencat xD).

L'xorg que serveix es el que no te numero, però de totes formes... si pots, fer un arxiu comprimit amb tots els xorg.conf que hi ha.

Una altra cosa, el kubuntu funciona no? Es una altra particio o es simplement o tens instalat gnome i kde en la mateixa particio?

salut!

---

### Post by Druiling on 2008-04-19
En la mateixa partició.
Suposo que no et pensaves pas que seria tan fàcil...

Fins ara.

---

### Post by patrickfromspain on 2008-04-19
si esta en la mateixa particio.. jo trobo que descartem l'xorg.conf com a font del problema.

Proba:

cd
sudo rm -rf .ICEauthority .Xauthority

a veure si aixi pots entrar...

salut!

---

### Post by CarlesOriol on 2008-04-19
i seguint amb el raonament d'en patrick

chown elteuusuari:elteuusuari -R /home/elteuusuari

---

### Post by patrickfromspain on 2008-04-19
pro clar.. ara que hi caic.. si kde va be.. xD

---

### Post by Druiling on 2008-04-19
M'he recordat que puc veure la partició on tinc ubuntu a windows.
Ja ho va dir en Carles fa segles, que no tenia clar que fos el xorg, però igualment us passo una còpia que he fet del xorg.conf en odt.
Gràcies nois.

PD: jo no sóc de rendir-me, però em veig reinstal.lant...

---

### Post by patrickfromspain on 2008-04-19
bé, jo diria que podem confirma que es no res del xorg.conf, ja que te bona pinta. A partir d'aqui.. es probar.

prova a fer:

```
cd
mv .gnome .gnome-original
mv .gnome2 .gnome2-original
mv .config .config-original
mv .gconf .gconf-original
mv .gconfd .gconfd-original
```

salut!

---

### Post by Druiling on 2008-04-20
Bon dia tothom gent!
Patrick, mira no surto d'això:

"command not found" i "no such file or directory"

El fet que no faci res de res, em dona a entendre que potser estic fent alguna cosa malament. No sé si se us acut què?

Fins ara.

---

### Post by patrickfromspain on 2008-04-20
Command not found quan? mira que ho escriguis be... tan **cd** com **mv** son comandes que hauries de tenir.

salut!

---

### Post by Druiling on 2008-04-20
> **patrickfromspain said:**
> Command not found quan? mira que ho escriguis be... tan **cd** com **mv** son comandes que hauries de tenir.

Ho he escrit bé, estic segura perquè ho he provat diversos cops. Ara bé, igual és que hi ha alguna cosa que no faig bé abans o algo. Ho descric:

Ctrl+Alt+F1
usuari
password
sudo cd
command not found
sudo mv .gnome .gnome-original
<.gnome> no such file or directory
i així successivament amb tot.

He provat a no posar sudo i tornar a fer-ho tot, però el resultat és el mateix.

Estic segura perquè he estat una bona estona provant.

Fins ara.

---

### Post by papapep on 2008-04-20
Druiling, quan vols fer alguna cosa (moure, copiar, esborrar, etc..) a algun fitxer o directori tens dues opcions:

 1.- Ets al mateix directori on tens l'objecte amb el que vols actuar.

 Ex. vols fer una còpia de seguretat del sources.list: 

```
cd /etc/apt/sources.list
sudo cp sources.list sources.list.backup
```

això funciona per que JA ETS on és el fitxer que vols copiar.


 2.- Li dones el camí fins on és l'objecte a tractar (indiferentment d'on estiguis tu en aquell moment).

Amb el mateix exemple d'abans:

```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

T'anirà bé fer un cop d'ull a això: [https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#head-0e06aad37c971bb4c2c1d36df8d6700c3114f319](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#head-0e06aad37c971bb4c2c1d36df8d6700c3114f319)

Amb això, entre d'altres coses, veuràs que "sudo cd" no és una ordre correcte, en el sentit de que **cd** necessita un paràmetre que és a on vols anar.

---

### Post by patrickfromspain on 2008-04-20
sudo cd.. no pas. No funciona.

nomes cd a seques. 

salut!

EDITO: papapep, prova a fer qualsevol sudo cd.. no va

patrick@patrick-desktop:~$ sudo cd /root/
sudo: cd: command not found

Una altra cosa, druling. Tu vas insta&#322;lar ubuntu o kubuntu?

---

### Post by papapep on 2008-04-20
Encara que no m'hagi explicat és el que volia dir...que "sudo cd", nanay...

AFEGITÓ: Druiling, si acabes venint a Caldes, recorda fer abans una còpia de seguretat de tot el que et calgui conservar de l'ordinador. Fa pinta de que hi tinguis un bon guirigall i igual cal fer-li un rentat+centrifugat a fons...

---

### Post by Druiling on 2008-04-20
Patrick, vaig instal.lar ubuntu, el que passa és que vaig començar a enredar amb aplicacions de kde i després em  vaig instal.lar també l'escriptori kde, però la instal.lació va ser Ubuntu.


> **papapep said:**
> AFEGITÓ:Fa pinta de que hi tinguis un bon guirigall i igual cal fer-li un rentat+centrifugat a fons...

Paraula de Déu. Et lloem Senyor.

Jajajaja

Tothom  tranquil.

Tanco aquest post maleït i ens veiem  a Caldes, perquè em sembla que això requerirà la intervenció d'unes mans expertes. Anem  a veure si podem començar amb el tema net (la higiene és molt important a la vida).

Una abraçada, fins dissabte i moltes gràcies a tots.



PD: Més val que dediqueu la vostra saviesa a casos resolubles i no pas a polstergeits com aquest. Si cas, quan ho haguem  resolt (eufemisme de ho hagueu resolt), podem  reobrir el fil i si algú s'hi torna a trobar, que pugui saber quina va ser la solució, si no acaba sent petar-ho tot i tornar a instal.lar. 

RPD: Una altra setmana amb windows. Veieu com tinc un karma complicat?, ho veieu?

---

### Post by SiscoGarcia on 2008-04-20
> **papapep said:**
> Encara que no m'hagi explicat és el que volia dir...que "sudo cd", nanay...

AFEGITÓ: Druiling, si acabes venint a Caldes, recorda fer abans una còpia de seguretat de tot el que et calgui conservar de l'ordinador. Fa pinta de que hi tinguis un bon guirigall i igual cal fer-li un rentat+centrifugat a fons...

Sense ànims de segrestar el fil: Pot ser interessant per tothom que vinguem a Caldes de fer còpia de seguretat de tot per si de cas o què?

---

### Post by CarlesOriol on 2008-04-21
> **SiscoGarcia said:**
> Sense ànims de segrestar el fil: Pot ser interessant per tothom que vinguem a Caldes de fer còpia de seguretat de tot per si de cas o què?

SEMPRE. S'ha de fer copies de seguretat. Hi ha un fil de fa uns dies molt interessant sobre les diverses eines per fer-ho.

I evidentment com dieu si cal actualitzar una màquina és especialment crític. Però sempre hi ha valents que creuen en la immortalitat :-)

---

### Post by SiscoGarcia on 2008-04-21
No ho sóc tan valent jo... ans al contrari. Ho deia perquè dubto d'actualitzar-me abans de la festa o fer-ho allà. La veritat és que m'agradaria fer-ho ben fet, amb el vostre assessorament.:)

EDITO: Ja veus el meu "valor".

---


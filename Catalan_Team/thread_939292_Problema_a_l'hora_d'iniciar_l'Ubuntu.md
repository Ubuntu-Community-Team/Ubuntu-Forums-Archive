---
title: "Problema a l'hora d'iniciar l'Ubuntu"
date: 2008-10-05
forum: Catalan Team
---

### Post by Only_catalan on 2008-10-05
Seguint amb els meus problemes relacionats amb emprar l'Ubuntu a un ordinador, i després de resoldre'n el primer problema derivat, em topo de nassos amb el segon problema.

Un cop la instal·lació ha final·litzat. Cada cop que engego l'ordinador, aquest es queda a una pantalla negra on figuren les següents indicacions:

Starting anac(h)ronistic cron anacron [OK]
Starting deferred execution scheduler atd [OK]
Starting periodic command scheduler crond [OK]
Cheking battery state
Runnig local boot scripts (/etc/rc.local) [OK]

i es queda aquí, amb un "_" fent pampallugues i sense opció a res més. Aviam vosaltres, que sou homes de sapiència i de fe, si sou capaços de treure'm d'aquest merder. (Rodol·lí supervisat per la generalitat de Catalunya i en Draqui)

Gràcies!

---

### Post by Only_catalan on 2008-10-05
Ara acabo de guipar, amb no pas poc esfereïment i fins i tot corpreniment, que qualque qüestió semblant a eixa prou temps fa que rodola per ací. Tanmateix caldrà, altra volta, que hi faci una bona lectura abans de començar a fer preguntes. 

Si un cop feta la guaitada general i àdhuc així no me'n sortís, llavors reemprendria aquest missatge.

Perdoneu el torb.

---

### Post by Only_catalan on 2008-10-07
Bé, després de fúmer un rest de cops de cap, ara sí, pregunto com solucionar el problema que se'm presenta.

Un cop el  Línux "alternate" és intal·lat a l'ordinador i inicio l'ordinador, aquest se'm queda aturat a les línies que ja us vaig comentar. Llavors pitjo ctrl+alt+F1 i entro com a usuari posant la contrasenya i l'usuari. Un cop dins faig startx i em diu:

EE: VIA(0): No valid modes found.
EE:Screen found, but none have a usuable configuration.

Què pot fer hom per tal d'assolir la increïble, magna i esfereïdora fita d'iniciar l'ordinador. 

P.S:He provat alguna cosa d'aquelles d'editar el Kernel i escriure algunes comandes com api=off o coses per l'estil però no sé ben bé si ho faig bé o com redois es fa. Bé, romandré a l'aguait de vostres savis mots i consells.

---

### Post by papapep on 2008-10-07
Jo provaria a fer un:

```
sudo dpkg-reconfigure xserver-xorg
```

i veure si així pots configurar el servidor gràfic i, com a mínim, arrencar-lo.
Si amb el teòric driver que li pertoca a la placa nova, executa un altre cop la ordre i tria el driver "Vesa", que és el genèric.

Més endavant ja li podràs fer un ajustament més fi.

---

### Post by Only_catalan on 2008-10-07
Mercès gentilhome.

---

### Post by Only_catalan on 2008-10-07
Un cop entro aquesta instrucció em pregunta primer per si vull emprar la interfície cap al dispositiu de "framebuffer" del nucli. I un cop resposta aquesta pregunta em fa preguntes sobre configuracions de teclat i llavors s'acaben i torna a l'estadi anterior. Però enlloc em diu res sobre VESA. Què és el que no faig bé? On es canvia això de VESA? És normal això que em passa?

---

### Post by papapep on 2008-10-07
....fes això:

```
aptitude search xserver |grep ^i
```

amb això li demanem que ens mostri tots els paquets de servidor gràfic que tens instal·lats en aquest moment (amb "grep ^i filtres els que la línia del llistat resultant comença amb una "i", que són els instal·lats).

---

### Post by Only_catalan on 2008-10-07
Un cop fet em diu que tinc el "VESA display driver", entre molts d'altres. Com el trio o selecciono ara?

---

### Post by papapep on 2008-10-07
mmmm....hauríem d'assegurar un parell de coses.

1.- La targeta gràfica que tens.

 Fes:

```
lspci |grep [gG]raphic
```

amb això llistem tots els dispositius detectats als ports pci del sistema i filtrem les línies que continguin la paraula "Grafic" o "graphic".

2.- Hem de veure el contingut del fitxer **/etc/X11/xorg.conf**, que és el fitxer de configuració del servidor gràfic.

 Sé que és complicat per que no pots tallar i enganxar de manera fàcil, però ajudaria saber-ne el contingut. Una, o vàries, fotografia potser farien la feina ;-)

---

### Post by Only_catalan on 2008-10-07
Comencem per la targeta gràfica que ja et dic que és VIA/S3G KM400/KN400 i poso una imatge per a demostrar-t'ho:

[IMG]http://img504.imageshack.us/img504/9787/imag0057yi9.jpg[/IMG]

Pel que fa a l'altra cosa que necessito, he escrit aquesta línia de codi que em dius "/etc/X11/xorg.conf" però clar, evidentment no es fa així. Suposo que he d'entrar a les carpetes i visualitzar l'arxiu. Si em diguessis les instruccions per entrar a carpeta, sortir-ne i visualitzar arxiu t'ho agrairia. Jo conec les de win però no crec que siguin les mateixes...

---

### Post by Only_catalan on 2008-10-07
Bé, ja he cercat com es fa però no trobo aquest arxiu. De fet no se com baixar per sota del nivell home i per tant, no sé com anar a "/etc/X11/xorg.conf"

---

### Post by SiscoGarcia on 2008-10-07
Hola gentilhome ;)

Aquesta sí que me la sé, però no sé si podré ajudar-te gaire més. Per poder entrar a la carpeta desitjada has d'obrir un terminal i escriure-hi:

```
cd /etc/X11/xorg.conf
```

Amb això canvies de directori i et situes al dels gràfics (xorg.conf), llavors per veure què hi ha has de llistar-ho, és a dir, has de fer:

```
ls
```

i així et llistarà el contingut del fitxer desitjat.

Després caldran els savis consells del papapep o algun altre mestre :)

EDITO: si no et funcionés prova a posar-hi al davant "sudo" (sense les cometes), és a dir, a assolir privilegis de superusuari de l'equip.

---

### Post by Only_catalan on 2008-10-07
Grosses mercès confrare!

---

### Post by Only_catalan on 2008-10-07
Bé, bé, bé, ja ho tenim això. He fet les tres fotos màgiques. Aviam si pot servir per desllorigar-ho. Per cert, us he dit gràcies?

[IMG]http://img137.imageshack.us/img137/731/pic0055oq0.jpg[/IMG]

[IMG]http://img114.imageshack.us/img114/2702/pic0056wr9.jpg[/IMG]

[IMG]http://img243.imageshack.us/img243/6823/pic0057zh8.jpg[/IMG]

---

### Post by papapep on 2008-10-08
Vaja home, ara resulta que a partir de la Hardy s'han carregat la funcionalitat de reconfigurar el servidor gràfic amb dpkg-reconfigure xserver-xorg....:[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)
Per això no t'ha preguntat res de la configuració de la gràfica abans....buffff. Quins "invents de la sopa d'all" que fan a vegades...
Necessito una mica de temps per veure si algú se n'ha sortit amb aquesta gràfica teva que, a més, sembla que és de les "divertides" :-)

---

### Post by Only_catalan on 2008-10-08
Gràcies, però ahir vaig informar-me i vaig esbrinar la festa major que hi ha rere la meva targeta. Vaig descobrir que és la de pitjor instal·lació i que a més no pot ni amb les tres dimensions. Per tant, a aquest ordinador hi deixaré Xp. Ara, intentaré arreglar la pantalla (comprar-ne una i instal·lar-la) d'un altre portàtil Ahtec de 15,4 polzades que tinc. Que per cert, si sabeu d'on puc treure una pantalla de segona mà per aquesta bestiola tant si és genèrica com Ahtec (que segur que és genèrica) per màxim 60 euros m'ho dieu.

Si algú té una targeta VIa S3 unichrome i li interessen els enllaços a pàgines on es parla sobre com instal·lar les 2d que ho digui i els posaré car els guardí.

Arreveure i moltíssimes gràcies.

---


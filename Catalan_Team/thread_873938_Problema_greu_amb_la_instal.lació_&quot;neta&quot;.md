---
title: "Problema greu amb la instal.lació &quot;neta&quot; de l'Ubuntu"
date: 2008-07-29
forum: Catalan Team
---

### Post by alhanduin on 2008-07-29
Com alguns sabreu últimament he estat barallant-me de manera desmesurada amb els drivers de la tarjeta ATI Radeon 9600 que porta el meu ordenador portàtil Acer... Doncs bé cada vegada que la "cagava" reinstal.lava l'ubuntu de nou formatejant la seva partició i ja està però ara no hi ha maner´

LA situació és la següent;

Poso el Cd d'instal.lació, trio idioma, zona horaria... i arribo a les particions;

17GB per a ubuntu en /
2 GB d'area d'intercambi
40GB d'espai per a arxius en /home

El que faig és que quedi així;

15GB per a ubuntu en / + Formateig de la nova partició
2Gb d'espai lliure per a Suricataos
2 GB d'area d'intercambi + formateig d'aquesta àrea (automàtic)
40GB d'espai per a arxius en /home

La instal.lació segueix, tot perfecte, s'acaba, reinicio l'ordenador, trec el cd, salta la pantalla de nom d'usuari i contrasenya i quan carrega l'escriptori gnome apareixen unes ratlles diagonals que ocupen tota la pantalla i que són del color marró del fons de pantalla de l'escriptori.

En aquesta situació si moc el cursor veig una infinitat de punts blancs distribuits al llarg de les ratlles diagonals que canvia d'una a l'altre. Si el porto per intuició (xq no veig res) a dalt de tot de la pantalla on tenia els accessos directes i faig clic canvien de color les ratlles així que suposo que s'obre algún menú...

He probat en mode gràfic segur i passa el mateix... Només puc entrar en terminal en mode gràfic segur...

Algú pot ajudar a reconfigurar el recen instal.lat ubuntu??? 

(la tarjeta aquesta m'està portant pel camí de l'amargura amics meus!!!!!!)

---

### Post by alhanduin on 2008-07-29
He probat amb l'ordre; 

sudo dpkg-reconfigure -phigh xserver-xorg

i tampoc ha funcionat...

---

### Post by ffp on 2008-07-29
Perdona la pregunta, que es?

2Gb d'espai lliure per a Suricataos. ????

De la resta del teu problema, no se que dir-te, funciona el PC amb live CD?.
Les altres vegades, funcionava ve, tot i que sense acceleració?. Si funciona ve amb el live, quelcom es deu carregar malament.

---

### Post by alhanduin on 2008-07-29
1.- La pregunta és; ¿Quines ordres he d'escriure a la terminal per a arreglar el problema que tinc i poder tornar a utilitzar el meu ordenador???

2.- El suricataos es una versió del win Xp molt reduida que serveix única i exclusivament per jugar (amb linux m'era totalment impossible)

3.- El LiveCd funciona moooolt lent però funciona.

4.- Porto un any amb ubuntu Feisty Fawn y Hardy Heron. Sempre m'ha funcionat bé però sense acceleració 3d.

Jo crec que hi ha algun arxiu residual que m'està fent la punyeta...

---

### Post by alhanduin on 2008-07-29
He eliminat l'arxiu xorg.conf (sudo rm /etc/X11/xorg.conf)i obviament no s'obre ni la pantalla d'inici, la qual queda negre i amb ratlles de colorets... Ara tornaré a reinstal.lar l'ubuntu a vere que tal...

Si algú te suggeriments, si us plau... Jo faig el que digueu

---

### Post by alhanduin on 2008-07-29
Ja he tornat a instal.lar l'ubuntu i res de res... Segueix igual...

---

### Post by oriolsbd on 2008-07-30
Hola, ens podries dir què obtens si fas des de consola;
ls -l /home

Salut!

---

### Post by alhanduin on 2008-08-01
Gracias a Iván hemos podido solucionar mi problema, de manera resumida lo hemos hecho así.

Como habia jodido las particiones ya no podia ni reinstalar ubuntu, entonces puse el xp en las particiones 1 y 2 con el formateo y el sistema fat3.

Tras esto reinstalé el ubuntu en la 2 sin problemas

Una vez en ubuntu no podia entrar en la partición 3 donde tenia los archivos porqué estaba dañada y la hemos mandado verificar y reparar con el gparted.

Una vez hecho esto ya podíamos acceder a la partición 3 pero no podia ver la carpeta lost+found xq no tenia los permisos y lo último que hicimos fué darle los permisos con el comando chmod.

Y ya he recuperado mis archivos!!!!

Moltes gràcies Ivan!!! M'has salvat la vida!!! jejejejje

---

### Post by CarlesOriol on 2008-08-03
eps... el fòrum és en català.

---


---
title: "Molts problemes amb la 8.10"
date: 2008-10-31
forum: Catalan Team
---

### Post by lluisalguero on 2008-10-31
Aquest matí he fet l'actualització, i crec que és la gota que ha fet vessar el got.

Si abans amb la 8.04, ja vaig tindre problemes (no funcionava el mouse, encara no puc fer funcionar la webcam, em desconecta la wifi cada 2x3), ara amb l'actualització, directament m'ho ha desconfigurat tot..la wifi no sap ni el que és, per cable no hi ha forma de connectar-se (ni tant sols puc accedir al router!!). Li fico la ip, porta d'enllaç i les dns i fa el que li rota...torno a entrar i m'ho ha canviat tot.

Com veieu pel to del meu missatge, la desesperació és màxima. Un fa el possible per "desintoxicar-se" dels sistemes operatius privatius, i amb els lliures les meves batalles son constants.

Però la "cabra intrèpida" ho té clar amb mi...no em rendeixo facilment, cada cop que em foti de cap, em tornaré a ficar en peus...i espero que algú em doni un cop de mà per continuar endavant.

Moltes gràcies,
Lluís

---

### Post by badChecksum on 2008-10-31
Jo també n'he tingut.:-? 

Fa cosa d'un mes vaig probar l'Ubuntu per primera vegada, i vaig fer-me una partició per tenir-lo junt amb el Finestres XP. 
Amb la 8.04.1 tot funcionava de meravella, pero des de que vaig actualitzar ahir a la 8.10 el router es desconfigura cada cop que entro al XP, si prèviament he entrat a Ubuntu :-? Al no trobar-hi cap solució he acabat tornant a instalar el Hardy...:(

---

### Post by tanreb20 on 2008-10-31
Pel que fa a la camera web, prova amb cheese:

sudo aptitude install cheese

Esta als repos i et soluciona elproblema, ara si el que vols es fer videoconferencies i tal.... aMsn

Per tot el demés em passa com amb tu amb el tema de la wifi, ara provare a veure si amb el ndsiwrapper funciona pero no i tinc massa esperances... per sort el cable si que funciona!

---

### Post by tanreb20 on 2008-10-31
Jo he aconseguit qeu em reconegui les conexions wifi de la seguent manera:

sudo gedit /etc/modprobe.d/blacklist

i afegir:

```
[B]blacklist ath_hal
blacklist ath_pci
[/B]
```

després he installat el ndiswrapper:

```
sudo aptitude install i A ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1 ndisgtk
```

i a continuació obrir fer:

```
ndisgtk i seguir grtaficament

o bé:

sudo ndiswrapper -i direccio del driver/arxiu.inf
```

I esperant una estona m0han sortit les conexions wifi!

Ara falta que m'hi coneccti,pero vaig per bon camí!

---

### Post by climent on 2008-10-31
Doncs jo porto un quart d'hora amb l'intrèpid i cap problema. Això sí, no he fet actualització sinó instal·lació nova de trinca, fins i tot de la partició /home. Primer de tot em connecto amb cable i quan ja he actualitzat l'idioma, tot seguit instal·lo el wicd i esborro el network-manager (no sé si amb la nova versió va millor, però des que tinc el wicd les wifi van com la seda). Després, a instal·lar la resta, i de moment, cap problema.

---

### Post by PatrickVogeli on 2008-10-31
ei nanus, pareu el carro!

Aquest post, amb la informacio que doneu es completament inutil.

Es inutil perque barrejeu problemes: el problemes que teniu cada un van a un fil per separat. Si no, no n'hi treurem l'aigua clara.

Es inutil perque es una queixa: quin es el teu hardware? Aquesta informacio es VITAL per poder ajudar.

Es inutil perque es donen solucions que funcionen en base a un hardware concret, sense tenir en compte el hard del que te el problema.

sento dir-ho aixi, no us ho prengue malament (si us plau), però s'ha dit molts cops: un problema un fil. Quan obriu un fin, adjunteu informacio.

salut

---

### Post by lluisalguero on 2008-10-31
M'estic baixant una copia de la 8.10, faré una instalació neta i a veure que pasa...

PatrickVogeli, estic fent servir un portàtil clònic, que amb la 8.04 només tenia el problema que no m'anava la webcam integrada (la veritat és que tant se me'n fotia), lo de desactivar el touchpad ho vaig poder solucionar.

Ara així a "bote pronto" els problemes més destacables que tinc son:

- La connexió wifi, em diu que no la gestiona :confused:
- No puc connectar ni amb cable, ni puc accedir tant sols al router
- No puc desactivar el touchpad (he seguit els mateixos passos que vaig fer amb la 8.04, però no ha fet efecte)
- No tinc so, només sento un soroll de "fregit" amb la "cançoneta" de l'inici.
- Tot i estar connectat a la corrent per cable, em diu que no ho està i per tant em va descarregant la bateria.
- Cada cop que obro el Firefox, em diu que l'haig de reiniciar perque s'actualitzat :confused:
- Haig de clicar dos cops per a que pugue obrir qualsevol cosa (no em refereixo a doble clic), vull dir que intento obrir un programa, es queda pensant i a la barra inferior em surt com si el vulgués obrir, però seguidament es tanca, torno a provar, i si hi ha mooooooolta sort igual és obre, encara que el 80% de les vegades no ho fa...

Ja dic, això és el que en un primer moment he vist, segurament que tindré alguna "trampa" més amagada...si algú es veu en cor de donar-me un cop de ma, jo encantat...si no molt a contracor faré una instal·lació neta.

I ara que se m'acut, hi ha possibilitat de tornar enrara (tornar a la 8.04)?

Perdoneu el "totxo", però m'heu d'entendre, estic desesperat

---

### Post by PatrickVogeli on 2008-10-31
hola,

el fet de que sigui un portatil clonic no ajuda a esbrinar quin es problema, però, anem a fer uns pocs pasos que ens ajudaran a saber quin hardware tens exactament i perque pot estar fallant:

en un terminal, just despres d'arrancar fes:

cd ~/Escriptori
dmesg > dmesg.log
lspci > lspci.log
lsusb > lsusb.log

despres d'aixo et trobaras 3 fitxers .log a l'escriptori. En pots fer un tar.gz i adjuntar-lo aqui.

Evidenment, si primer fas una intal·lació neta, molt millor. Així descartem possibles problemes de configuracio degut a l'actualització (cosa que no sembla infreqüent). No se com ho deus tenir fet tu, però si et fas una particio /home separada no perdras les dades ni res. Si no ho tens així, fes un pensament, perque es molt comode. Jo per actualitzar de la hardy a l'intrepid no vaig perdre ni tan sols massa temps: quan la intrepid va arrancar em vaig trobar l'escritori igual que amb la hardy, i les aplicacions configurades igual.

salut, anims i sort

---

### Post by lluisalguero on 2008-11-01
> **PatrickVogeli said:**
> hola,

el fet de que sigui un portatil clonic no ajuda a esbrinar quin es problema, però, anem a fer uns pocs pasos que ens ajudaran a saber quin hardware tens exactament i perque pot estar fallant:

en un terminal, just despres d'arrancar fes:

cd ~/Escriptori
dmesg > dmesg.log
lspci > lspci.log
lsusb > lsusb.log

despres d'aixo et trobaras 3 fitxers .log a l'escriptori. En pots fer un tar.gz i adjuntar-lo aqui.

Evidenment, si primer fas una intal·lació neta, molt millor. Així descartem possibles problemes de configuracio degut a l'actualització (cosa que no sembla infreqüent). No se com ho deus tenir fet tu, però si et fas una particio /home separada no perdras les dades ni res. Si no ho tens així, fes un pensament, perque es molt comode. Jo per actualitzar de la hardy a l'intrepid no vaig perdre ni tan sols massa temps: quan la intrepid va arrancar em vaig trobar l'escritori igual que amb la hardy, i les aplicacions configurades igual.

salut, anims i sort

provaré de fer això que dius...

---

### Post by lluisalguero on 2008-11-01
> **PatrickVogeli said:**
> hola,

el fet de que sigui un portatil clonic no ajuda a esbrinar quin es problema, però, anem a fer uns pocs pasos que ens ajudaran a saber quin hardware tens exactament i perque pot estar fallant:

en un terminal, just despres d'arrancar fes:

cd ~/Escriptori
dmesg > dmesg.log
lspci > lspci.log
lsusb > lsusb.log

despres d'aixo et trobaras 3 fitxers .log a l'escriptori. En pots fer un tar.gz i adjuntar-lo aqui.

Evidenment, si primer fas una intal·lació neta, molt millor. Així descartem possibles problemes de configuracio degut a l'actualització (cosa que no sembla infreqüent). No se com ho deus tenir fet tu, però si et fas una particio /home separada no perdras les dades ni res. Si no ho tens així, fes un pensament, perque es molt comode. Jo per actualitzar de la hardy a l'intrepid no vaig perdre ni tan sols massa temps: quan la intrepid va arrancar em vaig trobar l'escritori igual que amb la hardy, i les aplicacions configurades igual.

salut, anims i sort

Aquí tens el que demanes, gràcies per donar-me un cop de ma

---

### Post by PatrickVogeli on 2008-11-02
Bé, anem per parts:

**1.-** tens una wifi intel 3945, i aquesta tarja t'hauria de funcionar sense masses problemes, ja que el suport en el nucli es bo. Pot ser que el problema el tinguis amb el network manager, un programa que jo, de moment, considero altament inestable i trobo qüestionable que vingui instal·lat i en us per defecte. La solucio pot estar fent servir el [wicd]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=635891"). Per fer-lo servir, primer desinstal·la el network-manager i despres instal·les el wicd. Reinicia i proba que tal. Amb la mateixa tarjeta, a mi em funciona de conya.

**2.-** Per cable: el wicd gestiona també el cable. A mi em va de conya, a mes pots tenir varis perfils, cada un amb la seva ip estatica diferent o dinamica o com ho vulguis. Proba i ja diras.

**3.-** Audio: has mirat que ho tinguis ben configurat? Mira al controlador de volum del gnome primer, i a alsa-mixer despres, a veure que hi trobes. Si et serveix, igual tens alguna barra en mute i/o tens activat que se senti el soroll del microfon pels altaveus. Et pasa amb tots els sons que es senten malament? 
Si no: el dmesg indica que fas servir el modul snd-hda-intel, pero que no sap el model i per tant, n'agafa un automaticament. Mirant la documentacio de l'ALSA, per la teu codec (ALC883), hi ha diferents models:
```

	ALC883/888
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  acer-aspire	Acer Aspire 9810
	  medion	Medion Laptops
	  medion-md2	Medion MD2
	  targa-dig	Targa/MSI
	  targa-2ch-dig	Targs/MSI with 2-channel
	  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
	  lenovo-101e	Lenovo 101E
	  lenovo-nb0763	Lenovo NB0763
	  lenovo-ms7195-dig Lenovo MS7195
	  haier-w66	Haier W66
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  6stack-dell	Dell machines with 6stack (Inspiron 530)
	  mitac		Mitac 8252D
	  clevo-m720	Clevo M720 laptop series
	  fujitsu-pi2515 Fujitsu AMILO Pi2515
	  auto		auto-config reading BIOS (default)

```
Per especificar un model en concret, has d'editar el fitxer /etc/modprobe.d/alsa-base i al final de tot hi poses: options snd-hda-intel model=MODEL
Es bastanta feina, ja que has de posar el model que vols probar, guardar i reiniciar i tornar-hi fins que trobis un model que sigui bo.

Els demes problemes, no se que dir-te. El tema del corrent em sembla extrany, igual que el del firefox.

Per provar: gksudo gedit /etc/apt/sources.list i alla comenta-ho tot (posant un # davant de cada linea) i posa-hi aixo:

```

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

```

llavors fes sudo apt-get update && sudo apt-get install ubuntu-desktop linux && sudo apt-get dist-upgrade, a veure si et faltava qualsevol cosa. Si despres de reiniciar segueix tot igual, jo faria una instal·lacio nova i miraria. Si ja l'has fet, et segueix passant tot el que has dit?

salut

---

### Post by lluisalguero on 2008-11-02
Com que amb la 8.10 no anava, he fet una instal·lació neta de la 8.04 i gairebé estem amb el mateix.

- puc connectar-me a la meva wifi, pero faig un ping al router i em diu que allà no hi ha res.

- tema soroll, ara amb la 8.04 si funciona

Alguna cosa faré, no sé el què...però algo faré......

---

### Post by papapep on 2008-11-02
El primer que hauries de fer és obrir un fil nou per a cada tema per separat. Sinó es fa impossible prestar l'atenció necessària a cada cosa.

---

### Post by lluisalguero on 2008-11-03
> **papapep said:**
> El primer que hauries de fer és obrir un fil nou per a cada tema per separat. Sinó es fa impossible prestar l'atenció necessària a cada cosa.

Al final he optat per formatejar tot el disc dur i eliminar totes les particions que tenia (inclosa la del xp) i ho reinstalaré tot de cap i de nou...llavors si tinc ja algún problema us ho ficaré.

Gràcies a tots per l'ajuda.

---


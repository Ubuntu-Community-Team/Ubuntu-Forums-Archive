---
title: "[SOLVED] Sortida inesperada..."
date: 2008-02-09
forum: Catalan Team
---

### Post by Frealof on 2008-02-09
Hola a tothom...

M'estava llegint un post per aquí buscant alguna manera de poder configurar el GLX de la GeForce 7300 GT que he adquirit recentment quan, a l'hora de tirar endarrere la plana amb el Firefox (la fletxeta que hi ha a dalt a l'esquerra) automàticament m'he trobat a la finestra d'inici d'ubuntu... algú té idea de què pot haver passat? O millor encara com solucionar-ho?

Gràcies per endavant.

---

### Post by cortsenc on 2008-02-09
Quina por!!
Et passa sempre? Quina web visitaves?

Només se m'acud que et *petés* l'entorn gràfic...
Prova de mirar els LOGs, a veure que diuen.

---

### Post by Frealof on 2008-02-11
Hola de nou! I gràcies per haver fet un cop d'ull per petit que sigui al meu petit problema.  :)

Doncs no, sempre no... però ara s'està tornant un fet "habitual" i si, fa por. I quan no em passa, se'm penja tot, cosa que tampoc es que sigui massa divertida...

Em passa a la que inicio el Firefox, ni que sigui per mirar el correu electrònic o mirar de buscar pel Google alguna solució... Lo de la pantalla d'inici em va passar quan buscava per aquesta web una solució per un altre petit problema que tenia...

Mirar els LOG's, deies? Podries explicar-me com ho haig de fer? Es que sincerament, tot i portar un temps amb Ubuntu encara sóc un pobre ignorant...

---

### Post by papapep on 2008-02-11
Jo el que també provaria, a banda de mirar els logs, és a fer un memtest a la ram que no sigui que tinguis algun mòdul en procés de defunció.

---

### Post by CarlesOriol on 2008-02-12
Prova desactivant els efectes d'escriptori si et passa.

M'he trobat algun cop en això que descrius en gràfiques intel amb el xgl activat.

---

### Post by Frealof on 2008-02-13
Hola de nou! Caram, idees! Cosa d'agrair :)
 
Últimament vaig bastant embolicat i tinc poc temps per remenar el trasto. 

Lo dels efectes d'escriptori ja vaig provar de treure'ls, però m'ho continua fent... Per tant provaré el Memtest i si em surt algun error el plantaria aquí a veure què s'hi pot fer.

---

### Post by Frealof on 2008-02-13
Hola,

He fet un Memtest... li he tingut fins ara, perquè l'he engegat i he marxat de casa, No m'ha donat cap error per tant suposo que la memòria esta en ordre... 

La targeta gràfica que tinc es una GeForce 7300 GT l'he re-instal·lat i sembla que esta ben configurada... Si més no ja puc tornar a jugar amb l'enemy territory, i de moment no m'ha tornat a "petar" res... pot ser que fos la targeta?

Salut!

---

### Post by papapep on 2008-02-13
Clar que si. De fet, ram i targeta gràfica solen ser la font d'aquests tipus de problemes.

---

### Post by Frealof on 2008-02-13
Doncs sembla que no s'ha solucionat la història :( 

Ara després de dinar estava provant d'instal·lar de nou el RegnumOnline, Tot ha anat correctament fins que m'ha tornat a petar...

El fet es que després de sortir i re-iniciar el PC abans abans que aparegués la barra aquella que mostra com es va carregant l'Ubuntu, m'ha saltat la pantalla i m'hi han aparegut tot de codis, al final hi posava això (he copiat tot el què hi posava)... 

[21.979333] kernel panic - not syncing: Attempted to kill init!

Acte seguit he posat el DVD d'edubuntu i he re-iniciat, més que res perquè vaig veure que hi havia una opció que posava "rescatar sistema trencat" o alguna cosa per l'estil (el què fa la inexperiència...),  he sel·lecionat i... bé, sembla que ha funcionat lo just com per poder escriure aquestes línies... de moment em funciona tot, targeta gràfica, adaptador USB per xarxes inalàmbriques, però clar... Hi ha alguna cosa que falla i no sé què.

He mirat si el sistema estava actualitzat i si. He mirat que no hi hagués cap paquet trencat (al haver estat remenant ves a saber..) i no n'hi ha cap... estic per carregar-me tot el què hi ha al disc dur i tornar-ho a instal·lar tot de cap i de nou...

Algun suggeriment?

---

### Post by Frealof on 2008-02-13
Altre cop jo XD 

Sento escriure tanta resposta seguida... Però es que n'hi ha per llogar-hi cadires amb les taules a joc i tot ;)!

El què deia... lo just per escriure aquí. Hi ha tornat, però ara quan s'ha iniciat el gnome ho ha fet més ràpid que mai, m'ha sortit un missatget tan maco d'aquests amb un signe de prohibit passar que deia

"Failed on initialize HAL"

I cap a la pantalla d'inici (com al joc de l'oca quan caus a la casella de la mort XD). Torna a entrar usuari i contrasenya i na fent...

Ara he obert el PC i veig que un dels ventiladors de la placa base (un que hi ha sobre el port AGP 8x) no funciona, no sé si hi podria tenir cap relació.

Gràcies per la vostra paciència.

---

### Post by papapep on 2008-02-13
Doncs una placa, i a més la gràfica, reescalfada òbviament alegries no te'n portarà gaires. No sé si és EL problema, però un part, com a mínim, segur. Tens alguna altra gràfica a mà per provar?

---

### Post by Frealof on 2008-02-13
Si. La que portava abans, una GeForce 2 MX400... Trec la que tinc i hi poso altre cop la vella?

---

### Post by papapep on 2008-02-13
Si, canvia-la. Si ho fas ajudarà a saber si el problema és estrictament de la gràfica o si és d'alguna altra cosa.

---

### Post by patrickfromspain on 2008-02-13
Has d'arreglar el ventilador!! si poses una grafica nova, i no arregles del ventilador de la placa base no faras massa cosa no?

---

### Post by papapep on 2008-02-13
Oh! És que jo havia interpretat (potser erròniament) que el ventilador anava incorporat a la targeta gràfica! Evidentment, si el problema és **directament** a la placa base, el tema s'ha de solventar abans de fer res. No em diràs que és el ventilador del processador, oi??? :-)

---

### Post by patrickfromspain on 2008-02-13
[QUOTE=Frealof]
Ara he obert el PC i veig que un dels ventiladors de la placa base (un que hi ha sobre el port AGP 8x) no funciona, no sé si hi podria tenir cap relació.[/QUOTE]

Jo diria que es el ventilador del northbridge.. No te perque afectar a la tarja.. de fet jo el meu tambe el tinc parat i tot va be desde fa molt de temps.. inclus a l'estiu. 

Si es el de la CPU... mal rotllo, pero diria que tampoc donaria aquests errors, sino que es rebotaria o s'apagaria el pc sencer. No?

salut!

---

### Post by Frealof on 2008-02-14
No, no es el ventilador de la CPU aquest esta ben bé sobre el processador i afortunadament funciona :) . El que jo dic es un de bastant més petitet. Es el que va sobre el lloc on hi ha el logotip de la marca. Us passo la direcció de la plana de Gigabyte amb el model perquè veieu de quin parlo 

[http://www.giga-byte.es/products/mb/specs/ga-7va_2x.html](http://www.giga-byte.es/products/mb/specs/ga-7va_2x.html)

en tot cas i com que no es que m'agradi que la placa estigui bullint n'aniré a buscar un de nou.

Gràcies altre cop.

---

### Post by CarlesOriol on 2008-02-14
Doncs... aixó.. el que t'ha dit en Patrick!

Tot i que ell té sort que l'ordinador li funcioni. :-)

---

### Post by Frealof on 2008-02-14
Doncs: he canviat el ventilador, n'he recuperat un que tenia d'una altra placa (que en pau descansi); passat l'aspirador per tots els racons del trasto... he estat remenant per Internet,; he provat els jocs a màxima resolució; mirat algun vídeo al Youtuve (que abans em petava)... i de moment no m'ha petat res de res... 

Pot ser que tot aquest merder el provoque&#347; un ventilador?? Aquesta tarda li faré un Memtest a veure què m'hi diu.

Salut i Ratafia!!

---

### Post by papapep on 2008-02-14
No, un ventilador no. L'excés de temperatura per manca d'ell si ;). Recordes de física el tema de la resistència a la conductivitat [en funció de la temperatura del medi]("http://es.wikipedia.org/wiki/Resistividad") suport??? Doncs va per aquí.

---

### Post by CarlesOriol on 2008-02-14
Si... si ... però a la ratafia a veure quan ens convides... ;-P

---

### Post by Frealof on 2008-02-14
Gràcies per la lliçó de física, de tan en tan va bé recordar que les coses s'aprenen per alguna raó :)
 
Home... Jo entenc que es una mica complicat via Internet. I sincerament la collita d'aquest any ha estat molt... diguem-ne "volàtil" ;), La propera vegada que feu alguna trobada que em quedi més o menys a prop de casa ja miraria de passar i portar-ne de can Rosset. XD

Però tornant al tema principal del post... de moment tot sembla anar bé. He fet el memtest i no m'ha donat errors... però ara fa, una horeta o dues mentre jugava una mica a l'Enemy Territory, he rebut un correu, el Pidgin m'ho ha fet saber i m'ha saltat el joc... per mi de moment això ja es molt, si més no ho puc fer anar tot amb certa tranquil·litat..

Salut!

---

### Post by Frealof on 2008-02-19
Sembla que tot continua funcionant sense problemes, per tant si us sembla bé donarem aquest fil per tancat.

Gràcies per les aportacions de tothom ;)

---


---
title: "La Gutsy em fa anar lent el portàtil"
date: 2008-01-28
forum: Catalan Team
---

### Post by pserra on 2008-01-28
Hola companys,
fa 1 mes vaig actualitzar a Gutsy el meu portàtil de 5 anyets, encara que darrerament  li he ampliat Disc dur (80 GB) i Ram (512) per  acabar-lo d'apurar, 
es un Toshiba 2410-304.
Doncs bé... continuu pensant (sentint) que amb Ubuntu  el disk dur em fa una mica de 'sorollet' quan treballa, cosa que amb el windows no en fa gens i altre cosa que  em te amoïnat es que des de que he fet l'actualització a Gutsy sembla que em deu consumir més recursos i **tot ell va bastant més lent** que quan tenia la Festy...
Per exemple quan faig busquedes amb el synaptic va lent... quan vull carregar un arxiu.doc... i em fa posar dels nervis....
Hi ha alguna manera de fer alguna comprobació o algú més si ha trobat en aquest problema??? ja se que el portàtil es 'vellet',però encara (mentre no peti del tot) el volia apurar 1 o 2 anyets més.

---

### Post by pserra on 2008-01-28
Abans m'he deixat detalls:
-a la barra de dalt i tinc l'icona del processador i gairabé sempre va al màxim (190GHz)
-L'icona de l'estat del processador em diu que la tinc al 93% d'us i cliko sobre ella per veure els processos i el que en aquests moments m'absorbeix més es:
-amule 9%
gnome system monitor 11%
gnome system monitor 23%
ktorrent 20%
mplayer 6%
mplayer 6%
mplayer 6%
aquests valors tenen constants fluctuacions, però més o menys es mou per aquests valors...
Es normal?
merci

---

### Post by papapep on 2008-01-28
Deixa'ns veure que mostra la comanda "top" a un terminal. Talla les línies que tinguin activitat i enganxa-les aquí, si us plau.

---

### Post by CarlesOriol on 2008-01-29
Pot ser que un dels discs un estas usant l'amule (o els multiples mlayers que tens oberts) sigui un ntfs?

---

### Post by pserra on 2008-01-29
Merci per l'ajuda companys..
Respecte al comentari de Carles Oriol, jo el amule no he fet cap configuració estranya, des de    sempre descarrega a /home.
També ara acabo d'arrancar el portàtil i va encara 'mitjanament bé' pero conforme treballo el sistema sembla que s'alenteix....

Aqui hi ha la sortida de la comnanda top:

top - 16:21:30 up 6 min,  1 user,  load average: 4.31, 3.11, 1.39
Tasks: 143 total,   5 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.6%us,  8.0%sy, 41.9%ni,  0.0%id, 35.2%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    515708k total,   502672k used,    13036k free,     7172k buffers
Swap:  2104468k total,      232k used,  2104236k free,   270204k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6753 beaglein  39  19 55172  17m 8300 R 37.5  3.5   0:02.79 beagle-build-in
 6185 pere      15   0 78060  29m  19m S 13.3  5.9   0:14.86 ktorrent
 6137 pere      15   0 89284  27m  17m S  2.3  5.4   0:11.57 amule
 4989 root      15   0 79112  22m 7556 R  1.0  4.4   0:10.93 Xorg
 6412 pere      15   0 42444  20m  16m R  1.0  4.1   0:02.71 konsole
 6205 pere      15   0 28896  10m 8780 S  0.3  2.1   0:00.31 kded
    1 root      15   0  2952 1852  532 S  0.0  0.4   0:01.37 init
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0
   27 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kacpid
   28 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  129 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod


hi veieu alguna cosa estranya??no  entenc massa cosa....

---

### Post by papapep on 2008-01-29
Doncs en el moment que has fet la "instantània", no sembla que el sistema tingui gaire càrrega. Com tu mateix podràs veure, només té un 14 i escaig per cent de processador i amb prou feines pagina a disc dur.
El que si que és cert és que, a l'altre post que has fet, tenies un  munt d'aplicacions corrent simultàniament, fins i tot tres instàncies de l'mplayer, fet el qual pot fer renquejar una màquina com la teva (amb no massa ram i no sobrada de processador).

En tot cas, cal tenir present que el fet de que un ordinador vagi "lentorro" no pot ser una apreciació subjectiva, sinó que s'ha de fonamentar en medicions reals. Aleshores, a fi de poder determinar una mica més la realitat de la teva apreciació, cal que facis més proves amb la comanda top a fi de veure quines aplicacions carreguen més el teu sistema i quines menys.

---

### Post by pserra on 2008-01-29
Merci pe'ls teus sabis consells Papapep.
El dia que em vagi tant 'lentorro' miraré la comanda top a veure amb que difereix amb la d'avui....Ara ja fa   3 hores que va el portàtil i encara va marxant.... veig que l'icona del processador la tinc al màxim però  de moment no tant lent com ahir.

Una pregunta... al quindos  hi ha la possibilitat de des fragmentar els disks i diverses 'utilitats' per mirar errors de registres i per fer neteja de arxius 'inutils' 
per tal d'optimitzar el sistema.
En Ubuntu hi ha alguna cosa similar??  recordo haver llegit alguna cosa fa  temps, potser en aquest fòrum d'una utilitat  però que es deia que no era massa útil. Es cert?
Merci.

---

### Post by patrickfromspain on 2008-01-29
no has de desfragmentar el disc, no fa falta. A linux NO hi ha registre, no has de netejar res.

L'unic que pots fer, si de cas, es un sudo apt-get clean, que netejara els paquets que ja t'has baixat (es queden guardats a /var/cache/apt/archives). Ara mateix, en un Hardy instal·lat fa uns quants dies, hi tinc casi 700mb de paquets.

salut!

---

### Post by pserra on 2008-01-29
Acabo de tornar-ho a mirar el resultat del top  i ja m'ha pujat el consum  del processador al 64%, i una pregunta... el valor del costat (34.8%sy) que és??
Merci




top - 19:46:04 up  3:31,  1 user,  load average: 6.19, 5.40, 5.74
Tasks: 139 total,   8 running, 131 sleeping,   0 stopped,   0 zombie
**Cpu(s): 64.2%us, 34.8%sy,  0.7%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si**,  0.0%st
Mem:    515708k total,   509808k used,     5900k free,     5628k buffers
Swap:  2104468k total,   154248k used,  1950220k free,   217208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6492 root      25   0  2364 1048  832 R 47.1  0.2 101:53.91 top
 6185 pere      15   0  110m  21m 9932 S 23.6  4.2  49:29.69 ktorrent
 4989 root      16   0 88684  20m 6296 R 12.9  4.1  17:07.04 Xorg
27661 pere      15   0 33024  18m  15m R  6.0  3.6   0:02.91 konsole
 6137 pere      15   0 97.9m  20m  10m R  5.6  4.0   7:29.90 amule
 6184 pere      15   0  250m 104m  23m S  3.3 20.8  14:56.21 firefox-bin
 5767 pere      15   0 20196 4764 4336 S  0.7  0.9   0:25.48 gnome-screensav
 6246 pere      39  19 71864  11m 3688 S  0.7  2.4   1:41.00 beagled-helper
 5687 pere      15   0 17968 8008 6412 S  0.3  1.6   0:39.36 metacity
27734 root      15   0  2364 1176  876 R  0.3  0.2   0:00.44 top
    1 root      18   0  2952  508  460 S  0.0  0.1   0:01.42 init
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      34  19     0    0    0 R  0.0  0.0   0:00.03 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 events/0
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
root@Ubuntu:/home/pere#

root@Ubuntu:/home/pere#

---

### Post by papapep on 2008-01-29
La primera mesura (us) són els processos que ha invocat directament un usuari (**us**er), la segona (sy) són els que ha invocat "automàticament" el sistema operatiu (**sy**stem).

---

### Post by pespin on 2008-01-30
Nomes comentar que no cal estar loguejar com a root per a fer la ordre 'top'!

---


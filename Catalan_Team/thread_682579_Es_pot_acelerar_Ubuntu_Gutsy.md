---
title: "Es pot acelerar Ubuntu Gutsy?"
date: 2008-01-30
forum: Catalan Team
---

### Post by antiheroes on 2008-01-30
M'agradaria saber si hi ha qualque manera d'acelerar gràficament l'ordenador, encara que sigui qualsevol cosa per obrir les finestres més ràpidament!

El meu ordenador té les següents carecterístiques: Toshiba Satellite A110-179 CORE DUO T2250 8 1730 Mhz. La targeta gràfica és: Intel 945GM de 128 Mb de Ram DDR2. I 1024 de RAM

Gràcies!!

---

### Post by papapep on 2008-01-30
Què entens per "obrir finestres"? Quan engegues els programes? O obrir una finestra nova al firefox? per exemple. 
Dóna'ns un exemple concret de què vols accelerar.

---

### Post by antiheroes on 2008-01-30
Acelerar gràficament.... és a dir, que els programes s'obrin més aviat o navegant per les carpetes sigui més ràpid. Es  que per exemple, la primera vegada que obri el firefox, es torba un poquet en obrir-se i després va més ràpid. El mateix amb la resta de programes...

---

### Post by papapep on 2008-01-30
Però és que en mostrar-te els programes en la seva arrencada no intervé només la targeta gràfica. El processador, el disc dur i la ram també fan "alguna que altra" feina.
Per això mateix, quan ja tens, per exemple, el firefox engegat triga molt poc en obrir-te noves finestres, ja que ja ho tens a la ram i, bàsicament, se n'encarreguen aquesta, la memòria de la gràfica i, depenent del programa en més o menys mesura, el processador.

Entens ara que la resposta a la pregunta no és tan simple ni directa com a tu t'agradaria?? :-)

---

### Post by antiheroes on 2008-01-30
Sí, això que m'has explicat ja ho sabia. Però vull saber si hi ha qualque cosa per accerlerar l'ordenador, no se si m'entens... Per a que arranqui més ràpid en el moment d'encendrer-lo, que obri els programés més ràpid, etc. Segurament no hi ha res, però només vull saber si existeix qualque cosa. Encara que sigui per accelerar el processador, la targeta gràfica o la memòria RAM.

De totes formes, gràcies per contestar!:)

---

### Post by CarlesOriol on 2008-01-30
El problema de la teva pregunta és que és massa extensa... i on no cal acceleració es precisament on ho demanes a la part gràfica.

1. Openoffice: Hi ha un applet per pre-carregar el nucli i que així s'obri rapidament (el que fa es sols mostrar-se ja que llavors està tota l'estona obert).

2. L'escriptori es pot multithreadejar la càrrega canviant la forma d'inici dels serveis.
Però et donarà més problemes que alegries.

... etc...

També pots fer tonteries destructives com overclockejar la gràfica o posar que el disc dur estigui sempre funcionant però sols aconseguiràs carregar-te el maquinari.

---

### Post by papapep on 2008-01-30
> Sí, això que m'has explicat ja ho sabia. Però vull saber si hi ha qualque cosa per accerlerar l'ordenador, no se si m'entens

Jo t'entenc perfectament, però ja t'hem explicat que la resposta no és directe ni simple.

---

### Post by antiheroes on 2008-01-30
És a dir, que com tenc l'ordenador éstà molt bé, no? La veritat és que és més ràpid que fa un any, quan tenia Windows XP.

Una qüestió més: un familiar meu té un ordenador de torre amb processador Pentium IV 3.2 GHZ, 512 MB RAM i gràfica ATI 128 MB. El SO és Windows XP professional, i vaig fer una prova a me'm quin s'encenia més ràpidament i va ser el windows abans que l'ubuntu. Deu ser pel meu processador, per què el meu ordenador és portàtil i la gràfica està integrada, o per què? Tranquils, no em pens tornar passar a windows. La veritat, es que a l'Ubuntu no se m'ha penjat ni el firefox encara i a l'ordenador que us estic parlant qualque vegada es penja, encara que no molt!

PD: Les característiques del meu ordenador estan a l'inici del post!

Gràcies!

---

### Post by pespin on 2008-01-30
Si vols que el firefox o alguna aplicació se't obri abans potser podries provar-la d'iniciar quan arranqui l'ordinador. Així tarda més en arrancar l'ordinador però després a l'hora d'anar obrint-les va lleugerament més ràpid.... però la veritat esk són molts problemes per a la poca avantatja que et dona :)

---

### Post by ilku on 2008-01-31
Hola company:
Nomes et volia dir que si vols comparar velocitat d'encendre fiestres i ubuntu, ho facis a la mateixa maquina, et trobaràs alguna sorpresa. Potser l'ubntu per una casualitat és mes lent (pot passar si el finestres esta acabat d'instalar) però llavors fica-li un antivíric al finestres i veuràs el temps. O simplement utilitza el finestres un temps (1 mes per exemple) sense ficar-hi res nomes navegant i despres compara amb 1 mes d'ubuntu (utilitzant el mateix, obrint els mateixos continguts, etc)
(ja no parlem de comparar amb un vista, que em sembla que no cumpleix ni requisits minims)

La velocitat és raonablement alta en un Ubuntu. Potser tens activats efectes d'esciptori o alguna cosa així. Proba a activar nomes els serveis necessaris, i a treure efectes, aixó potser ajuda

---

### Post by eselma on 2008-01-31
> **antiheroes said:**
> ...Però vull saber si hi ha qualque cosa per accerlerar l'ordenador, no se si m'entens... Per a que arranqui més ràpid en el moment d'encendrer-lo, que obri els programés més ràpid, etc. Segurament no hi ha res, però només vull saber si existeix qualque cosa. Encara que sigui per accelerar el processador, la targeta gràfica o la memòria RAM.

Quant a la "velocitat d'arrencada" és un terme sovint enganyós. Quant arrenques* Hasefroch* (també conegut com a finestres). no s'engeguen tots els serveis. De fet, després d'aparèixer l'escriptori, encara hi ha activitat de diac dur. Per usar altres serveis, caldrà engegar-los també més endavant. En canvi, els sistemes *NIX (GNU/Linux entre ells) arrenquen un bededéu de serveis, fan comprovacions específiques, i cada x arrencades repassen les particions de disc per veure si s'ha escolat algun error. 

A banda d'això, sovint tenim temptacions d'instal·lar programari que necessita altres serveis (Ex: un programa de facturació que instal·la un servidor de base de dades, encara que aquell dia no l'usis per a res) o també "embellidors d'escriptori", com el *Compiz* i companyia, que també ajuden a ralentir l'arrencada i el sistema. Naturalment, si tens alguns* amules* i* ktorrents* treballant, la sobrecàrrega de CPU, disc i ample de banda pot ser important, encara que no ho vegis directament. Jo no uso aquests "xupòpters", i la màquina em va prou ràpida.

Pel que fa a "accelerar el processador", pensa que el fabricant sap prou bé del que aquest és capaç i el subministra al màxim rendiment que és possible. Ell l'ha creat, i ho sap millor que nosaltres. Com al cotxes, pot fer-hi una mica de "tuning": augmentar la velocitat de rellotge, instal·lar un radiador monstruós, etc, cosa que també interessa als fabricants, perquè moltes CPUs moren prematurament (i no es fa pública la defunció, es clar). 

Com sempre, la millor solució per accelerar una màquina, és treure-li "pes" inútil. És millor tenir RAM suficient per als processos que tinguis engegats. Les altres solucions acostumen a ser enganyoses.

---

### Post by patrickfromspain on 2008-01-31
Que el windows sigui mes rapid a l'arrancar que ubuntu es molt possible (sempre i quan es tingui un sistema net). En el meu cas, passa. El windows XP amb Nod32 arranca més ràpidament que l'Ubuntu. Pero es clar, s'ha de tenir en compte una cosa molt important, i es la propia manera d'arrancar. Ubuntu ha de carregar tots el móduls a l'arrencada, comproba qué necessita i, si ho té, ho carrega. Windows no ho fa això. I es precisament el punt en el que Ubuntu (o qualsevol altre linux, pel cas) es superior: si canvies el maquinari, carregarà uns altres móduls i a correr. Amb windows, et trobaras una pantalla blava i un reset i l'hauras de reparar (o, en el pitjor dels casos, reinstal·lar).

salut!

---

### Post by kukat on 2008-01-31
Pots accelerar el Firefox[ seguint aquestos pasos]("http://loscazadoreslinux.wordpress.com/2007/11/14/acelerar-firefox/")

I respecte a Ubuntu, prova de llevar alguns efectes, pot ser el tingues molt "carregat".

Salut!

---

### Post by mcako on 2008-01-31
Aquí tinc una cosa que potser et pot ajudar, quan vaig instal·lar Ubuntu vaig anar seguint un manual on explicava com optimitzar-lo perquè anés una mica més ràpid (faig la traducció):

[LIST=1]
[*]**Memòria SWAP**: Per defecte linux te el valor d'ús de SWAP al 60%. Això significa que farà bastant d'ús de la memòria d'intercanvi. Resulta útil si tenim un servidor amb gran càrrega de treball i poca RAM, i si compilem freqüentment aplicacions molt grans. Però en un sistema d'escriptori, amb varies aplicacions petites executant-se, podem baixar aquest valor al 10% perquè el nucli utilitzi més sovint la memòria RAM (més ràpida) i recorri menys a la memòria d'intercanvi (SWAP).
Per fer això, obrim una terminal i fem el següent:
1- Consultem el valor inicial:
**sudo cat /proc/sys/vm/swappiness**
Després d'introduir la contrasenya, ens mostra un valor de 60 (si ja ens mostra 10, no cal fer res).
2- Provem provisionalment com respon el sistema al baixar el valor:
**sudo sysctl -w vm.swappiness=10**
3- Executem un parell d'aplicacions i si el resultat és satisfactori, anem a modificar un arxiu de configuració perquè el canvi sigui permanent:
**sudo gedit /etc/sysctl.conf**
i afegim al final la següent linia: **vm.swappiness=10** i guardem els canvis.

[*]**Xorg:** Podem baixar la profunditat de color de 24-bit a 16-bit notant poca diferència. Això redueix l'ús de la memòria de la targeta gràfica.
Obrim una terminal:
**cd /etc/X11**
Ara anem a modificar l'arxiu de configuració **xorg.conf**:
**sudo gedit xorg.conf**
Busquem la linia que posa DefaultDepth (section screen) i modifiquem el seu valor de 24 a 16 i guardem els canvis. (personalment no ho he fet servir)

[*]**Serveis Innecessaris:** Ubuntu inicia un seguit de serveis que de vegades són innecessaris. Si deshabilitem els que no necessitem evitarem consumir memòria inútilment.
Una manera fàcil i còmoda de veure quins serveis s'executen i poder desactivar-los és instal·lant el Boot-Up Manager ([http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)). Et mostrarà la llista de serveis i una petita descripció del que fa cadascun. Pots obrir-lo des del menú Administració.  
Alguns dels serveis que vaig desactivar eren:
[INDENT]laptop-mode >>> per portàtils o pc's moderns
acpi-support >>> per portàtils o pc's moderns
acpid >>> per portàtils o pc's moderns
hotkey-setup >>> per portàtils o pc's moderns
powernowd >>> per portàtils o pc's moderns
Vaig activar el servei hdparm. Amb aquest servei optimitzem l'accés a disc.
pcmciautils >>> Només s'usa per portàtils que tinguin targetes PCMCIA.
rsync >>> Eina per transferir arxius per fer còpies o mantenir un mirall sincronitzat.[/INDENT]
Suposo que tu tenint portàtil no podràs desactivar gaires dels serveis que he esmentat.

[*]**OpenOffice:** Una de les aplicacions més pesades és OpenOffice. Utilitzant la memòria caché intentem que s'executi més ràpid.
Obrim OpenOffice. Per exemple: menú Aplicacions, Oficina, OpenOffice.org Word Processor.
Entrem al menú Tools, apartat Options, seguidament anem a l'apartat Memòria. Canviem el valor "d'Ús per a OpenOffice" a 128 i de "Memòria per objecte a 20. Acceptem els canvis.
Al executar OpenOffice repetides vegades notarem la diferència de càrrega.
[/LIST]

---

### Post by antiheroes on 2008-01-31
Només tenc l'efecte lámpara mágica... l'expo i el famós cubo. res més!

---

### Post by antiheroes on 2008-01-31
Tens raó Patrick. La veritat és que el windows no és molt més ràpid. I també té el NOD 32, però me va sorpendre, encara que la teva explicació és totalment lògica. Gràcies! M'encanta aquest fòrum. Sempre contestau!

---

### Post by eselma on 2008-01-31
> **mcako said:**
> 

[LIST=1]
[*]**Xorg:** Podem baixar la profunditat de color de 24-bit a 16-bit notant poca diferència. Això redueix l'ús de la memòria de la targeta gràfica.
Obrim una terminal:
**cd /etc/X11**
Ara anem a modificar l'arxiu de configuració **xorg.conf**:
**sudo gedit xorg.conf**
Busquem la linia que posa DefaultDepth (section screen) i modifiquem el seu valor de 24 a 16 i guardem els canvis. (personalment no ho he fet servir)
[/LIST]

Efectivament, reduint la resolució per píxel de 24 (a la pràctica 32, 4 bytes) a 16, el rendiment de la tarja gràfica augmenta gairebé al doble. Només es pot veure la diferència si es tracta de fotografies molt ben calibrades i tonalitats suaus. Per descomptat, la velocitat de càrrega dels programes no queda massa afectada, i només s'accelera el "rendering" (certs jocs, per exemple). 

El problema és que sovint *Compiz* i similars no funcionen a menys de 24 bpp (bits per píxel). Com a mínim, a les meves targes nVidia. Tot depèn del que vulguis fer.

---

### Post by antiheroes on 2008-01-31
Al final crec que deixaré l'ordenador tal com el tenc, que va molt bé. La meva configuració de COMPIZ és la 'normal' i només li he afegit el 'cubo' (poal en mallorquí que és molt ridícul xD), així que no afecta molt. Estic molt content de com funciona la màquina, només volia resoldre un parell de dubtes, i cercar qualque possibilitat, però me basta! Moltes gràcies!

---

### Post by eselma on 2008-02-02
Una mica *offtopic*:[COLOR="Red"] poal[/COLOR] és un terme d'ús general en català, i no pas un localisme mallorquí. Jo no el veig pas ridícul, no ho sé vosaltres. Evidentment, no sentireu gaire aquest terme a Barcelona. 

Tanmateix, a banda del càntir amb un broc, es refereix a una galleda, no pas a un figura geomètrica. Els hexaedres regulars, en català, reben el nom de "cub". O sigui que abans de desactivar el *Compiz*, jo també tenia el cub giratori a l'escriptori. Aviat, però, em sembla que veurem més cubs als nous escriptoris lliures.

---

### Post by mcako on 2008-02-02
A veure, un localisme és, és propi del dialecte mallorquí, per molt que surti al Diccionari d'Estudis Catalans hi han paraules que només s'utilitzen en determinades regions, per exemple, el meu company de pis diu "llosca" en comptes de dir "burilla" (punta de cigarret), òbviament a mi no  se'm sentirà mai dir "llosca". El que passa és que en determinats llocs com el País Valencià, Mallorca, Eivissa, i Menorca el català s'ha vist molt desprestigiat fins al punt de considerar-se pagesot que algú parli en tals dialectes, és la diglòssia que ha anat sembrant el PP durant aquests anys, que la gent se senti ridícula parlant català és un dels seus objectius.

---

### Post by antiheroes on 2008-02-02
Bé, jo no vull entrar en conflictes polítics... El mallorquí és una variació dialectal del català, això està provat científicament. Jo només volia fer un petit acudit. Només ens diferenciam en l'ús de paraules sense importància, i això és important, perquè vol dir que hi ha varietat lingüística, a més del famós article salat. Bé, no vos enfadeu! xD

---

### Post by papapep on 2008-02-02
Si aquí alguna cosa et garantirem és que tots hi som ben rebuts i que cadascú parla a la seva manera (ens agrada "parlar" amb correcció, això si) sense cap mena de problema (jo el que no he entès és per que titlles la paraula "poal" de ridícula, precisament la diversitat és la que ens enriqueix a tots).

Salut a totes les variants del català/valencià/mallorquí/alguerés/el_que_sigui !!! ;-)

---

### Post by mcako on 2008-02-02
Jo ho deixaria en:
Salut a totes les variants del català (valencià/mallorquí/alguerès/el_que_sigui)! :mrgreen: ;)

---

### Post by lluisanunez on 2008-02-02
Sense ànim d'entrar en polèmica, **poal** també es fa servir a més llocs:
[http://dcvb.iec.cat](http://dcvb.iec.cat)
1. Galleda (Cerdanya, Vallès, Barc., Maestrat, Morella, Val., Bal.); cast. cubo, pozal./

A part, el teu Firefox té moltes extensions? Això el pot alentir. Al meu portàtil el FF triga una estoneta a engegar-se la primera vegada...

---

### Post by eselma on 2008-02-03
> **lluisanunez said:**
> Sense ànim d'entrar en polèmica, **poal** també es fa servir a més llocs:
[http://dcvb.iec.cat](http://dcvb.iec.cat)
1. Galleda (Cerdanya, Vallès, Barc., Maestrat, Morella, Val., Bal.); cast. cubo, pozal./


Podeu afegir-hi el Priorat i segurament el Baix Camp i la Ribera d'Ebre, entre d'altres.

Justament a això em referia. Aquí ningú no s'enfada per les variants del català; això ens enriqueix a tots (i a totes). Senzillament és xocant que a vegades ens sembli ridícul de ser com som, no? Això no són temes "polítics": el programari lliure vol adaptar-se a l'usuari, i també som tan lliures de triar la variant dialectal que volem com d'usar *Python* o _Perl_... ([COLOR="Green"]*Ai! que em sembla que això sí que és un tema punxegut... bé oblideu-ho, si us plau*[/COLOR]).

---


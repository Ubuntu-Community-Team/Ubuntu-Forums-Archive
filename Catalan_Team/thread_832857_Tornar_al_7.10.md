---
title: "Tornar al 7.10"
date: 2008-06-18
forum: Catalan Team
---

### Post by rogespierre on 2008-06-18
Des què vaig actualitzar a la versió d'Ubuntu 8.10 em va cada cop pitjor, lent, inestable.. Se'm penja sovint, alguns progames o no s'obren o desapareixen, l'àudio i el vídeo em dónen molts problemes... També es cert que el meu pc ja te tres anys ben bons. La qüestió és què l'Ubuntu 7.10 m'anava com la seda, em recomaneu tornar-hi? Com es fa?

Gràcies

---

### Post by guillemsola on 2008-06-18
Si no és restaurant una copia de seguretat penso que potser el que pots fer és tornar a instal·lar una 7.10 i després muntar l'actual carpeta home a la nova instal·lació. Am això recuperaràs els usuaris i preferències.

Jo tinc la home en una partició separada per més comoditat a l'hora de fer coses com aquestes però no he provat mai si funciona de veritat. Amb el gparted pots crear noves particions i editant el /etc/fstab modificar on apunta la nova partició home.

Recorda però, de fer còpies de seguretat ( per exemple amb una live i dd ) per si hi ha problemes.

Salut

---

### Post by Miquel Ubuntero on 2008-06-18
Hola companys.
Estic d'acord que el millor és tindre el "home" en una altre partició per més comoditat. Si serveix d'informació també he tingut bastants problemes amb Ubuntu 8.04 i finalment he formatat i posat de nou Ubuntu 7.10 que de moment sembla que tira millor. Que crec és la manera més fàcil i sencilla de tirar enrere.
Salut!

---

### Post by PellRoja on 2008-06-18
a mi les actualitzacions sempre m' han funcionat malament. Jo tinc la última versió instal·lada neta i em funciona bé.

Tot i així no se si es pot tornar a versions anteriors després d' una actualització. per internet si busques, no ho recomanen.

Jo obtaria per fer instal·lació nova. proves la 8.04 neta, a veure que tal et va, i si no funcionen coses, llavors si que tornaria a 7.10

;)

---

### Post by kukat on 2008-06-18
Jo tinc el ubuntu gutsy gibbon, ja que vaig estar lluitant per fer anar la tarja ATI Radeon 9550 i no va haver manera. Així que...estic de meravella amb el Gutsy!!!! I ara amb el Firefox 3....jejjeje

---

### Post by oriolsbd on 2008-06-18
Hola, Rogespierre.

Ara ja no ho pots fer, però fa poc he sentit d'un programa que potser per a properes vegades pot anar bé. Es diu Remastersys. Precisament aquest mes hi ha un article a la revista Linux+ on en parlen.

Aquest programa, en línies generals, el que fa és crear-te un CD/DVD d'instal·lació amb el paquets i les configuracions que tens tu al teu equip. Com si fos la teva pròpia distribució de Linux. :-)

ULL: Encara no he tingut temps de provar-lo, i no sé què tal funciona la instal·lació a partir d'aquest CD/DVD, ni si el sistema funciona directament després de la instal·lació o si hi ha alguna cosa que queda a l'aire. De tota manera, quan tingui temps de comprovar que va bé, la meva idea és, cada cop que vulgui fer un Upgrade de versió, primer em crearé un CD de la meva versió actual amb Remastersys (més backup dels meus fitxers de dades). Després, provaré l'Upgrade d'Ubuntu normal. Si veig que no em va bé, faig la instal·lació del CD que m'hagi creat el Remastersys. A males, si després d'això no em funciona, sempre tinc com a última opció reinstal·lar Ubuntu (havent de reinstal·lar posteriorment tots els programes que tinc ara).

Salutacions,

Oriol.

---

### Post by rogespierre on 2008-06-18
gràcies a tots! però més que res no entenc gaire cosa, mai he formatat un pc ni reinstalat un SO :):):) i a més sóc de lletres

pellroja: que vols dir amb una instal·lació neta? com se fa? per si t'es d'ajuda sapigues que compto amb una versio en cd del 8.4

angry

> **angrychai said:**
>  instal·lar una 7.10 i després muntar l'actual carpeta home t

ok, però com instal·lo de nou el 7.10...?

---

### Post by kukat on 2008-06-18
Ostres, això del Remastersys hi haurà que mirar-ho bé, per què pot solucionar molts maldecaps alhora de actualitzacions i demés coses que pugen sortir mal.

---

### Post by Curial on 2008-06-18
Encara estic amb la gutsy, em va de perles i m'esteu acollonint.

Algun dia hauré de fer el canvi, em caldran ànims però, us ho aviso.

Salut

---

### Post by oriolsbd on 2008-06-18
Hola, Rogespierre.

Quan el Pellroja diu "fer una instal·lació neta" vol dir instal·lar el Sistema Operatiu del tot des del CD. És a dir, que et quedaries amb l'Ubuntu tal i com tenies el primer dia. Bé, també conservaries tot el que tens a /home/els_teus_usuaris si a la instal·lació li dius que no formati aquesta partició (si és que ara la tens com una partició separada). En aquest cas, podries fer-ho tant amb un CD de la 7.10 com de la 8.04, depenent de la que prefereixis. Malgrat els problemes que has tingut amb la 8.04, crec que si instal·les un Ubuntu "net", és millor fer-ho amb la versió més nova (i més si tenim en compte que la 8.04 és una LTS). Una instal·lació "neta" no acostuma a donar massa problemes, però s'ha de tornar a reinstal·lar i configurar tot.

Quant al fet que tinguis un PC de 3 anys, no hauries de tenir cap problema. El meu en té 5 i vaig perfectament (només hi he ampliat la memòria).

Sobretot, et recomano que et facis una còpia de seguretat (en un CD/DVD o en un disc dur extern) dels teus fitxers de dades.
Kukat, estic començant a provar ara el Remastersys en una màquina virtual. Ja et diré què tal. Apart de l'article que us he comentat, també he trobat aquest altre a Ubuntu Geek:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
De tota manera, per si el vols anar provant, en tots dos articles hi he trobat una errada, i és que no és correcta la línia que afegeixen al sources.list. Suposo que els de Remastersys deuen haver modificat la seva URL. La línia correcta seria:
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

Ja et comentaré què tal va el programa.

Salut!

---

### Post by guillemsola on 2008-06-18
Per fer una instal·lació neta primer ens podries dir quins S.O. tens al PC i les particions que tens així com l'espai de disc dur lliure.

pots fer des d'una terminal:

> sudo gparted

i adjuntar una captura de pantalla del programa. Amb això et podem dir com tens el tema de les particions. Si tens prou espai al disc dur lliure pots redimensionar el disc dur per crear espai per poder instal·lar un nou linux. Pots per exemple conservar l'Ubuntu que tens ara i afegir-n'hi un de nou. Després a l'hora d'arrencar tries amb quin vols iniciar l'ordinador. Després hi copies la teva partició \home de la instal·lació que tens ara i festa.

Si tens por a perdre les coses del pc o vas just d'espai tampoc no descartis comprar un disc nou que pel que valen et pots estalviar molts mal de caps.

---

### Post by ealbert on 2008-06-19
Ahir, vaig estar a punt d'obrir un nou fil per problemes similars als que indica Rogespierre.
En el seu dia l'actualització al 8.04 hem va fallar i per fer el canvi vaig optar per netejar el disc dur i instal·lar-ho tot des de zero. 
Al principi tot anava bé, "però" les petites incidències que notava, les atribuïa a comentaris que llegia en general culpant al firefox per no ser una versió final i pensava, ara quant surti la versió definitiva s'acabaran solucionant els problemes. 
En el meu cas no ha estat així, l'ordinador de tant en tant s'hem alentia, la pantalla del firefox es tornava de color gris i la lentitud es feia més palesa que mai. Finalment i coincidint amb la versió final del firefox 3.0, es tancava per motu propi i es negava a tornar a obrir-se (ja hem veia navegant de nou amb el "finestres"), també tenia problemes amb el procesador de textes del OpenOffice.
Aleshores, s'hem va acudir des del terminal teclejar "free" i la informació que vaig obtenir no hem va fer el pes, veia molta memória ocupada i hem va mosquejar. 
Com disposaba de 1 GB de memòria en dos mòduls, vaig treurem un i vaig provar de nou el sistema, seguia fallant; aleshores vaig substituir el mòdul instal·lat pel que havia tret en primer lloc i en aquest moment s'han acabat tots els problemes.
En el meu cas tot ha estat **culpa de la memòria** i per tant els meus problemes no han estat causats pel Ubuntu, el Firefox o la resta de programes.
Ara sols disposo de la mitat de la memòria, però el meu PC va fi com una seda.
He volgut comentar·ho per si la meva experiència li pot fer servei a la resta de companys.

---

### Post by rogespierre on 2008-06-19
angrychai: posant "sudo gparted" em diu command not found

oriol: bé, doncs faig còpia de seguretat de totes les dades (la majoria les tinc en un disc dur extern) i amb el cd del 8,4 linstalo de nou. Tinc una partició petita amb el linux i una altra amb el windows xp, a l'hora de instal·lar-ho ja em dirà a quina partició ho vull instal·lar? 

gracies

---

### Post by oriolsbd on 2008-06-19
Hola de nou.

Des de Synaptic pots instal·lar-te el paquet "gparted".

En principi, les dades que tinguis en el disc dur extern no cal fer còpia. És més que res les dades que tinguis al PC. Quan facis la instal·lació, podràs dir-li a quina partició fer la instal·lació. Abans de fer-ho, convindria tenir la informació del gparted que t'ha comentat l'Angrychai.

---

### Post by rogespierre on 2008-06-19
aquí t'adjunto la info que em demanaves. Bé, de fet ja ho sabia que ho tenia així, el que no se es pq no apareix en aquest programa les dades de la partició linux...

[IMG]http://img80.imageshack.us/img80/2026/particionseo0.jpg[/IMG]

mmm, també he fet una còpia de la carpeta home, tot i que no hi tinc massa cosa, quan hagi reinstal·lat l'ubuntu l'he de subsituir meu dit?

---

### Post by oriolsbd on 2008-06-19
Hola, sí que apareix la partició Linux. És la /dev/sda3 (tipus "ext3") que et diu que té "/" com a punt de muntatge. Per cert, tens només un disc dur? O en tens més d'un? El gparted només et mostra la informació disc a disc. Si tens un altre disc, pots veure les seves particions a través del menú "Dispositius" (em sembla que era aquest). De moment, si no tens més discos durs, aquí podem veure que no tens en una partició separada el "/home".

Abans de fer res, crec que seria interessant fer cas de l'Ealbert, i com a mínim comprovar que no hi hagi cap problema a la memòria del teu ordinador. Si el problema fos la memòria, potser canviant-la ja no caldria reinstal·lar res. Per fer un test de memòria, a l'inici de l'arranc del PC hi tens una opció del Grub que diu "... memtest ..." (no recordo exactament el nom de l'opció). Et farà una comprovació de la memòria (sense arribar a entrar en Ubuntu).

Salut!

---

### Post by guillemsola on 2008-06-20
Vas pel bon camí, instal·la l'ubuntu de nou (no fa falta que desinstalis el vell per si no et convenç el canvi).

Des del nou ubuntu li copies la carpeta que tindràs a /media/sda3/home o a la copia de seguretat que has fet.

A la carpeta home i ha una subcarpeta per cada nom d'usuari creat al sistema. Allí s'hi desen totes les teves preferències i arxius de configuració personals. A la nova instal·lació que facis et recomanaria crear l'usuari amb un nom diferent perquè no tingui conflictes amb el que copies de la configuració anterior. Posteriorment t'identifiques amb el nom d'usuari que has copiat i després si vols elimines l'usuari creat durant la instal·lació.

Ja diràs.

sort!

---

### Post by rogespierre on 2008-06-20
gracies angrichay (ho he de llegir tot 2 o 3 vegades pero ho vaig entenent) 

a veure, la carpeta home que tindre a la copia de seguretat la faig servir per substituir la home de la nova instal·lació? o nomes hi afegeixo la carpeta "roger" (és el meu nom) que tindre a la copia de seguretat?

ho dic pq no se si la puc liar molt substituint aquesta carpeta a sac, pq llavors lusuari q haure creat fent la nova instal·lació no mel carrego?

---


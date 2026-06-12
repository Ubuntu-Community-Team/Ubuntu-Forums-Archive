---
title: "[SOLVED] Passar un disc amb Ubuntu a una altra màquina"
date: 2007-12-24
forum: Catalan Team
---

### Post by lpargemi on 2007-12-24
Hola

He tingut un daltabaix, i se m'ha mort la placa base de la màquina -suposo-. Era un PC clònic del seu moment sense gaires peculiaritats.

Ara tinc un disc amb Ubuntu 7.04 instal.lat i en funcionament, amb la partició de swap al mateix disc físic (amb la mida que el sistema va determinar al moment de la instal.lació, m'imagino que en funció de la memòria).

Voldria fer anar el mateix sistema operatiu [vull dir el mateix disc que ja el té instal.lat], amb els menors canvis possibles sobre una nova placa base, però que segur que no serà igual: correrà més, segur que tindrà més RAM; i no hi entenc gens amb targetes de vídeo, però pel que he anat seguint al fòrum és una de les coses dóna problemes.

[Ara mateix no tenia previst canviar el PC, així que el pressupost si que serà un problema].

Les preguntes que us faig son:

1: Té sentit pretendre que el sistema m'arrenqui amb el disc que ja tinc, ni que sigui en mode segur, i anar adaptant els canvis poc a poc (per exemple la mida del disc de swap, la ubicació del DVD, la targeta de xarxa...)

2: Si tingués sentit, He de tenir en compte alguna característica especial a la placa base que em facilités la operativa?

3: Si no hi res a fer - i cal instal.lar-ho tot de zero - quina mena  de targeta de vídeo m'aconsellaríeu que estigui ben suportada per Ubuntu. [No faig anar jocs, només m'interessaria que anés el Google Maps; però ara mateix no em funcionava i tampoc em va representar cap gran desconsol].

Agraït

Lluís

---

### Post by orestesmas on 2007-12-24
> **lpargemi said:**
> Hola

1: Té sentit pretendre que el sistema m'arrenqui amb el disc que ja tinc, ni que sigui en mode segur, i anar adaptant els canvis poc a poc (per exemple la mida del disc de swap, la ubicació del DVD, la targeta de xarxa...)

Sí que té sentit, perquè precisament un nucli linux modular fa que carregui automàticament els mòduls necessaris per funcionar en cada maquinari concret. Si només fos pel nucli en canvi de placa hauria de funcionar sense problemes, sempre i quan el disc dur estigui ubicat a la mateixa interfície lògica que l'anterior (vull dir que si abans el disc era /dev/hda, ara ho hauria de seguir essent).

Ara bé, les X windows és diferent, perquè no es configuren automàticament segons el maquinari que detecten. El més probable és que no arrenquin a la primera, però no és res que no es pugui solucionar reconfigurant-les.

> **lpargemi said:**
> 
2: Si tingués sentit, He de tenir en compte alguna característica especial a la placa base que em facilités la operativa?

No se m'acut ara. Com més bona millor. ASUS o Gigabyte solen ser bones marques. Compta que si canvies la placa base gairebé segur que hauràs de canviar també el processador i la RAM. Si ara no pots, planteja't de buscar una placa de característiques semblants a la que tenies per poder aprofitar RAM i CPU, i tira amb ella fins que puguis fer una renovació més a fons.

> **lpargemi said:**
> 
3: Si no hi res a fer - i cal instal.lar-ho tot de zero - quina mena  de targeta de vídeo m'aconsellaríeu que estigui ben suportada per Ubuntu. [No faig anar jocs, només m'interessaria que anés el Google Maps; però ara mateix no em funcionava i tampoc em va representar cap gran desconsol].

Si és externa, escull ATI. Nvidia també és una opció però per tenir acceleració gràfica hauràs d'instal·lar controladors privatius.

Si està integrada en placa base, Intel també és una bona opció.

---

### Post by patrickfromspain on 2007-12-24
grafica NVIDIA!

Les tarjetes d'ati que tenen un bon soport amb el driver lliure son velles i el driver privatiu es pessim. El driver privatiu d'NVIDIA sense ser la canya, es molt millor. 

Si no.. una placa amb video integrat d'intel tambe es una bona opcio.

salut!

---

### Post by CarlesOriol on 2007-12-25
Estic totalment d'acord amb en Patrick, les ATI de moment sols donen problemes.

Si ets novell en el mon linux o és un ordinador per jugar una nvidia és la teva elecció.
Però tingues en compte que nvidia no és una gràfica lliure i que qualsevol problema estàs lligat a la bona voluntat d'aquesta empresa. (absent en molts cops com ja ha demostrat).
Però VIGILA!: Les gràfiques de la serie 8600 en endavant no estan suportades directament en la versió actual de l'ubuntu (malgrat estar-ho en les alfes de la propera) i hauràs de fer malabarismes per insta&#320;lar-les.

Si vols una màquina professional o un portàtil o valores principalment la teva llibertat una gràfica integrada intel és la solució.
Aquí ens trobem en una situació similar a l'anterior (malgrat no ser tant crítica). Amb les noves gràfiques d'intel no podràs tenir els efectes "guapos" d'escriptori fins a la propera versió d'ubuntu. PERÒ podràs insta&#320;lar el sistema sense cap problema.

---

### Post by eselma on 2007-12-25
> **patrickfromspain said:**
> grafica NVIDIA!

Les tarjetes d'ati que tenen un bon soport amb el driver lliure son velles i el driver privatiu es pessim. El driver privatiu d'NVIDIA sense ser la canya, es molt millor. 

Si no.. una placa amb video integrat d'intel tambe es una bona opcio.


A les dues màquines de sobretaula de casa hi tinc targes gràfiques *nVidi*a (de les sèries 6000 i 7000); hi tinc instal·lats els controladors privatius i la veritat és que fins ara no hi tingut problemes (llevat d'una 6600LE que senzillament no reconeixia el controlador lliure "nv"). Al portàtil hi tinc una *intel* integrada que va la mar de bé amb el controlador lliure.

A la feina tenia una *Radeon* (ATI) que anava regular (sense *Compiz, Beryl* ni altres caramels) i recentment me l'han canviat per un de nou amb tarja ATI (em temia el pitjor). Amb el controlador privatiu va la mar de bé i molt ràpid; però al magatzem hi tinc una altra ATI que vaig jubilar fa uns anys per problemàtica. Crec que amb ATI en mans d'AMD les coses ara van canviant, però en tot cas el canvi no serà immediat.

En fi, una excusa com una altra per desitjar-vos **[COLOR="Red"]BONES FESTES[/COLOR]** a tots els *forumaires*.

---

### Post by lpargemi on 2007-12-25
Moltes gràcies pels vostres consells.

El cas es que trobant-nos aquestes dates difícilment podré arreglar l'assumpte abans d'uns dies. Ja us mantindré informats.

Una altra qüestió: preguntant als proveïdors de màquines, pel què sembla ara tot el què és nou porta processador de 64 bits. 

Si canviés placa i CPU, suposo que la diferència ja seria massa radical pretendre que arrenqués amb el nucli que tinc ara. No he vist a les distribucions en català el que corre amb amd64, però suposo que instal.lant el genèric després podria adaptar la llengua.

Bon Nadal

lluís

---

### Post by CarlesOriol on 2007-12-26
El sistema en 64 bits funciona en català tal com dius. 

Però tingues en compte que al sistema en 64 bits hi haurà diversos programes que no et funcionaran i això pot ser un problema per un usuari novell (no sé si és el cas). Sempre pots installar el de 32 en una màquina de 64.

Alerta en les màquines noves!! Hi ha diverses plaques mare que no estan directament suportades (per tant no engega) així com (tal com et comentava abans) les nvidia de serie 8600 i superior. Es poden fer funcionar però també s'escapa del concepte posa-el-disc-i-ja-està ubuntaire.

---

### Post by lpargemi on 2007-12-26
Suposeu bé pel què fa al nivell d'usuari: sóc novell. Fa dies que vull presentar-me al fil però mai no m'hi poso [la mandra és per buscar una foto o un dibuix així per penjar-hi].

Us agraeixo de nou les observacions

lluís

---

### Post by lpargemi on 2008-01-03
Hola de nou

Després de les festes i de tot plegat he aconseguit aplegar el material i el temps necessari per provar de recuperar la màquina.

He muntat una placa base MSI amb un AMD64 4200+, i he aprofitat el sistema de discs que tenia (per això em calien dos connexions IDE).

El sistema ha arrencat, tot i ser preparat per a i386. L'única cosa que no ha anat bé ha sigut els gràfics: em donava un error al carregar la interfície gràfica i només podia arrencar amb la cònsola.  

He seguit els passos que s'indica a [guia-ubuntu.org]("http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%B3n_gr%C3%A1fica_VIA_/_ASROCK_/_S3G") per instal.lar aquest vídeo i tampoc va funcionar. 

La solució bona ha estat arrencar la màquina amb el live-CD que vaig fer servir per instal.lar l'Ubuntu, que ha arrencat bé el Gnome, i copiar el fitxer  /etc/X11/xorg.conf que funcionava a un disquet, per després arrencar  des de la cònsola i sobreescriure el que tenia al sistema. Després d'això tot ja ha funcionat bé. [Ho explico per si pot servir d'ajuda a algú][Tampoc sé si he fet alguna animalada flagrant]

Finalment una pregunta més: ara he passat a tenir 1.7 GB de RAM, i la meva swap és -encara- de 768Mb. Es suposa que l'he de canviar a 2x1.7=3.4 GB?  Des d'on és més recomanable fer-ho?

Bon any

Lluís

---

### Post by papapep on 2008-01-03
Jo tinc una màquina que faig servir de servidor de proves, que és un PIII a 1GHz, amb 1,8 GB de RAM, amb 800 Mb de swap i em va de conya, i gairebé mai em pagina. O sigui que no crec que et sigui massa problemàtic.
Recorda que aquesta manera de calcular la mida de la swap era, bàsicament, de quan els sistemes en tenien molta menys que actualment.

---

### Post by lpargemi on 2008-01-06
D'acord, ho deixaré així.

Gràcies a tots per l'ajuda, i com que ja funciona , tancaré el post.

---


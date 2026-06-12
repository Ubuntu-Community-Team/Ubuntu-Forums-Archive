---
title: "[SOLVED] Problemes instal·lació Gimp (problemes amb Automatix)"
date: 2008-01-04
forum: Catalan Team
---

### Post by Asus4 on 2008-01-04
Salut i bon any a tothom!

Feia temps que no escrivia per aquest blog, però la veritat és que hi anava passant de tant en tant.
El problema que em té intrigat és una mica peculiar... fa temps no se com però em vaig quedar sense el Gimp (l'editor d'imatges). Ara fa poc he actualitzat a Ubuntu 7.10 i pensava que ja el trobaria a faltar i me l'instal·laria a la mateixa actualització ja que en teoria ve amb la distribució...

No ha estat així i, per més inri, quan he volgut instal·lar-lo, he anat al Synaptic i m'han aparegut dos errors. Per tal que els pogueu captar millor he fet captures de les pantalles.

La primera:
[[IMG]http://img178.imageshack.us/img178/2792/capturagimpsynapticxu6.th.png[/IMG]](http://img178.imageshack.us/my.php?image=capturagimpsynapticxu6.png)

La segona:
[[IMG]http://img178.imageshack.us/img178/4796/capturagimpsynaptic2vx5.th.png[/IMG]](http://img178.imageshack.us/my.php?image=capturagimpsynaptic2vx5.png)


Gràcies i fins aviat!!
PD: durant la meva absència he tingut altres problemes amb l'Ubuntu que un amic m'ha ajudat a solucionar. Quan pugui explicaré què em va passar i com ho vam poder solucionar per tal que si a algú li havia passat o li passa pugui tenir una guia més d'on tirar.:)

---

### Post by papapep on 2008-01-04
Respecte el teu problema, cal que revisis l'apartat del Synaptic on especifiques quins repositoris tens accessibles i quins no, a fi de tenir-lo disponible.
Ara no sóc davant de cap Ubuntu i no puc mirar-te a quin repositori és.

Per cert, has provat a fer un:

```
sudo aptitude update
```

Abans d'intentar instal·lar-lo?

---

### Post by CarlesOriol on 2008-01-04
Pots mostrar la pantalla anterior sense els missatges d'error per que poguem veure el nombre de versió.

També estaria bé que ens copiesis l'arxiu /etc/apt/sources.list

---

### Post by Asus4 on 2008-01-05
Salut i Gràcies per contestar!!

He provat el que m'has dit papapep, i res de res. He vist com buscar els repositoris accessibles però no sé a on es troba el gimp.

D'altra banda, aquí poso el que has dit CarlesOriol:

La **versió del gimp** és aquesta:*** 2.4.0~rc3-1ubuntu7***
De tota manera, aquí teniu la captura:
[[IMG]http://img222.imageshack.us/img222/2379/capturagimpppr6.th.png[/IMG]](http://img222.imageshack.us/my.php?image=capturagimpppr6.png)

L'arxiu** /etc/apt/sources.list**:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

# deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

# Treviño’s Ubuntu Feisty EyeCandy Repository (GPG key: 81836EBF)
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

# deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
# deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END


Gràcies una altra vegada i fins aviat!!

---

### Post by papapep on 2008-01-05
> #AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END


Un dels problemes que tens és aquest. 

L'[Automàtix porta MOLTS problemes]("http://extralinux.net/?q=node/26") d'inconsistències a les bases de paquets.

Com que el Gimp és un paquet dels que instal·la "de sèrie" l'Ubuntu, encara és més estrany el que et passa. Per tant, el primer que t'aconsello és que esborris les línies que he comentat del teu sources.list i, seguidament facis un "sudo apt-get update" i un "sudo apt-get install -f".

---

### Post by Asus4 on 2008-01-07
Salut!

He fet el que m'has dit papapep: he modificat l'arxiu sources.list i he entrat les dues comandes a la consola. 
A partir d'aquí he tornat a intentar instal·lar el gimp a través de synaptic i també de consola. En el synaptic m'ha tornat a sortir el mateix, i a la consola m'ha aparegut un error semblant al synaptic, però us el poso aquí per tenir més informació del tema:

> joan@joan-desktop:~$ sudo apt-get install gimp
[sudo] password for joan:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
No s'han pogut instal·lar alguns paquets. Això pot ser degut a que vàreu
requerir una situació imposible o a que esteu usant la distribució
unstable i alguns paquets requerits encara no han estat creats o bé
encara no els hi han afegit.

Degut a que sols heu requerit una única operació, serà molt
probable que el paquet no sigui instal·lable i que s'hagi d'emetre
un informe d'error en contra d'aquest per a arxivar-lo.
La següent informació pot ajudar-vos a resoldre la situació:

Els següents paquets tenen dependències sense satisfer:
  gimp: Depén: gimp-data (>= 2.4.0~rc3) però no serà instal·lat
        Depén: gimp-data (< 2.4.0~rc3-z) però no serà instal·lat
E: Paquets trencats
joan@joan-desktop:~$ 


Cada cop entenc menys què passa...
però bé! Moltes gràcies i fins aviat!

---

### Post by papapep on 2008-01-07
> Cada cop entenc menys què passa...

Doncs és molt fàcil, que tens problemes amb la base de dades que controla els paquets i les seves dependències. Més que probablement gràcies a l'automàtix.

[COLOR="Red"]**Per cert! Què et diu el terminal en fer el apt-get install -f??**[/COLOR]

Prova a fer:

```
sudo aptitude purge gimp
```

Si et funciona (o sigui, que esborra el gimp), torna a fer els:

```
sudo apt-get update
```

```
sudo apt-get install -f
```

Si això també et funcionés, ja hauries de poder instal·lar el gimp de manera normal:

```
sudo aptitude install gimp
```

---

### Post by patrickfromspain on 2008-01-07
Si el que et diu en Papapep no et funciona, prova el següent:

gksudo gedit /etc/apt/sources.list

borra tot el que hi tens i posa-hi el següent:


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

#### GUTSY COMERCIAL ####
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

#### PAQUETS FONT
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

guardes, tanques i sudo apt-get update i torna a provar el que ha dit en papapep

salut!

---

### Post by Asus4 on 2008-01-08
He seguit els passos que m'heu anat indicant i sembla que ara tot funciona a la perfecció. He pogut instal·lar el gimp i l'he executat sense cap impediment!
Moltíssimes gràcies per l'ajuda!! Aquí us deixo una còpia de la consola de totes les comandes que m'heu dit i he anat entrant per tal de solucionar el problema. (és una miiiica llarg xD)
Fins aviat!!



> joan@joan-desktop:~$ sudo apt-get install -f
[sudo] password for joan:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4 wormux-data
Use 'apt-get autoremove' to remove them.
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 1 no actualitzats.
joan@joan-desktop:~$ sudo apt-get autoremove
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4 wormux-data
S'ELIMINARAN els següents paquets:
  python2.4 python2.4-minimal wormux-data
0 actualitzats, 0 nous a instal·lar, 3 a eliminar i 1 no actualitzats.
Es necessita obtenir 0B d'arxius.
Després de desempaquetar s'alliberaran 86,6MB d'espai en disc.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 128380 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant python2.4 ...
S'està desinstal·lant python2.4-minimal ...
Unlinking and removing bytecode for runtime python2.4
S'està desinstal·lant wormux-data ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
joan@joan-desktop:~$ sudo aptitude purge gimp
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
Els paquets següents s'han apartat:
  gimp-python 
Els paquets següents se suprimiran:
  gimp{p} 
0 paquets actualitzats, 0 instal·lats, 1 a suprimir i 1 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
Esteu segur de voler continuar? [Y/n/?] y
S'està escrivint la informació d'estat estesa... Fet
(S'està llegint la base de dades ... hi ha 126807 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant gimp ...
S'estan purgant els fitxers de configuració de gimp ...
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
joan@joan-desktop:~$ sudo apt-get update
Des:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-ca        
Des:2 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-ca  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-ca
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release              
Des:3 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/main Translation-ca [6978B]
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/restricted Translation-ca
Des:4 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/universe Translation-ca [1981B]
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/multiverse Translation-ca               
Des:5 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates/main Translation-ca
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates/restricted Translation-ca
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy Release                           
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates Release                         
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources         
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources         
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources           
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages          
Obj [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages        
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/main Packages                     
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy-updates/restricted Sources
8962B descarregats en 1s (8275B/s)
S'està llegint la llista de paquets... Fet
joan@joan-desktop:~$ sudo apt-get install-f
E: Operació no vàlida install-f
joan@joan-desktop:~$ sudo apt-get install -f
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 1 no actualitzats.
joan@joan-desktop:~$ sudo aptitude install gimp
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents contenen errors.
  gimp gimp-data 
Els paquets nous següents s'instal·laran automàticament:<
  gimp-gnomevfs 
Els paquets següents s'han apartat:
  gimp-python 
Els paquets nous següents s'instal·laran:
  gimp-gnomevfs 
0 paquets actualitzats, 2 instal·lats, 0 a suprimir i 1 a no actualitzar.
Es necessita obtenir 3899kB d'arxius. Després del desempaquetat s'utilitzaran 10,8MB.
No s'han trobat les dependències del paquets següents:
  gimp: Depén: gimp-data (< 2.4.0~rc3-z) però el 2.4.2-1~getdeb1 està instal·lat.
  gimp-data: Entra en conflicte: gimp (< 2.4.0) però el 2.4.0~rc3-1ubuntu7 està per instal·lar.
Resolving dependencies...
Les accions següents resoldran les dependències:

Desactualitza els següents paquets:
gimp-data [2.4.2-1~getdeb1 (now) -> 2.4.0~rc3-1ubuntu7 (gutsy)]

La puntuació és 80

Accepteu la solució? [Y/n/q/?] y
Els paquets nous següents s'instal·laran automàticament:<
  gimp-gnomevfs 
Els paquets següents es desactualitzaran:
  gimp-data 
Els paquets següents s'han apartat:
  gimp-python 
Els paquets nous següents s'instal·laran:
  gimp gimp-gnomevfs 
0 paquets actualitzats, 2 instal·lats, 1 desactualitzats, 0 a suprimir i 1 a no actualitzar.
Es necessita obtenir 5803kB d'arxius. Després del desempaquetat s'utilitzaran 9757kB.
Esteu segur de voler continuar? [Y/n/?] y
S'està escrivint la informació d'estat estesa... Fet
Obté:1 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/main gimp-data 2.4.0~rc3-1ubuntu7 [1904kB]
Obté:2 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/main gimp 2.4.0~rc3-1ubuntu7 [3892kB] 
Obté:3 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/main gimp-gnomevfs 2.4.0~rc3-1ubuntu7 [7318B]
S'han recollit 5803kB en 18s (311kB/s)                                          
dpkg - avís: s'està desactualitzant gimp-data de 2.4.2-1~getdeb1 a 2.4.0~rc3-1ubuntu7.
(S'està llegint la base de dades ... hi ha 126808 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar gimp-data 2.4.2-1~getdeb1 (fent servir .../gimp-data_2.4.0~rc3-1ubuntu7_all.deb) ...
S'està desempaquetant el reemplaçament de gimp-data ...
S'està seleccionant el paquet gimp prèviament no seleccionat.
S'està desempaquetant gimp (de .../gimp_2.4.0~rc3-1ubuntu7_i386.deb) ...
S'està seleccionant el paquet gimp-gnomevfs prèviament no seleccionat.
S'està desempaquetant gimp-gnomevfs (de .../gimp-gnomevfs_2.4.0~rc3-1ubuntu7_i386.deb) ...
S'està configurant gimp-data (2.4.0~rc3-1ubuntu7) ...
S'està instal·lant una versió nova del fitxer de configuració /etc/gimp/2.0/gimprc ...
The generated cache was invalid.

S'està configurant gimp (2.4.0~rc3-1ubuntu7) ...

S'està configurant gimp-gnomevfs (2.4.0~rc3-1ubuntu7) ...
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
joan@joan-desktop:~$

---


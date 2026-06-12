---
title: "Paquets Trencats"
date: 2008-04-23
forum: Catalan Team
---

### Post by LitusMayol on 2008-04-23
Bones familia!

Primer de tot. Desconeixia que a Ubuntu Forums es poguéssin resoldres dubtes en català... sóc un autèntic *"newbie"*hehe.

El problema. Vaig començar amb KDE. Em vaig passar a GNOME. Avui he decidit que com que tenia el KDE fet caldo el "*purgue*va". Després de netejar-lo he provat de tornar-lo a instal·lar i...

> litus@mayolets:~$ sudo apt-get install kdm
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
  kdm: Depén: kdebase-bin (= 4:3.5.8-0ubuntu2.2) però s'instal·larà 4:3.5.8-2ubuntu3~gutsy1~ppa1
E: Paquets trencats


Algú se li acut què pot ser!? O com solucionar-ho? I de pas algú em pot explicar perquè passa? (és que si algú em dona la solució *cullonut*, però també voldria entendre que ha passat per anar-ne sabent més poc a poc).


Merci!

---

### Post by papapep on 2008-04-23
> Primer de tot. Desconeixia que a Ubuntu Forums es poguéssin resoldres dubtes en català... sóc un autèntic "newbie"hehe.

Si senyor. Estem al fòrum, tenim dues llistes de correu i un canal d'irc :-) Per a més referències: [www.ubuntu.cat](www.ubuntu.cat) o [https://wiki.ubuntu.com/CatalanTeam](https://wiki.ubuntu.com/CatalanTeam).

Respecte el teu petament de paquets, doncs poc podem saber del perquè has arribat on ets si tu no ens ho dius :-D

> Avui he decidit que com que tenia el KDE fet caldo el "purgueva". Després de netejar-lo he provat de tornar-lo a instal·lar i...


El que és clar, és que alguna barrabassada li has fet a la base de dades de paquets "purgeant" i fent coses d'aquestes i que ara te l'està cobrant "en espècies".

Quins repositoris tens al sources.list?

---

### Post by LitusMayol on 2008-04-23
Perfecte!
Ara m'apunto a les llistes!

> El que és clar, és que alguna barrabassada li has fet a la base de dades de paquets "purgeant" i fent coses d'aquestes i que ara te l'està cobrant "en espècies".

Mmmm... :)El motiu pel que vaig fer un "aptitude install ubuntu-desktop" va ser que vaig probar d'instal·lar Fusion. XD Ho sé, ho sé... És una guarrada. Però a sobre ho devia fer malament perquè des d'aleshores que el KDE em funcionava lent lent (em va recordar l'etapa fosca de quan m'havien rentat el cervell i anava amb el SO privatiu aquell... el que... ostres no em surt el nom, segur que saps de quin parlo! ;) ). Aleshores vaig instal·lar-me el Ubuntu. Poc a poc m'hi he avesat i m'agrada molt. Però pel que veig tenia el KDE més petat del que em pensava.

> Quins repositoris tens al sources.list?

Doncs... la veritat és que no recordo on és (sé que l'he hagut de modificar un parell de vegades)... Si m'ho dius et facilito la informació!


Merci! ;)

---

### Post by papapep on 2008-04-23
A un terminal 

```
sudo nano /etc/apt/sources.list
``` 
:-)

---

### Post by LitusMayol on 2008-04-23
*Tomá peásso'h de li'hta*:
> 
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse



#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

Merci! ;)

---

### Post by papapep on 2008-04-23
:shock: Punyetes....quin munt de coses que hi tens...

1.- Comenta (fica un "quadradillu" al davant) la línia del CDROM:

> deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

2.- El servidor de repositoris d'Andorra (suposo que ad deu ser Andorra, no?) no sé què tal funciona. En tot cas, deixa'l i ja ho veurem.

3.- Estàs amb Feisty o amb Gutsy?? Tens entrades de les dues versions...

4.- Si vols evitar problemes com els que ara tens: automàtix a la brossa directament. Tot això que ve ara, esborrat:

> #AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

Un cop fet això:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

Ara torna a provar a instal·lar el paquet que no et deixava, a veure què diu.

---

### Post by LitusMayol on 2008-04-23
1. Gutsy
2. :(
> litus@mayolets:~$ sudo apt-get install kdm
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
  kdm: Depén: kdebase-bin (= 4:3.5.8-0ubuntu2.2) però s'instal·larà 4:3.5.8-2ubuntu3~gutsy1~ppa1
E: Paquets trencats

Jo vull fer això:
> sudo apt-get install kdm
sudo apt-get install kubuntu-desktop
sudo apt-get install kde 
sudo dpkg-reconfigure kdm

Merci de nou! ;)

---

### Post by papapep on 2008-04-23
Bé. Carrega't totes les línies que siguin de Feisty.
Després, torna a enganxar el sources.list que et quedi.

---

### Post by LitusMayol on 2008-04-23
Mmmm... em comença a preocupar perquè re del que faig canvia la situació.

El *kit* deu està aquí:

> Els següents paquets tenen dependències sense satisfer:
  kdm: Depén: kdebase-bin (= 4:3.5.8-0ubuntu2.2) però s'instal·larà 4:3.5.8-2ubuntu3~gutsy1~ppa1





Per cert... et pots passar per: [http://ubuntuforums.org/showthread.php?p=4771722#post4771722](http://ubuntuforums.org/showthread.php?p=4771722#post4771722)
 

Merci! ;) :D:lolflag:

---

### Post by papapep on 2008-04-23
> El kit deu està aquí:

Quote:
Els següents paquets tenen dependències sense satisfer:
kdm: Depén: kdebase-bin (= 4:3.5.8-0ubuntu2.2) però s'instal·larà 4:3.5.8-2ubuntu3~gutsy1~ppa1


Evidentment el "quid" és això, ja que això indica que tens un problema amb la base de dades de paquets, causat pel poti-poti de repositoris que has estat fent servir, que és el que intentem arreglar.

Quan fas els "aptitude update" i "aptitude safe-upgrade" no tens cap missatge sospitós??? Tot va perfecte?

---

### Post by LitusMayol on 2008-04-24
Bones!

A veure... jo no hi veig re estrany, però tampoc sé que és lo normal (vull dir que quan ho faig miro que la última línia no sigui un error i prou). No ho sé, mira:
```

litus@mayolets:~$ sudo apt-get update
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-ca
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-ca
Des:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-ca              
Des:2 http://ad.archive.ubuntu.com gutsy Release.gpg [191B]                    
Des:3 http://ad.archive.ubuntu.com gutsy/main Translation-ca [6978B]     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-ca  
Ign http://security.ubuntu.com gutsy-security/universe Translation-ca   
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-ca 
Obj http://security.ubuntu.com gutsy-security Release                   
Ign http://ad.archive.ubuntu.com gutsy/restricted Translation-ca        
Des:4 http://ad.archive.ubuntu.com gutsy/universe Translation-ca [1981B]
Ign http://ad.archive.ubuntu.com gutsy/multiverse Translation-ca         
Obj http://security.ubuntu.com gutsy-security/main Packages              
Des:5 http://ad.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://ad.archive.ubuntu.com gutsy-updates/main Translation-ca             
Ign http://ad.archive.ubuntu.com gutsy-updates/restricted Translation-ca       
Ign http://ad.archive.ubuntu.com gutsy-updates/universe Translation-ca         
Ign http://ad.archive.ubuntu.com gutsy-updates/multiverse Translation-ca       
Obj http://security.ubuntu.com gutsy-security/restricted Packages              
Obj http://security.ubuntu.com gutsy-security/main Sources               
Obj http://security.ubuntu.com gutsy-security/restricted Sources         
Obj http://ad.archive.ubuntu.com gutsy Release                           
Obj http://security.ubuntu.com gutsy-security/universe Packages                
Obj http://security.ubuntu.com gutsy-security/universe Sources           
Obj http://security.ubuntu.com gutsy-security/multiverse Packages        
Obj http://security.ubuntu.com gutsy-security/multiverse Sources         
Obj http://ad.archive.ubuntu.com gutsy-updates Release                   
Obj http://ad.archive.ubuntu.com gutsy/main Packages       
Obj http://ad.archive.ubuntu.com gutsy/restricted Packages
Obj http://ad.archive.ubuntu.com gutsy/main Sources
Obj http://ad.archive.ubuntu.com gutsy/restricted Sources
Obj http://ad.archive.ubuntu.com gutsy/universe Packages
Obj http://ad.archive.ubuntu.com gutsy/universe Sources
Obj http://ad.archive.ubuntu.com gutsy/multiverse Packages
Obj http://ad.archive.ubuntu.com gutsy/multiverse Sources
Obj http://ad.archive.ubuntu.com gutsy-updates/main Packages
Obj http://ad.archive.ubuntu.com gutsy-updates/restricted Packages
Obj http://ad.archive.ubuntu.com gutsy-updates/main Sources
Obj http://ad.archive.ubuntu.com gutsy-updates/restricted Sources
Obj http://ad.archive.ubuntu.com gutsy-updates/universe Packages
Obj http://ad.archive.ubuntu.com gutsy-updates/universe Sources
Obj http://ad.archive.ubuntu.com gutsy-updates/multiverse Packages
Obj http://ad.archive.ubuntu.com gutsy-updates/multiverse Sources
8962B descarregats en 1s (6600B/s)    
S'està llegint la llista de paquets... Fet
litus@mayolets:~$ sudo aptitude safe-upgrade
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
No s'instal·larà, actualitzarà o suprimirà cap paquet.
0 paquets actualitzats, 0 instal·lats, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
litus@mayolets:~$ 

```

Merci de nou!

---

### Post by papapep on 2008-04-24
Si us plau, fes:

```
sudo **[COLOR="Red"]aptitude[/COLOR]** update
sudo **[COLOR="Red"]aptitude[/COLOR]** safe-upgrade
```

i enganxa els missatges.

---

### Post by LitusMayol on 2008-04-24
Així?

**sudo aptitude update**
> litus@mayolets:~$ sudo aptitude update
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-ca
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-ca
Obté:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-ca               
Obté:2 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main Translation-ca              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-ca  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-ca    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-ca  
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                   
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/restricted Translation-ca         
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/universe Translation-ca
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/multiverse Translation-ca
Obté:3 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates Release.gpg [191B]     
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main Translation-ca       
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/restricted Translation-ca 
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/universe Translation-ca   
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages             
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/multiverse Translation-ca
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy Release
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources              
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources        
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates Release                  
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources          
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages       
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources        
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main Packages                    
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/restricted Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/restricted Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/universe Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/universe Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/multiverse Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/multiverse Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/restricted Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/restricted Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/universe Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/universe Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/multiverse Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/multiverse Sources
S'han recollit 3B en 1s (2B/s)        
S'està llegint la llista de paquets... Fet 



**sudo aptitude safe-upgrade**
> litus@mayolets:~$ sudo aptitude safe-upgrade
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
No s'instal·larà, actualitzarà o suprimirà cap paquet.
0 paquets actualitzats, 0 instal·lats, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
litus@mayolets:~$ 


És això el que m'has dit? O no...? :S
Merci

---

### Post by papapep on 2008-04-24
mmmm.....doncs en teoria la base de paquets està bé....:confused:

I si ara fas el:

```
sudo [COLOR="Red"]**aptitude**[/COLOR] install kdm
```

què et diu?

---

### Post by LitusMayol on 2008-04-24
Doncs a veure, ha funcionat!
Mira et penjo el què. Ara està en "*ello*". Com pot ser que amb "aptitude install" funcioni i amb "apt-get" no?

El CODI:
```
litus@mayolets:~$ sudo aptitude install kdm
[sudo] password for litus:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents contenen errors.
  kdm 
0 paquets actualitzats, 1 instal·lats, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 664kB d'arxius. Després del desempaquetat s'utilitzaran 1606kB.
No s'han trobat les dependències del paquets següents:
  kdm: Depén: kdebase-bin (= 4:3.5.8-0ubuntu2.2) però el 4:3.5.8-2ubuntu3~gutsy1~ppa1 està instal·lat.
Resolving dependencies...
Les accions següents resoldran les dependències:

Instal·la els següents paquets:
libarts1-mpeglib [4:3.5.8-0ubuntu1 (gutsy)]
mpeglib [4:3.5.8-0ubuntu1 (gutsy)]

Desactualitza els següents paquets:
kcontrol [4:3.5.8-2ubuntu3~gutsy1~ppa1 (now) -> 4:3.5.8-0ubuntu2.2
(gutsy-updates)]
kdebase-bin [4:3.5.8-2ubuntu3~gutsy1~ppa1 (now) -> 4:3.5.8-0ubuntu2.2
(gutsy-updates)]
kdebase-kio-plugins [4:3.5.8-2ubuntu3~gutsy1~ppa1 (now) -> 4:3.5.8-0ubuntu2.2
(gutsy-updates)]
kdesktop [4:3.5.8-2ubuntu3~gutsy1~ppa1 (now) -> 4:3.5.8-0ubuntu2.2
(gutsy-updates)]
kfind [4:3.5.8-2ubuntu3~gutsy1~ppa1 (now) -> 4:3.5.8-0ubuntu2.2 (gutsy-updates)]
konqueror [4:3.5.8-2ubuntu3~gutsy1~ppa1 (now) -> 4:3.5.8-0ubuntu2.2
(gutsy-updates)]

La puntuació és 212

Accepteu la solució? [Y/n/q/?] Y
Els paquets següents no s'utilitzen i se suprimiran:
  cryptsetup 
Els paquets nous següents s'instal·laran automàticament:<
  libarts1-mpeglib mpeglib 
Els paquets següents es desactualitzaran:
  kcontrol kdebase-bin kdebase-kio-plugins kdesktop kfind konqueror 
Els paquets nous següents s'instal·laran:
  kdm libarts1-mpeglib mpeglib 
0 paquets actualitzats, 3 instal·lats, 6 desactualitzats, 1 a suprimir i 0 a no actualitzar.
Es necessita obtenir 9728kB d'arxius. Després del desempaquetat s'utilitzaran 3105kB.
Esteu segur de voler continuar? [Y/n/?] Y
```

Que vol dir que es desactualitzaran 6 paquets!?

Merci Josep!

---

### Post by papapep on 2008-04-24
> Com pot ser que amb "aptitude install" funcioni i amb "apt-get" no?

Doncs per que tot i que tots dos són dues excel·lents eines, l'aptitude és més modern i gestiona millor les dependències. Tot i això hi ha cops que s'arreglen coses amb l'apt-get que amb l'aptitude no es pot, o sigui que no pensis que un és superior a l'altre. 
El millor és que tenim un sistema de gestió de paquets (dpkg/apt-get/aptitude) absolutament genial ;-)

---


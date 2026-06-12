---
title: "Senyal d'error..."
date: 2008-05-03
forum: Catalan Team
---

### Post by lo gambusí on 2008-05-03
[IMG]http://img175.imageshack.us/img175/5237/capturazc2.png[/IMG]:confused::confused::confused::confused::confused::confused:

M'ha sortit així de repent...

---

### Post by CarlesOriol on 2008-05-03
Tens unes " davant del text deb en una linia del del sources.list (o en algun arxiu de paquets a la carpeta /etc/apt/sources.list.d )

---

### Post by lo gambusí on 2008-05-03
Això vol dir que he d'editar-ho i treure-hi les comes?

---

### Post by MorlanXaos on 2008-05-03
Gambusí, jo soc molt nou i no et puc ajudar massa. Però el que diu l'Oriol sembla raonable.

Estava mirant el teu escriptori i es molt bonic. La barra que tens a sota, amb els icones, quina es?

---

### Post by lo gambusí on 2008-05-03
MorlanXaos, la barra és d'un programa anomenat Awn-manager ;)

He tret les cometes, i m'ha passat [això]("http://img518.imageshack.us/img518/6999/capturakt1.png"). Li he donat a tanca i m'ha dit [això]("http://img512.imageshack.us/img512/3422/captura1yd1.png").

---

### Post by CarlesOriol on 2008-05-03
A veure la 1a és normal si no incorpores les signatures digitals de repositoris de tercers. Però l'expert en automàtix és en papapep.

La segona seria més fàcil de veure que tens al sources.list i dir-te que cal que eliminis.

Per cert. per posar aquests missatges aniria molt millos que ho fecis de linia (sudo apt-get update) de comanda i enganxessis el text, és molt més senzill per tots que aquestes imatges.

---

### Post by lo gambusí on 2008-05-03
> oriol@oriol-laptop:~$ sudo apt-get update
[sudo] password for oriol: 
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-ca
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-ca
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy Release.gpg                                    
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/main Translation-ca                      
Des:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-ca                 
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/restricted Translation-ca                
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/universe Translation-ca                  
Ign [http://ftp.oleane.net](http://ftp.oleane.net) hardy/multiverse Translation-ca                
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates Release.gpg                      
Ign [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/main Translation-ca              
Ign [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/restricted Translation-ca        
Ign [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/universe Translation-ca
Ign [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/multiverse Translation-ca
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy Release
Des:2 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [6733B]                         
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                             
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates Release             
Obj [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/main Packages                            
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/restricted Packages
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/restricted Sources
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/main Sources
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/multiverse Sources
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/universe Sources
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/universe Packages
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy/multiverse Packages
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/main Packages
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/restricted Packages
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/universe Packages
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/multiverse Packages
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/main Sources
Obj [http://ftp.oleane.net](http://ftp.oleane.net) hardy-updates/restricted Sources
190B descarregats en 4s (45B/s)       
S'està llegint la llista de paquets... Fet
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY CC919A31E23C5FC3
W: Potser voldreu executar apt-get update per a corregir aquests problemes
oriol@oriol-laptop:~$ 

Això és lo que he passat a text.

---

### Post by lo gambusí on 2008-05-03
I això el sources.list
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb [http://ftp.oleane.net/ubuntu/](http://ftp.oleane.net/ubuntu/) hardy main restricted
deb-src [http://ftp.oleane.net/ubuntu/](http://ftp.oleane.net/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.oleane.net/ubuntu/](http://ftp.oleane.net/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [http://ftp.oleane.net/ubuntu/](http://ftp.oleane.net/ubuntu/) hardy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.oleane.net/ubuntu/](http://ftp.oleane.net/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.oleane.net/ubuntu/](http://ftp.oleane.net/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
# deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main
# deb [http://www.bashterritory.com/pytube/releases](http://www.bashterritory.com/pytube/releases) /
# deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/
#AWN
# deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator


deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by RainCT on 2008-05-03
Esborra tot aquest liu que hi tens i posa-hi només això:

```

deb http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/ hardy universe restricted main multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

```

(Si no t'interessa poder fer servir la comanda «apt-get source», amb les tres primeres línies ja n'hi ha prou.)

---

### Post by lo gambusí on 2008-05-03
Ho borro TOT? O a partir de certa línia?:?

---

### Post by guillemsola on 2008-05-03
No em voldria precipitar però crec que el sources que et proposa RainCT es corresponen amb la versió Hardy i tu tens la Gutsy, de manera que no hauries de fer-ho. 

Segon, sempre que canvis dades d'un fitxer de configuració fes una copia de seguretat de l'arxiu.

---

### Post by RainCT on 2008-05-03
lo gambusí: Sí, tot. Totes les línies que començen per "#" no fan absolutament res, així que es pots esborrar, i les que et dic jo es corresponen a la resta (però escrit de forma més compacta) més el repositori hardy-security, que et falta i que és el que té les actualitzacions de seguretat.

angrychai: No, té la Hardy. Si t'hi fixes les línies de la Gutsy estan totes comentades, i les descomentades que hi ha més amunt són de la Hardy.

---

### Post by CarlesOriol on 2008-05-03
L'avis que no has incorporat la clau del repositori de l'automatix és correcte ja que no pot validar-ne l'origen.

Jo personalment eliminaria aquesta font ja que a més és per a gutsy i ha desaparagut com a projecte.

I no estic d'acord amb l'angrychai veig que els repositoris insta&#320;lats son els de la hardy.

A mes comprova que no tinguis més fonts de tercers a la carpeta /etc/apt/sources.list.d i si hi son et recomano que els eliminis.

---

### Post by lo gambusí on 2008-05-03
moltes gràcies a tots, ja he pogut actualitzar amb tranquil·litat.

carlesoriol: faig alguna cosa, o ho deixo així?

salut!!

---

### Post by CarlesOriol on 2008-05-04
posa un # al començament de la linia 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main 
i ja està.

---

### Post by lo gambusí on 2008-05-05
ok, fet.

moltes gràcies!!

---


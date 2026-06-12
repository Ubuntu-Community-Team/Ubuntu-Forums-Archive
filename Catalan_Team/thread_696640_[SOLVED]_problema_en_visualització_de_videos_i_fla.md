---
title: "[SOLVED] problema en visualització de videos i flash"
date: 2008-02-14
forum: Catalan Team
---

### Post by rogespierre on 2008-02-14
Bones, primer de tot sóc nou nou, porto un parell de setmanes amb l'ubuntu, tot i això em va prou bé i vaig aprenent-ne.

el problema es que no puc visualitzar moltes aplicacions en flash i videos. El youtube si q el puc veure, tot i q no massa b i les icones de control del video s'aglomeren.

les altres webs q allotgen videos no en puc veure cap. i aplicacions en flash tampoc, per exemple les últimes q e visitat qelcom.com o , per qi jugui al hattrick, el visualitzador de partits en flash.

he mirat altres posts com dieu al missatge de benvinguda pero diria q el que comenteu ho tinc instal·lat. com que encara no en sé gaire us llistaré les aplicacions que em diu el sistema q tinc instalades i q dugin la paraula flash:

a Afegeix-Elimina em diu a **Aplicacions instalade**s:
macromedia flash plugin
ubuntu restricted areas
gstreamer ffmpeg video plugin
gnash swf viewer

i al **synaptic** si busco flash em surten amb quadradet verd (q suposo q vol dir instalats):

flashplugin-nonfree
gnash
gnash-common
gnash-sygnal
gnash-tools
kubuntu restricted extras
libswfdec0.5-1
mozilla-plugin-gnash
ubuntu restricted extras
xubuntu restricted extras

a veure si em podeu ajudar, i gràcies per endavant!

---

### Post by papapep on 2008-02-14
Benvingut Rogespierre!!! (ja trigues a explicar-nos la teva vida al fil de benvinguda ;) ),

Respecte el teu problema, jo l'orientaria treient tot el que tens ara de flash instal·lat i instal·lant l'afegit propietari de Macromedia de bell nou:

Per a desinstal·lar tot el que tens ara, fes a un terminal:

```
sudo aptitude purge flashplugin-nonfree gnash gnash-common gnash-sygnal gnash-tools mozilla-plugin-gnash
```

Per a fer el segon pas, fes el que s'indica en aquest altre fil: [http://ubuntuforums.org/showthread.php?t=687423&highlight=flash](http://ubuntuforums.org/showthread.php?t=687423&highlight=flash)

Ja ens explicaràs com va tot plegat.

Ui!! Per cert, estaria bé saber si tens instal·lada la versió de 32 o de 64 bits d'Ubuntu (la de 64 dóna bastant de mals de cap amb el flash...)

---

### Post by rogespierre on 2008-02-14
mmm.... ei, però si ho borro tot ajudeu-me fins al final e?!

que he de anar a 
[http://www.howtoforge.com/native_lin...yer9_in_ubuntu](http://www.howtoforge.com/native_lin...yer9_in_ubuntu)
i baixar-me un plugin?

no ho faig des de cap gestor de paquets?

PD quan ho solucioni, us explico la vida al fil de benvinguda ;)

---

### Post by papapep on 2008-02-14
No, has de baixar el paquet tar.gz del lloc web d'Adobe: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

> no ho faig des de cap gestor de paquets?

No, el que busquem no hi és.

> PD quan ho solucioni, us explico la vida al fil de benvinguda 

Óndia!! Això no és xantatge??? :-D

---

### Post by rogespierre on 2008-02-14
no omeee, era un pronòstic ;)

b, ja tinc el paquet a lescriptori baixat, elimino tot el q em dius... i executo el paquet i au?

---

### Post by jaume69 on 2008-02-14
prova de desinstal.lar el** gnash** viam si amb el flash-nonfree et funciona.

Si tampoc funciona,decarrega'l de la [[COLOR="Red"]web[/COLOR]]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&Lang=Spanish").

Només clikan sobre flash-installer,et sortirà si vols obrir amb el terminal i segueixes les instruccions i ja està.

---

### Post by papapep on 2008-02-14
:-D, més o menys.

Executes la ordre per a desinstal·lar tota la morralla aquella que tens.

Després, descomprimexes el tar.gz on més gràcia et faci (millor a la teva carpeta personal, pels permisos) i l'executes. A partir d'aquí ja només li has d'anar dient el que demana que és ben poc.

---

### Post by rogespierre on 2008-02-14
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


mmm, no se ben bé q vol dir això, s'ha desinstalat la morralla o no?

---

### Post by papapep on 2008-02-14
No :-) vol dir que deus tenir el synaptic (o algun altre gestor de paquets) obert a alguna altra finestra i no pot accedir la ordre (per seguretat) a la base de paquets.

---

### Post by rogespierre on 2008-02-14
mmmm no nem b...

tenies rao, tenia un gestor de paquets obert

le tancat, e descomprimit linstalador, li e dit q ok a tot i sa instalat

tot i aixo.. no veig les coses, pero abans sem carregaven malament o em deien un missatge derror.. ara en canvi es qeda gris... i no veig ni el youtube:confused:

---

### Post by papapep on 2008-02-14
Corres massa home.

A veure, quin camí li has dit per trobar el navegador?? Si fas servir el firefox li has de dir:

```
/usr/lib/firefox
```

No m'has fet cas i no has mirat l'altre fil ;-)

Torna a executar l'instal·lador i digues-li això ara.

---

### Post by guillemsola on 2008-02-14
Hola

El paquet [COLOR="Red"]flashplugin-nonfree[/COLOR] també és pot instal·lar des de apt-get o desde synaptic. De fet són la mateixa versió que el que et baixes d'adobe.

A la carpeta [COLOR="Red"]/home/usuari/.mozilla/firefox/plugins[/COLOR] hi ha un arxiu [COLOR="Red"]pluginreg.dat[/COLOR] que tinc entès que si el borres (o millor li canvies el nom) forces al firefox a tornar a reconfigurar els plugins.

Si tens dubtes de quins plugins fa servir el teu firefox escrius aquesta direcció web 

> about: plugins

Aleshores et llista els plugins que ha trobat el firefox. Hi has de tenir

> 
Shockwave Flash

    Nom del fitxer: libflashplayer.so
    Shockwave Flash 9.0 r115

Salut!

---

### Post by papapep on 2008-02-14
Angrychai: la teoria és la que tu dius, però sé de bastanta gent que instal·lant dels repositoris no li ha funcionat (no em facis dir el perquè), i baixant el paquet tar.gz si.  Per això ho estem fent així.

---

### Post by guillemsola on 2008-02-14
Doncs no ho sabia, Bé potser actualment ja ho tenen millor resolt.

Jo l'he instal·lat a una 7.10 i el que fa és baixar el tar.gz de manera "diferent" a com ho fa apt-get habitualment i després executa l'script d'instal·lació tal com ho faria un usuari. La versió de l'arxiu és la mateixa.

És que tot el que entra per repositoris és un "gustazo". Amb la d'hores que havia perdut jo buscant cracks i mendangues i ara ja no poso ni cd's a l'ordinador. I s'actualitza solet!

Salut!

---

### Post by rogespierre on 2008-02-15
solucinat!

..no sé ben bé com, ja que aixo de canviar la ruta no se com fer-ho ja que el terminal arranca i nomes li dic q ok i va fent sola, la qüestió es q reinstalant-ho ja si em funciona tot!!!

moltes gràcies! i en especial al papapepet (ara escriuré al fil de presentació)

---

### Post by papapep on 2008-02-15
Me n'alegro que et funcioni. Ara et toca donar el fil per resolt ;)

---

### Post by CarlesOriol on 2008-02-15
Manu Calavera... Al grim fandango no escriuen com si enviessin missatges per sms... aquí tampoc ho fem.

---


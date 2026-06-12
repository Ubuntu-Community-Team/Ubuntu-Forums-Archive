---
title: "[SOLVED] apache2, PostgreSQL i PHP"
date: 2008-11-07
forum: Catalan Team
---

### Post by janiga on 2008-11-07
Bon dia a tothom.:)
Per començar, dir que sóc nou en el mon linux i vaig una mica perdut.
Porto una setmana intentant aprendre les bases de Linux i tractant d'instal-lar l'apache2, el PostgreSQL 8.3.5 i el PHP 5.2.6. Després de molt patir he triumfat en el PostgreSQL i  en el PHP. Pel que fa a l'apache2 estic tenint problemes... (he buscat durant hores en el Google i si que hi ha casos semblants però no idèntics i no em donen una resposta):confused:

És normal que tingui l'apache2 ubicat a /usr/local/apache2 (ubicació 1)i a la vegada a /etc/apache2 (ubicació 2)?:confused:

per executar-lo en la ubicació 1: #ubicació 1/apachectl start
per executar-lo en la ubicació 2: #ubicació 2/apache2 start
Per què aquesta diferència a l'hora d'execurtar-ho?
(serà que el tinc instal·lat a dos llocs paral·lel·lament?:confused:

L'arxiu de configuració: httpd.conf es troba a 2 llocs
en la ubicació 1/conf/httpd.conf (que conté dades)
i la ubicació 2/httpd.conf que està buit. 
Altre misteri...:confused:

Per altra banda, he creat una aplicació de mostra PHP: 'hola mon' i la he desada en ubicació 1/htdocs/proba.php
on NO funciona.

Ara bé, he fet una copia d'aquest arxiu a : /var/www/proba.php i si que funciona, és a dir, des del navegador: [http://localserver/proba.php](http://localserver/proba.php) i veig el missarge 'Hola mon'.

No sé si algú pot donar una mica de llum a aquest cas, que em porta de cap.:confused:
Perdó per l'explicació tan llarga i salut a tots.

---

### Post by papapep on 2008-11-07
Benvingut Janiga,

Et convido a passar-te, si no ho has fet ja, pels fils de capçalera per aprendre una mica com intentem funcionar i explicar-nos una mica més de tu :-)

Respecte el que planteges, doncs és que cal una mica d'explicació prèvia:

Els [dimonis]("http://ca.wikipedia.org/wiki/Dimoni_(programa)") (daemons) servidors de Linux (com apache, postgresql, sendmail, samba, etc...) normalment desen els fitxers de configuració sota /etc, que és el seu lloc predeterminat.
En canvi els executables solen ser sota /usr (/usr/bin, /usr/sbin, /usr/local, etc...en funció de diferents coses).

Per arrencar-los, cal anar a /etc/init.d/, i aqui veuràs tots els dimonis que tens disponibles per arrencar o aturar.

Normalment, apache (en aquest cas apache2), s'arrenca amb un (amb drets d'administració):

```
/etc/init.d/apache2 start
```

El fitxer principal de configuració d'apache2 ja no és httpd.conf, és un fitxer que s'hi arriba per dues vies diferents (no em preguntes el perquè...):

a /etc/apache2/sites-available/default

i a /etc/apache2/sites-enabled/000-default

aquest últim (000-default) és un enllaç simbòlic al primer (default), o sigui que realment en editar-los edites el mateix.

I el que et passa respecte la prova en php que no et funciona fora de /var/www està íntimament relacionat amb el contingut dels fitxers que t'acabo d'esmentar. Si el visualitzes, veuràs que et mostra una cosa semblant a això:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                RedirectMatch ^/$ /apache2-default/
        </Directory>

```

A banda d'altres coses, clar. Aquí està dient que el directori arrel per a servir pàgines web és /var/www, ja que és un problema de seguretat servir pàgines web de qualsevol directori sense més. Estaries obrint una porta a possibles atacs a qualsevol part del teu sistema.

Espero haver-me sapigut explicar.

---

### Post by indiosincracia on 2008-11-07
Benvingut janiga;

si vols instal·lar un servidor el que necessites es coneix com sistema "LAMP"; Linux, Apache, MySQL i PHP (pero corre amb MySQL no en PostgreSQL)
tenint en compte la versió ubutu que tens

$lsb_release -a

trobaràs molta informació al gugle sobre els passos a seguir, com son una mica llargs, si tens algun entrebanc deixa'l per aquí.
Salut

---

### Post by papapep on 2008-11-07
> si vols instal·lar un servidor el que necessites es coneix com sistema "LAMP"

Això NO té per que ser així Lluís ;-)

Aquesta és una manera relativament accessible que s'ha creat per a iniciar-se, però tal i com ho fa en Janiga amb postgresql en vers de Mysql és perfectament factible, jo fa anys que hi treballo i, a més, molt més robust i professional (que el mysql, vull dir...).

I qui diu postgresql, pot dir qualsevol altre [RDBMS]("http://en.wikipedia.org/wiki/RDBMS") que estigui disponible per a Gnu/Linux, clar...:-)

Ah! m'oblidava, i tampoc l'apache és obligatori, hi ha una autèntica munió de servidors http disponibles als repositoris...

---

### Post by janiga on 2008-11-08
Gràcies companys per respondre tan de pressa.

En primer lloc disculpar-me per no haver-me presentat, ho faré ara després d'escriure aquest thread. Estava ofuscat i necessitava obtindre respostes :)

He de fer una aplicació que manegui grans bases de dades i després de llegir les característiques de MySQL i PostgreSQL vaig optar per aquest segon. La veritat es que tinc experiència 0 en qualsevol dels dos.

Pel que m'expliques Papapep arribo a varies conclusions que em porten a més preguntes :o

Quan vaig instal·lar el PHP vaig seguir una sèrie de passos que vaig trobar en un forum. Una de les darreres instruccions em deia d'accedir al fitxer httdp.conf i afegir una linia: Addtype PHP... (no m'enrecordo, que ho tinc a la feina) però bàsicament es tractava de fer-li saber a l'apache2 que a partir d'ara hauria d'entendre un format d'arxiu nou amb extensió php (suposo). Si l'arxiu de configuració el tenim a /etc/apache2/sites-available/default, suposo que el que vaig afegir no va servir de res...
Per què serveix l'arxiu httpd.conf? o apache2.conf? o ports.conf? buffff
tan se val, són tants els dubtes que tinc que ja m'espavilaré.

i ara, des del PC de casa on tinc el mateix ubuntu que a la feina, sense descarregar-me res he fet: sudo apt-get install apache2
i me l'instal·la...? sense configurar-lo ni compilar-lo?

ja m'he comprat un llibre de Linux (que no 'pillo' ni un cromo')

Salutacions

---

### Post by lpargemi on 2008-11-08
> **janiga said:**
> 
Per què serveix l'arxiu httpd.conf? o apache2.conf? o ports.conf? buffff
tan se val, són tants els dubtes que tinc que ja m'espavilaré.

i ara, des del PC de casa on tinc el mateix ubuntu que a la feina, sense descarregar-me res he fet: sudo apt-get install apache2
i me l'instal·la...? sense configurar-lo ni compilar-lo?


Hola 

El fitxer apache2.conf és el de la configuració, però per no fer-ho tan pesat (suposo) té un include al httpd.conf, així que el què hi ha al segon fitxer també és configuració. I també el què hi ha a ports.conf i al directori conf.d

Pel què fa al segon comentari, doncs si, si tot va bé és així de fàcil. (Que bé, no?)

Una altra cosa, que jo faig servir, tot i que no sé què tal queda pel tema de seguretat: Jo em faig les pàgines dins del meu usuari, en un directori, i a www hi poso un enllaç. Així tinc menys problemes de drets d'accés mentre ho preparo. Quan ho tinc llest ho baixo al servidor, i ja està. Per fer-ho, et poses a var/www i amb drets d'administrador fas
```
ln -s /home/usuari/NomDirectori NomEnllaç
```
Així entrant al navegador [http://localhost/NomEnllaç](http://localhost/NomEnllaç) veuràs la pàgina  que tens penjada al directori.

De qualsevol manera, insisteixo en què no sé com queda això pel tema de seguretat.

Lluís

---

### Post by RainCT on 2008-11-09
Em sembla que les instruccions que has seguit no estaven gaire bé... No hauries de tenir res de l'Apache a /usr/local, ja que no et cal (ni et recomano) que compilis res per tu mateix, i en principi tampoc et cal tocar cap fitxer de configuració per tal que funcioni (tot i que això sí que ho pots fer després si vols canviar alguna cosa).

En principi la següent comanda (i alguna cosa més que segur que m'oblido) t'ho haurien de deixar tot a punt:
```
sudo aptitude install libapache2-mod-php5 postgresql-8.3
```

---

### Post by papapep on 2008-11-09
Si molt no m'equivoco, /usr/local és la ubicació habitual del servidor web a RedHat i derivats (els quals per cert l'anomenen httpd, no apache).

I sí, Janiga, a les versions derivades de Debian (com Ubuntu) amb un "aptitude install" o "aptitude remove" o "aptitude xxxxx" podràs satisfer el 95% (en condicions habituals) de les teves necessitats d'instal·lació de programari. No cal compilar, no cal fer invents estranys i, la majoria de vegades no cal gairebé ni configurar res.. :-)

Tal i com et comenta en RainCT, has d'anar amb compte d'on treus les instruccions, no per que estiguin malament, sinó per que et poden conduïr a fer més feina de la necessària, o a complicar-te una miqueta la vida si, com en aquest cas, barreges diferents estils de distribució, són antigues, o et topes amb un "fonamentalista de la compilació" que es compila fins els documents d'Openoffice (és un broma, evidentment...).
Et recomano, com sempre, llegir molt :-)
Al wiki de l'equip [tens uns quants documents que et poden guiar una miqueta al principi]("https://wiki.ubuntu.com/CatalanTeam/Recursos") per a tenir alguna referència, i no dubtis en demanar consell sobre com es pot fer "tal o qual cosa" o on trobar referències de documentació.

---

### Post by janiga on 2008-11-10
'sudo aptitude install libapache2-mod-php5 postgresql-8.3'

Doncs si que ha funcionat sense cap error... (i pensar tota la matada...en fi, he après moltes coses noves;))

Gràcies de nou

salut

Jaume

---

### Post by SiscoGarcia on 2008-11-10
> **janiga said:**
> Doncs si que ha funcionat sense cap error... (i pensar tota la matada...en fi, he après moltes coses noves;))

Doncs per acabar d'arreglar-ho bé, marca el fil com a resolt (Thread Tools>Mark This Thread As Solved) ;)

---


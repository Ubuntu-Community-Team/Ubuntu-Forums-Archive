---
title: "wifi radar"
date: 2008-11-02
forum: Catalan Team
---

### Post by venusfenix on 2008-11-02
buenas,

despres d'actualitzar-me a 8.10, tinc un problema,
a l'executar wifi-radar em diu lo següent:

No s'ha pogut executar el procés fill «su-to-root» (No such file or directory)

que pasa??
com es pot arreglar??

merci

---

### Post by PatrickVogeli on 2008-11-02
del teu problema ni idea, ho sento. Pero potser el [wicd]("http://wicd.sourceforge.net/") et serveix per sortir del pas.

salut

---

### Post by papapep on 2008-11-02
Per cert, al fil del tema del Wicd: no sé si és un cas generalitzat o concret meu, però les versions superiors a la 1.4.2 m'han portat molts problemes. He hagut de baixar-me aquesta (la 1.4.2) per tornar a funcionar com una seda (amb Intrepid). Si algú es troba amb pegues que provi això.

---

### Post by PatrickVogeli on 2008-11-02
curios, jo m'he instal·lat la 1.5.4 avui i va com la seda, i abans d'aquesta la .3, la .2., .1 i la 1.5.0. i sempre perfecte.

Et puc dir que entre la 1.4.2 i les versions 1.5 una de les coses que han canviat es la ubicacio dels fitxers: a la 1.4.2 s'instalaven moltes coses sota /opt/wicd i a les noves s'ha pasat a /usr. No se si aixo pot influir, pero igual desintal·lar i assegurar-te que queda tot borrat i instal·lant la 1.5.4 ajuda.

salut

---

### Post by papapep on 2008-11-02
Ho sé, ho sé...si vaig estar buscant un grapat de dies...però passo de complicar-me, per ara. Em quedo amb la 1.4.2 i a veure si més endavant em ve un atac de ganes i provo amb les 1.5.x ;-)

---

### Post by venusfenix on 2008-11-03
buenas,

m'he instal.lat el wicd, pero continua sense funcionar, amb fils sense problemes, pero la xarxa sense fils, no hi ha manera.
es posible que no funcioni perque utilitzo el canal 12??

---

### Post by open-pitu on 2008-11-03
Anem a provar manualment si funciona el wifi del teu ordinador.

Primer de tot averiguarem l'interfície de la teva targeta
[INDENT]$iwconfig[/INDENT]
Aquí podem detectar quina és (normalment eth1, ra0...)

Si aquí ja no detecta quina interfície de wifi és malament rai... Però ho seguirem intentant.

Suposem que has detectat que la teva interfície és eth1, passem a buscar quines xarxes detecta la teva màquina:
[INDENT]sudo iwlist eth1 scan[/INDENT]

Ara ja només queda connectar-se a la nostra xarxa
[INDENT]sudo ifconfig eth1 up
sudo iwconfig eth1 essid NomDeLaNostraESSID
sudo iwconfig eth1 key s:LaContrassenyaDeLaXarxa
sudo dhclient eth1[/INDENT]

En principi ara hauríes d'estar connectat. Prova si funciona la connexió amb el teu navegador. Si és així crea un fitxer executable amb les comandes que acabes d'executar.
[INDENT]$sudo gedit /bin/connecta.sh[/INDENT]
Insertes les comandes que acabes d'executar. I Executes:
[INDENT]$sudo chmod +x /bin/connecta.sh[/INDENT]

Ara des de el terminal quan obris l'ordinador executes connecta.sh i ja et connectaràs a la teva xarxa sense fil.

Si mires coses de shells scripts pots aconseguir que el connecta sigui un miniprograma. Si necessita ajuda digam-ho.

---

### Post by venusfenix on 2008-11-05
buenas,
perdona el retras, pero paso a detallar:
ipconfig
bash: ipconfig: command not found
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Francesca"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


// com pots comprobar la xarxa wlan0 te vinculat una xarxa, pero no funciona, vull dir que no tinc access a internet, en el moment que desconecto el cable, em quedo sense conexio.

el següent pas, escanejar xarxes, hi troba, les mateixes que veig a traves del wicd. no faig llistat, doncs m'he trobat amb problemes a l'hora de fer el post.

que pasa doctor??

ara paso a fer el que indiques, conectar la wifi i configurar, pero a la primera ordre, no hi ha resposta.

sudo ifconfig wlan0 up
sudo: unable to resolve host Shuttle

en aquest moment, no continuo,prefereixo esperar-me a veure que contestes.
que penses que pot passar??

gracies,

---

### Post by torracastanyes on 2008-11-05
Ja has vist això ?:

[http://ubuntuforums.org/showthread.php?t=966897&page=3](http://ubuntuforums.org/showthread.php?t=966897&page=3)

---

### Post by venusfenix on 2008-11-06
he seguit els passos , i cambiat el canal al 2, pero continua igual.
aquest cap de setmana, provare de començar de nou, o sigui, desfer la configuració del router i anant pas a pas.
potser es aixo??

gracies,

---

### Post by PatrickVogeli on 2008-11-06
jo diria que es alguna cosa del router, ja que es un problema bastant extrany. Per provar: assegura't que no estas amagant l'essid i possa'l al canal 6 i sense encriptacio, a veure que pasa.

salut

---

### Post by open-pitu on 2008-11-06
Bones!

Et vas quedar en el punt que realment anàvem a intentar connectar.

[INDENT]sudo ifconfig wlan0 up[/INDENT]
[INDENT][INDENT]--->el que fas és activar la wifi per si decas no hi estava. Per tancar és down.[/INDENT][/INDENT]

Per tant, com que tens la targeta de xarxa wifi engegada  és quan t'intentes connectar amb aquestes comandes:

[INDENT]sudo iwconfig wlan0 essid Francesca [/INDENT]
[INDENT][INDENT]---> No recordo si s'havia de posar com "Francesca". D'aquesta manera indiques a quina xarxa vols connectar-te[/INDENT][/INDENT]
[INDENT]sudo iwconfig wlan0 key s:LaContrassenyaDeLaXarxa[/INDENT]
[INDENT][INDENT]--->Aquest pas indiques la cotnrassenya. També pots provar d'obrir la teva xarxa wifi per provar-ho sense. En el meu antic portàtil no em podia connectar a la wifi (sota Ubuntu 8.04) però amb altres màquines amb la amteixa distribució o altres SOs si que podia.[/INDENT][/INDENT]
[INDENT]sudo dhclient wlan0[/INDENT]
[INDENT][INDENT]--->Amb aquesta comanda indiques adreçament dinàmic sota el protocol dhcp. És necessari.[/INDENT][/INDENT]

Perdona per no explicar abans què feia cada comanda, ja que d'aquesta manera ho haguesis provat.

Seguim comunicats i expliques com evoluciona.

---

### Post by venusfenix on 2008-11-08
bon dia,

he començat desde cero, i res, diguem que he resetat el router i començat com si fos nou.
El tema, es que ubuntu (wicd) hem veu la xarxa, fa la conexio i en el moment de assignassio de ip es quan la treu de la wifi...potser ser???
a traves d'un altre ordinador amb windows XP, vaig fent el canvis al router i monitoritzant la conexió pero el router mai li arriva a assignar IP.

alguna solució??

gracies,

---

### Post by venusfenix on 2008-11-08
bon dia,

altre pista mes, soc client d'ONO, i ja m'ha passat algun cop que quant vols "donar" d'alta un ordinador nou a la xarxa d'internet d'Ono, has de fer-ho d'una determinada forma...(?????)

---

### Post by newbrocca_2 on 2008-11-08
> **venusfenix said:**
> buenas,

despres d'actualitzar-me a 8.10, tinc un problema,
a l'executar wifi-radar em diu lo següent:

No s'ha pogut executar el procés fill «su-to-root» (No such file or directory)

que pasa??
com es pot arreglar??

merci


 see this ...[http://ubuntuforums.org/showthread.php?t=968741&highlight=wifi+radar](http://ubuntuforums.org/showthread.php?t=968741&highlight=wifi+radar)

newbrocca

---


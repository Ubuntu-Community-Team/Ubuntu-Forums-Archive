---
title: "Sense connexió a internet"
date: 2008-11-07
forum: Catalan Team
---

### Post by Lluís Martí on 2008-11-07
Hola a tothom i a totdon.

Sense cap motiu aparent (no recordo haver canviat res) m'he quedat sense connexió al router (3CRADSL72 de 3COM) i per tant sense accés a internet. En principi crec que no és un problema del router, atès que he provat de connectar-m'hi per cable des del portàtil i funciona perfectament, si bé cal dir que a la torre hi tinc 8.04 i al portàtil 8.10 (+Vista). En principi a l'arxiu /etc/network/interfaces hi tinc el mateix:
"    auto lo
    iface lo inet loopback
    auto eth0
    iface eth0 inet dhcp"

De fet, Ubuntu reconeix la meva tarjeta de xarxa com el dispositiu eth0, i si faig "sudo ifconfig eth0 up" i "sudo ifup eth0" em retorna "ifup: interface eth0 already configured". El problema és que activant-la  en mode DHCP el router no retorna res: "No DHCPOFFERS received" quan faig un sudo dhclient eth0. De fet, ni tan sols puc accedir al router per configurar-lo, ja que no em retorna cap pàgina al posar la ip del router al firefox.

Porto dies buscant per la xarxa, i vaig trobar un fil de mitjans de juliol del 2006 que li passava el mateix però en canvi sí es podia connectar des de windows (jo només hi tinc ubuntu a la màquina) però també des del live cd (a mi no em connecta amb cap live cd, ni amb la 8.04, ni amb 7.10...). La qüestió és que aquell usuari després de molt barallar-se va optar per tornar a instal·lar la versió anterior (diria que era la breezy) amb la que sí que li funcionava i després va actualitzar a la següent.

Entenc que és una solució extrema (i en el meu cas sense gaires garanties, ja que no em funciona tampoc amb els live cd) i m'agradaria trobar la raó del perquè ha passat tot plegat, encara que només sigui per aprendre'n una mica. Us agrairé si em podeu donar un cop de mà.

Per cert, la meva tarja Ethernet és una Realtek RTL-8169.

Gràcies per endavant!

---

### Post by papapep on 2008-11-07
Haurem d'anar a pams, Lluís, ja que no tenim gaire informació per treballar.

Enganxa el que et mostrin les següents ordres:

```
ifconfig
```

```
route -n
```

```
less /etc/resolv.conf
```

Si dius que tens la Hardy, deus fer servir el Network Manager antic que, en teoria, no donava els problemes que dona a alguna gent el nou amb l'Intrèpid.

Has provat a configurar-lo amb una ip estàtica a veure si et funciona correctament?

---

### Post by Lluís Martí on 2008-11-08
sí, disculpa, suposo que he anat massa pel dret! això és el que em surt:

```
**ifconfig**
eth0      Link encap:Ethernet HWaddr 00:80:5a:67:6c:9a
          inet6 addr: fe80::280:5aff:fe67:6c9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:420 (420.0 B) TX bytes:8716 (8.5 KB)
          Interrupt:11 Base address:0x8000

eth0:avahi Link encap:Ethernet  HWaddr 00:80:5a:67:6c:9a
          inet addr:169:254:7:28  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:78612 (76.7 B) TX bytes:78612 (76.7 KB)

```

(si bé la informació relativa a eth0:avahi no apareix sempre)
més:

```
**route-n**
Kernel IP routing table
Destination     Gateway      Genmask        Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0      255.255.255.0  U     0      0        0 eth0
0.0.0.0         192.168.2.1  0.0.0.0        UG    100    0        0 eth0

```

i per acabar:
```
**less /etc/resolv.conf**
nameserver 192.168.2.1

```

respecte a la ip estàtica, he fet la prova i tot i que lenta d'entrada em funcionava la connexió. el més curiós és que al tornar a configurar-ho com DHCP per uns instants m'ha funcionat, però de seguida m'he tornat a quedar sense connexió (!)

---

### Post by papapep on 2008-11-09
Té aspecte de poder ser algun problema amb l'avahi. Enganxa el que et surti fent això:

```
sudo aptitude search avahi |grep ^i
```

---

### Post by Lluís Martí on 2008-11-09
potser sí, tot i que com ja comentava abans les línies referents a **eth0:avahi** no m'apareixen sempre.

en tot cas, de l'ordre que em comentaves em surt això:

```
**sudo aptitude search avahi |grep ^i**
i   avahi-autoipd                    - Avahi IPv4LL network address configuration
i   avahi-daemon                     - Avahi mDNS/DNS-SD daemon
i   libavahi-client3                 - Avahi client library
i   libavahi-common-data             - Avahi common data files
i   libavahi-common3                 - Avahi common library
i   libavahi-compat-libdnssd1        - Avahi Apple Bonjour compatibility library
i   libavahi-core5                   - Avahi's embeddable mDNS/DNS-SD library
i   libavahi-glib1                   - Avahi glib integration library
i A libavahi-qt3-1                   - Avahi Qt 3 integration library
i A libavahi-ui0                     - Avhi GTK User interface library
```
gràcies per l'ajuda!

---

### Post by papapep on 2008-11-09
Buscant he trobat una possible pista del problema. Enganxa el contingut del fitxer /etc/udev/rules.d/85-ifupdown.rules:

```
cat /etc/udev/rules.d/85-ifupdown.rules
```

---

### Post by papapep on 2008-11-10
Per cert, el Carles Oriol m'ho ha comentat i és cert, a mi se m'ha passat..., ja has provat amb un altre cable de xarxa que aquest no tingui cap problema???

---

### Post by Lluís Martí on 2008-11-10
bé, doncs, seguim fent proves:

```
**cat /etc/udev/rules.d/85-ifupdown.rules**
# This file causes network devices to be brought up or down as a result
# of hardware being added or removed, including that which isn't ordinarily
# removable.
# See udev(7) for syntax.

SUBSYSTEM=="net", DRIVERS=="?*", GOTO="net_start"
GOTO="net_end"

LABEL="net_start"

# Bring devices up and down only if they're marked auto.
# Use start-stop-daemon so we don't wait on dhcp
ACTION=="add",		RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup -- --allow auto $env{INTERFACE}"
ACTION=="remove",	RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown -- --allow auto $env{INTERFACE}"

LABEL="net_end"

```

respecte a lo del cable, ja ho provaré, tot i que quan vaig provar de connectar-me al router amb el portàtil ho vaig fer amb el mateix cable.

agraït!

---

### Post by Lluís Martí on 2008-11-14
hola,
només escric aquest missatge per pujar el fil (:oops:). 
en papapep em va demanar una informació sobre les **ifupdown.rules**, però sembla que es va oblidar de mi (!).
disculpeu!

---

### Post by papapep on 2008-11-14
> en papapep em va demanar una informació sobre les ifupdown.rules, però sembla que es va oblidar de mi (!).

No et puc contestar si no tinc clar què dir-te, ni temps per buscar-ho... :-)

Primer millor fer-ne una còpia de seguretat:

```
sudo cp /etc/udev/rules.d/85-ifupdown.rules /etc/udev/rules.d/85-ifupdown.rules.backup
```

Un cop assegurada l'esquena, l'edites i el deixes així:

```
# This file causes network devices to be brought up or down as a result
# of hardware being added or removed, including that which isn't ordinarily
# removable.
# See udev(7) for syntax.

SUBSYSTEM=="net", DRIVERS=="?*", GOTO="net_start"
GOTO="net_end"

LABEL="net_start"

# Bring devices up and down only if they're marked auto.
# Use start-stop-daemon so we don't wait on dhcp
ACTION=="add",		RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup --allow auto $env{INTERFACE}"
ACTION=="remove",	RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown --allow auto $env{INTERFACE}"

LABEL="net_end"
```

(no sé si te n'has adonat, però l'únic que de fet fem és treure dos guions "--" seguits de dues línies, ja que hi ha gent que fent això ho ha arreglat)

Un cop fet això, cal reiniciar el servei de xarxa (si dubtes, reinicies l'ordinador i punt):

```
sudo /etc/init.d/networking stop
```

Veuràs un missatge que diu que s'atura, i:

```
sudo /etc/init.d/networking start
```

I veuràs que es torna a posar en marxa.

Ara és quan hauries de provar a veure què passa.

Per cert, no has dit res de la prova del cable, i és un tema que hauriem de tenir clar si és o no és el que causa el problema.

---

### Post by Lluís Martí on 2008-11-17
doncs no hi ha hagut sort! he modificat els guions del **85-ifupdown.rules** però al fer l'**start** em continua mostrant els mateixos problemes, amb el missatge final:
```
No DHCPOFFERS received
```
respecte al cable, es pot descartar com a causa de l'error, ho he provat amb un de nou i res de res. de fet, amb el cable original em connecto correctament des del portàtil.
alguna nova idea? gràcies!

---

### Post by Lluís Martí on 2008-12-02
després d'anar provant diverses cosetes que he anat trobant per diversos fòrums, vaig optar per provar d'instal·lar la 8.10, però el resultat malauradament va ser el mateix.

la darrera alternativa va ser provar amb una altra targeta de xarxa, i en aquest cas sí va funcionar la connexió a la perfecció. em sap greu haver acabat anant a l'opció més fàcil [:oops:] hagués preferit treure'n l'entrellat de tot plegat, però tants dies desconnectat del món se'm feia massa avorrit!

en tot cas, em pregunto si simplement es tractava que la ethernet antiga estava feta malbé, tot i que la reconeixia. hi hauria alguna manera de verificar-ho?

per acabar, un dubte: he de marcar aquest fil com a sol·lucionat?

gràcies per la vostra col·laboració.

---

### Post by papapep on 2008-12-02
> en tot cas, em pregunto si simplement es tractava que la ethernet antiga estava feta malbé, tot i que la reconeixia. hi hauria alguna manera de verificar-ho?


Ficant-la a un altre ordinador i provant-la.

> per acabar, un dubte: he de marcar aquest fil com a sol·lucionat?

Al teu criteri, és el teu fil. Per una banda sí, ja que has conseguit connectar-te a inet, però per l'altra ho has fet pel dret. O sigui que, tu tries :-)

---


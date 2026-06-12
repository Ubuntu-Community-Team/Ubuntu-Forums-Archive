---
title: "[SOLVED] ubuntu 8.04 i gestor d'actualitzacions"
date: 2008-04-27
forum: Catalan Team
---

### Post by bratac on 2008-04-27
Bones,

per actualitzar-me a l'ubuntu 8.04 vaig utilitzar «el millor servidor» dins de la llista de fonts de programari. Un cop actualitzat el sistema volia accedir de nou a «fonts de programari» per a canviar-me al servidor principal. Cada cop que clico a «fonts de programari» no se'm carrega el programa. A més, el gestor d'actualitzacions es pot passar hores esperant la llista amb els paquets (no surt ni la barra de progrés) Si vaig al monitor del sistema, em diu que està adormit. Algú em pot ajudar a solucionar-ho?

Gràcies.

---

### Post by jmaspons on 2008-04-27
Hola,
pots modificar manualment les fonts editant el fitxer /etc/apt/sources.list

Amb un editor de text com el Kate pots obrir un dialeg per canviar cadenes de text amb Ctrl + r. Així pots modificar ràpidament totes les adreces que vulguis.

Sort!

---

### Post by bratac on 2008-04-30
Gràcies, però igualment encara no puc obrir el gestor de fonts de programari, ni el synaptic, a més, se'm penja el gestor d'actualitzacions. 

Algú em pot dir com ho puc solucionar?

gràcies.

---

### Post by RainCT on 2008-05-01
Executa el Synaptic des de la terminal i enganxa'ns el que et digui.

---

### Post by bratac on 2008-05-02
Bones, 

no sé com s'executa el synaptic des del terminal, m´ho podeu dir?

M'he adonat que, de fet, no puc instal·lar ni desintal·lar cap tipus de programa (ni amb el gestor de programes que hi ha al menú aplicacions) Pot ser que tingui algun problema amb l'apt?

Des de que m'he actualitzat no tinc cap actualització i a més no puc obrir li el programa de fonts de programari ni el synaptic.

Gràcies.

---

### Post by menut on 2008-05-02
És senzill:
```
sudo su
synaptic
```

---

### Post by bratac on 2008-05-02
Gràcies menut, em diu això:

bratac@laptop:~$ sudo su
synaptic
sudo: unable to resolve host laptop
bratac@laptop:~$ synaptic


i m'obre el synaptic. Què faig ara, per poder actualizar-me el sistema i poder desinstal·lar un parell de programes?

---

### Post by papapep on 2008-05-02
Per executar el synaptic:

```
sudo synaptic
```

Tot i això, seria interessant veure primer que et funcioni com cal el sistema de gestió de paquets:

```
sudo aptitude update
```

i 

```
sudo aptitude safe-upgrade
```

a veure si funcionen.

Edito: no havia vist la resposta d'en Menut.

Per l'error del "sudo: unable to resolve host laptop", enganxa el contingut del fitxer /etc/resolv.conf:

```
cat /etc/resolv.conf
```

---

### Post by bratac on 2008-05-03
Bones,

he fet el que m'heu dit (o el que jo he entès que havia de fer), us poso aquí el que he copiat del terminal (ordre i resposta)

bratac@laptop:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4924
#
### END INFO



nameserver 192.168.1.1


bratac@laptop:~$ sudo synaptic
sudo: unable to resolve host laptop

bratac@laptop:~$ sudo aptitude update
sudo: unable to resolve host laptop


bratac@laptop:~$ sudo aptitude safe-upgrade
sudo: unable to resolve host laptop

Si no ho he fet bé perdoneu la meua poca experiència en temes «terminals» Què he de fer ara, per a solucionar el problema?

Gràcies per la vostra ajuda.

---

### Post by papapep on 2008-05-03
Ups, quan et vaig dir /etc/resolv.conf, volia dir /etc/hosts.
Però tampoc em va malament veure aquest abans. No tens configurat cap  servidors de DNS (a no ser que el teu ordinador en sigui un) D'on obtens la ip de l'ordinador, per DHCP? o la tens fixa?

A més del contingut del /etc/hosts, enganxa el que et surti en fer

```
ifconfig
```

---

### Post by bratac on 2008-05-03
Bones,

he fet el que m'has dit:

bratac@laptop:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bratac@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:99:02:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:13:02:14:d6:fd  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe14:d6fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7356785 (7.0 MB)  TX bytes:752526 (734.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101401 (99.0 KB)  TX bytes:101401 (99.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-14-D6-FD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


la configuració és dhtml. 

pd. Avui m'ha arribat una actualització però quan clico a actualitza el programa no fa res...

---

### Post by papapep on 2008-05-03
El fitxer /etc/hosts, a banda del que hi ha ara, també hauria de tenir una línia com la següent:

```
127.0.0.1 localhost
```

Quan ho hagis afegit, torna a provar el **sudo aptitude update** i enganxa el missatge que et mostri.

---

### Post by bratac on 2008-05-03
Bones,

com ho faig per a posar el

127.0.0.1 localhost ?

Gràcies!

---

### Post by papapep on 2008-05-03
A un terminal:

```
sudo nano /etc/hosts
```

afegeixes el que t'he dit abans a la línia que vulguis. Un cop estiguis, fas Ctrl+X i ho desaràs.

---

### Post by bratac on 2008-05-03
Bones,

no em deixa posar el 127...

quan faig 

bratac@laptop:~$ sudo nano /etc/hosts
sudo: unable to resolve host laptop

Em diu això!

---

### Post by papapep on 2008-05-03
I des de l'entorn gràfic?

Fes Alt+F2 i posa:

```
gksudo gedit /etc/hosts
```

---

### Post by bratac on 2008-05-03
Bones,

ho he fet i em surt a la barra inferior un botó que diu «s'està llançant l'aplicació» després desapareix el botó i no surt res més.

Potser seria més fàcil fer un format c: i instal·lar-ho de nou?

---

### Post by RainCT on 2008-05-03
No podras editar el fitxer des de l'Ubuntu, ja que el sudo necessita que la línia aquesta ja estigui al /etc/hosts, però té solució fàcil: triar el mode de recuperació a l'encendre l'ordinador i quan et deixi en una terminal de root canviar-ho des d'allà.

Ah, i el "format c:" és una cosa del Finestres; amb GNU/Linux no es diu així.

---

### Post by bratac on 2008-05-03
Bones,

com puc triar el mode de recuperació a l'iniciar l'ubuntu? Quines tecles he de tocar?

gràcies!

---

### Post by bratac on 2008-05-04
Eii, 

he aconseguit fer lo de la 127.0.0.1, també he fet l'ifconfig, em dóna això:

bratac@laptop:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts

::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost
bratac@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:99:02:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:13:02:14:d6:fd  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe14:d6fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:607924 (593.6 KB)  TX bytes:126570 (123.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102370 (99.9 KB)  TX bytes:102370 (99.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-14-D6-FD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

No em funciona ni el sudo synaptic, ni el sudo aptitude update ni el sudo aptitude safe-upgrade.

El missatge d'error és el següent:
bratac@laptop:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   7656
#
### END INFO



nameserver 192.168.0.1

Vaig pel bon camí? Com ho puc acabar de solucionar?

---

### Post by bratac on 2008-05-08
Ja ho he solucionat!!! Però no puc marcar el fil com a solucionat :(, algú ho pot fer (a threat tools no hi ha l'opció)? Gràcies

---

### Post by canroca on 2008-05-26
Hola;

No se si finalment aquest fil s'ha tancat però jo no he acavat d'entendre la solució.
He estat revisant la configuració i aparentment tinc be els parametres de localhost i d'alres. 

L'arxiu etc/hosts diu:
127.0.1.1 cuina.canroca

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost

L'arxiu etc/resolv.conf:
search lan
nameserver 192.168.1.1
domain canroca

Finalment ifconf:
eth0      Link encap:Ethernet  HWaddr 00:1d:60:13:e1:52  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe13:e152/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1273623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1327122 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:380010556 (362.4 MB)  TX bytes:1292591161 (1.2 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:274148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1097491711 (1.0 GB)  TX bytes:1097491711 (1.0 GB)

Pot algu donar-me alguna idea sup?
Això m'està passant poc després de pasar a Hardy Heron i incloure manualment una font de programari per a AWN.

Gràcies per endevant

---

### Post by papapep on 2008-05-26
> No se si finalment aquest fil s'ha tancat però jo no he acavat d'entendre la solució.

Si noi, és el que passa quan un no explica com ha pogut solucionar els problemes...que el que ve a darrera es queda en pilotes....

Per cert....a tu què et passa en concret??? no recordo haver vist cap altre post teu sobre aquest tema...t'has afegit al fil però no sé d'on baixes. :-)

---

### Post by canroca on 2008-05-26
Hola company;

Fa unes tres setmanes vaig passar a Hardy i des de llavors havia de picar unes dos o tres vegades per arrencar Fonts de Programari o Synaptic. A banda els AWN no m'acavaven de funcionar i el gestor d'actualitzacions anava de pena. 
Llavors vaig veure en un forum en anglès que recomenaven editar a ma l'arxiu de fonts de programari per descarregar actualitzacions de AWN d'un altre lloc (que evidentment no vaig apuntar) i ho vaig canviar. També deien que el problema era que tanta gent s'estava passant a Hardy que colapsaven els servidors de descarrega i que recomenaven que abans de fer cada actualització busquesis "el millor servidor". Això em va anar be durant uns dies però per acavar-ho d'adobar se'm va acudir canviar el ruter de casa i canviar el nom de domini.
Des de llavors no em xuta res. Ni Synaptic, Ni gestor d'actualitzacions, Ni Fonts de programari, Ni DeVeDe, Ni comprovació de maquinari.
En fi, estic frexit...però m'ho paso be amb el meu Ubuntu, que consti...

---

### Post by papapep on 2008-05-26
mmm....a veure, que jo ho entengui...no et va bé la gestió de paquets, però sí que et pots connectar a internet? és això?

A banda de respondre la pregunta anterior, enganxa aquí el que tens al /etc/apt/sources.list

Per cert, si no ho has fet ja, estaria bé que et passessis pels dos fils "imprescindibles" pels nouvinguts que són a la capçalera del fòrum ;-)

---

### Post by canroca on 2008-05-26
Efectivament. Cap problema amb l'accés a internet o els podcasts.
Fins i tot executant el gestor de paquets des del terminal cap problema.

Quistà el sources.list i ara em paso pels imprescindibles:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets

#AUTOMATIX REPOS START


deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy-proposed universe main multiverse restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy-proposed universe main multiverse restricted
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy-backports universe main multiverse restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) hardy-backports universe main multiverse restricted
#AUTOMATIX REPOS END
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

---

### Post by papapep on 2008-05-29
Si vols evitar problemes, el primer que hauries de fer és carregar-te totes les fonts de programari no oficial, però especialment les de l'automàtix, que són una font de problemes important. Busca al fòrum i veuràs els antecedents...

Després, el que jo faria és fer neteja i deixar el sources.list amb els oficials i poca cosa més:

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

```

Fet això, fer:

```
sudo aptitude update && sudo aptitude upgrade
```

i provar a veure si el que no funcionava ara ja va.
T'aviso que com que sembla que tens cert problema a la base de paquets, la solució que t'he dit no és 100% lliure de probabilitats d'error, fet pel qual has de valorar tu si l'apliques o no (encara que actualment ja tens problemes, o sigui que...) ;-)

---

### Post by RainCT on 2008-06-01
Tiuuuu! Aquí falten les hardy-security! :P

Posa-hi això:

```

deb http://archive.ubuntu.com/ubuntu/ hardy universe restricted main multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted

```


I si també vols els paquets de codi font, un dels següents:

Per als paquets de la Hardy:
```

deb http://archive.ubuntu.com/ubuntu/ hardy universe restricted main multiverse

```

Per als últims (els de la Intrepid):
```

deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse

```

---

### Post by RainCT on 2008-06-01
[Post duplicat... El fòrum està tonto]

---

### Post by canroca on 2008-06-01
Val doncs
Entenc que el que he de fer es editar el sources.list (després de guardar-ne copia) i esborrar totes les entrades excepte les que heu descrit. Executar llavors la busqueda de fonts des de'l terminal eh voila.
A partir d'aqui, compte amb afegir fonts de programari a les recomanades per Canonical o comprovar abans en el forum que siguin "fiables".

Salutacions i gràcies. He de fer alguna cosa per tancar el fil?

---

### Post by papapep on 2008-06-01
> A partir d'aqui, compte amb afegir fonts de programari a les recomanades per Canonical 

Bé, aquesta és una bona manera de començar, tot i que la pràctica ja t'ajudarà a discriminar quines són més fiables i quines més arriscades.

Per intentar sortir del problema on ets ara, com a mínim, sí que es interessant fer "cau i net" i tornar a les fonts oficials.

Per cert, si dones el fil per resolt, jo no ho faria fins que tinguessis el problema arreglat, tens l'opció "Mark thread as solved" al menú "Thread tools", en vermell damunt dels fils.

---

### Post by canroca on 2008-06-01
Doncs tens tota la raó papapep. El problema no s'ha resolt.
He eliminat les fonts de l'Automatix i res. He executat 
sudo aptitude update && sudo aptitude upgrade 
i l'actualització s'ha fet però m'ha advertit que les fonts d'AWN podien no ser segures.
He eliminat la línia 
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
I això tampoc ha funcionat
Finalment he planxat el sources.list amb les vostres recomanacions (veieu més a baix) i tampoc. He deixat inactives les fonts de fonts de paquets, imagino que això es per usuaris avançats.
En tots els canvis he anat guardant els arxius i reiniciant la màquina però Fonts de programari i Synaptic segueixen sense arrencar.

#sources.list recomanat per en papapep com el minim necesari
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
#hardy security recomanat per en RAINCT
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe restricted main multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
#fonts per a paquets en codi font de Hardy
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe restricted main multiverse
#i els paquets en codi font de la Intrepid
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

---

### Post by papapep on 2008-06-01
En tot cas, deixa'ns veure què et mostra en fer l'aptitude update i l'aptitude safe-upgrade. Enganxa tot el totxo (o, si és massa gran, adjunta un fitxer amb el text).
Els repositoris de fonts no són per a experts, són per quan fan falta. No t'ha de fer cap mal tenir-los a mà.

---

### Post by canroca on 2008-06-01
Aquí teniu l'arxiu. No he pensat en enviar-lo amb el post anterior.
Gràcies per l'ajuda
:guitar:

---

### Post by papapep on 2008-06-02
> sudo: unable to resolve host cuina

Bé, per aquí tenim una pista. Enganxa el que tinguis a /etc/hosts, si us plau:

---

### Post by canroca on 2008-06-02
Aquí està

127.0.1.1 cuina.canroca

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost

salutacions

---

### Post by bratac on 2008-06-02
Bones,

perdoneu de no donar-vos la meva solució. Com que no vaig tenir més paciència i veia que el fil estava una mica oblidat vaig desar el meu usuari en un disc dur extern i ho vaig formatar tot. En començar de nou tot em funciona com una seda.

Gràcies!

---

### Post by papapep on 2008-06-02
> 127.0.1.1 cuina.canroca

Prova a deixar aquesta línia només amb:

```
127.0.1.1 cuina
```

suposant que "cuina" sigui el nom de l'ordinador.

---

### Post by canroca on 2008-06-03
Oe, Oe, Oe...Funciona
Vaig ser jo qui s'ho va carregar quan vaig instal·lar el nou router i reconfigurar la xarxa.
Varies coses:
- La informació que he trobat als manuals en línia sobre la configuració de xarxa es la única part que trobo una mica fluixa de tot el tema Ubuntu. La utilització de IP fixes o DHCP, els serveis de compartir fitxers via Samba, compartir impressores en xarxa, etc. A banda de mirar els foros, hi ha algun document que expliqui la configuració de xarxa que recomaneu??? (encara que no sigui pregunta d'aquest thread)
- Suposo que puc tornar al meu antic sources.list...de fet em costava molt baixar-me actualitzacions abans fins i tot de canviar el router?

Finalment donar-vos les gràcies a tots, no per la solució, sinó per el temps dedicat a algú qui no coneixeu.

Salutacions i fins al proper marró, a veure si puc ser jo qui ajudi a algú altre.
:guitar:

---

### Post by papapep on 2008-06-03
Apa, doncs ja pots marcar el fil com a resolt: Thread tools > Mark thread as solved. :-)
Bé, com que veig que no el vas iniciar tu ja el marco jo com a resolt.

---


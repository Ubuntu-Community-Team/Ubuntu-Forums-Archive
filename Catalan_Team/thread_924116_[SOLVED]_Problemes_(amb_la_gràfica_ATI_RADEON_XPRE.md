---
title: "[SOLVED] Problemes (amb la gràfica ATI RADEON XPRESS 1250?) a l'hora d'instal·lar ubu"
date: 2008-09-19
forum: Catalan Team
---

### Post by lo gambusí on 2008-09-19
Estic instal·lant ubuntu a un portàtil amb una gràfica com la que apareix al títol. Quan poso el live-cd i intento instal·lar l'ubuntu em dona el següent missatge:> MP-BIOS bug: 8254 timer not connected to IO-APIC.

Què puc fer?

---

### Post by papapep on 2008-09-19
Prova a passar-li el paràmetre "noapic" al kernel a l'arrencada.

---

### Post by lo gambusí on 2008-09-19
Ja ho he provat, i segueix igual.

---

### Post by papapep on 2008-09-19
Comprova si a la BIOS té l'opcio IOAPIC i desactiva-la.
Per cert, estaria bé tenir més pistes de la resta de ferro.

---

### Post by lo gambusí on 2008-09-19
Per desactivar-la l'he d'esborrar si apareix o he de posar NO IOAPIC?

---

### Post by lo gambusí on 2008-09-19
El PC, per cert, és un Samsung Core2Duo. No sé res més...

---

### Post by CarlesOriol on 2008-09-19
Al menu d'inici fes:

F6 - other options

i esborra la part de quiet i splash.

i inicia. (a veure que passa)

---

### Post by CarlesOriol on 2008-09-19
Parlem d'ina versió 8.04 8.04.1 o 8.10 oi?

En qualsevol cas l'intrepid ibex fa un pas de gegant a l'us de les ATIs

---

### Post by lo gambusí on 2008-09-19
Parlem d'una versió 8.04. Però l'Ibex no ha sortit encara, no? Només hi ha una Alpha...

Esborrant això que m'has dit es carrega però no surt la part gràfica, sinó que acaba dixant-me amb un > ubuntu@ubuntu:~$

---

### Post by lo gambusí on 2008-09-19
He entrat com a Recovery mode seguint los passos [d'este]("http://blog.gunbladeiv.com/2008/04/ubuntu-ati-crash-on-hardy-upgrade.html") web, però pel que veig no tinc connexió a internet, tot i estar connectat amb cable (coses de la configuració, suposo?), ja que fent ping a [www.ubuntu.cat](www.ubuntu.cat) em diu > ping: unknown host [http://www.ubuntu.cat](http://www.ubuntu.cat).

Què puc fer?

---

### Post by CarlesOriol on 2008-09-20
mmmm... em sembla que estas fent una mica de poti-poti. (jo seguia des del fil: *Com puc obrir una terminal des d'un LIVECD si no se'm carrega l'entorn gràfic* )

Anem per passos.

1r - Insta&#320;lem l'ubuntu (encara que ens falti el sistema gràfic, ja l'arreglarem)

Descarrega la versió alternate i fes la insta&#320;lació en mode text.

... quan estiguis expliques com ha anat i si tens conexió a internet i seguim.

---

### Post by lo gambusí on 2008-09-20
Bé, ja està instal·lat. Hauria de tenir connexió (estic connectat per cable, i ho estava durant la instal·lació) però fent pings no me la reconeix.

---

### Post by papapep on 2008-09-20
Per veure com està la configuració de xarxa cal mirar:

1.- Configuració de l'interfície (normalment, l'ethernet és eth0):

```
ifconfig eth0
```

Hauries de verificar que tant l'ip com la màscara de subxarxa (normalment 255.255.255.0, estan correctament configurats).

2.- Configuració de l'enrutat del kernel:

```
route -n
```

Aquí hauries de veure correctament configurada la passarela de sortida (normalment el router).

Si no ho està, pots fer (suposant que la passarela és 192.168.1.1):

```
sudo route add default gw 192.168.1.1
```

3.- Els servidors de DNS:

```
less /etc/resolv.conf
```

Aquí veuràs quins, si els tens, servidors de DNS té configurats el pc, amb el format (essent 1.2.3.4 l'ip del servidor DNS)

```
nameserver 1.2.3.4
nameserver 5.6.7.8
```

---

### Post by lo gambusí on 2008-09-21
> **papapep said:**
> Per veure com està la configuració de xarxa cal mirar:

1.- Configuració de l'interfície (normalment, l'ethernet és eth0):

```
ifconfig eth0
```

Hauries de verificar que tant l'ip com la màscara de subxarxa (normalment 255.255.255.0, estan correctament configurats).

Em surt el següent missatge: > Link encap:Ethernet HWaddr 00:13:77:35:9c:2c
BROADAST MULTIAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000
RX bytes:0 (0,0B) TX Bytes:0 (0,0 B)
Interrupt:22 Base address:0xa000

---

### Post by lo gambusí on 2008-09-21
El segon pas:

> route -n
> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface

---

### Post by lo gambusí on 2008-09-21
Code:

less /etc/resolv.conf
> 
nameserver 62.42.230.24
nameserver 62.42.63.52


---

### Post by papapep on 2008-09-21
Bé, doncs està clar que no tens la xarxa configurada.
Pots provar a fer-ho al network-manager (Sistema>Administració>Xarxa) o amb les ordres de terminal.

Abans, però, seria interessant veure que no tens cap altra interfície funcionant (que no sigui que no li hagi assignat el nom eth0):

Fes:

```
ifconfig
```

sense paràmetres.

---

### Post by lo gambusí on 2008-09-21
De manera gràfica no podré fer-ho, perquè no puc entrar al mode gràfic.

El que em surt quan faig ifconfig és > Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0,0B) TX Bytes:0 (0,0 B)

---

### Post by papapep on 2008-09-21
Bé, doncs fes:

```
sudo ifconfig eth0 1.2.3.4 255.255.255.0
```

Essent 1.2.3.4 la ip que li vols assignar.

```
sudo route add default gw 1.2.3.4
```

Essent 1.2.3.4 la ip de la teva passarela de sortida a internet.

Edita el fitxer /etc/resolv.conf i deixa'l tal i com t'he esmentat a un post anterior.

Un cop fet tot això hauries de tenir l'interfície de xarxa funcionant.

---

### Post by lo gambusí on 2008-09-21
> **papapep said:**
> Bé, doncs fes:

```
sudo ifconfig eth0 1.2.3.4 255.255.255.0
```

Essent 1.2.3.4 la ip que li vols assignar.

```
sudo route add default gw 1.2.3.4
```

Essent 1.2.3.4 la ip de la teva passarela de sortida a internet.

Edita el fitxer /etc/resolv.conf i deixa'l tal i com t'he esmentat a un post anterior.

Un cop fet tot això hauries de tenir l'interfície de xarxa funcionant.
Dues coses... 

a) Com sé quina IP li vull assignar?
b) Com sé la IP de la passarel·la de sortida?

Suposo que són coses molt bàsiques... :(

---

### Post by papapep on 2008-09-21
Has de saber la ip interna del teu router (de cara a la xarxa interna). Si, per exemple, és 192.168.1.1 aleshores el rang de la teva xarxa és de 192.168.1.2 (l'ú ja està agafat pel router) fins a 192.168.1.254 (el 255 és el broadcast i no es pot assignar a una placa física).

Aleshores, si saps la ip del router (la teva passarela de sortida) ja ho tens tot. Evidentment, a mi no me la demanis! :-D

---

### Post by lo gambusí on 2008-09-21
> SIOCSIFADDR: Invalid argument:confused::confused::confused::confused::confused:

---

### Post by papapep on 2008-09-21
Fent què? mostra la ordre, home...

---

### Post by lo gambusí on 2008-09-21
Perdó:)

Fent > sudo ifconfig eth0 192.168.0.20 255.255.255.0

---

### Post by papapep on 2008-09-21
Fes:

```
sudo ifup eth0
```

i torna a repetir la ordre anterior, a veure què diu.

Si segueix fent el burro, enganxa el contingut de /etc/network/interfaces.

---

### Post by lo gambusí on 2008-09-21
Em dóna lo mateix missatge que abans. Te copio lo que me surt quan faig *less /etc/network/interfaces*:> #The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
#iface eth0 inet dhcp

---

### Post by CarlesOriol on 2008-09-22
Gambu.

No pinta gens bé. Si no et reconex la ethernet tenim feina per rato. :-)

Per què no baixes una live de l'intrepid de [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com) per veure que tal anirà. 

Acabo de recordar que amb un samsung nou i una 8.04 vaig tenir molts problemes (em sembla recordar que era un model m40 o una cosa així)... l'altra opció a provar és descarregar la 8.04.1

---

### Post by lo gambusí on 2008-09-22
Bé, senyores i senyors, **es para mi motivo de honda satisfacción** anunciar-vos que **a)** l'Intrepid Ibex soluciona los problemes amb esta gràfica i **b)** tenim una xica nova dins la *secta.*:):):):):)

Moltes gràcies als dos!!!!!!!

---

### Post by papapep on 2008-09-22
> Bé, senyores i senyors, es para mi motivo de honda satisfacción

Uix...quina angúnia m'has fet venir amb aquesta frase....:frown:

Per altra banda, enhorabona per que funciona i per la nova "abducció" :-)

---

### Post by lo gambusí on 2008-09-22
:biggrin::biggrin::biggrin::biggrin::biggrin:

---


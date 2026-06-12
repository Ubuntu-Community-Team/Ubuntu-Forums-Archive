---
title: "Problema amb la DNS, em salta (canvia de cop)."
date: 2007-12-17
forum: Catalan Team
---

### Post by idrojsnop on 2007-12-17
Hola, com podeu veure als meus missatges, sóc un usuari nou, que farà cosa d'un dia que tinc el meu Ubuntu instal·lat a l'ordinador. L'he instal·lat perquè estic fart del Windows, sempre el mateix, per descobrir nous horitzons. També perquè el windows em xupava massa ram, i sobretot, per curiositat.

Bé, anem al gra.

El meu problema ha sigut, i encara és, l'internet. Com entrar-hi. Finalment, com podeu comprovar, hi he pogut entrar, però tot i així tinc problemes amb la DNS. A partir de les ajudes que  et proporciona l'Ubuntu, he pogut descobrir que el problema estava a la DNS, que em canvia. Hi ha unes DNS que em funcionen, que són les que poso jo, i les que l'ordinador em posa per defecte, fa que internet no em vagi.

Com puc fer per arreglar això? Com puc fer per posar jo les DNS per defecte?

No em sé explicar més ni millor, he fet el que he pogut, espero que em pogueu entendre. Moltes gràcies de totes maneres.

Una abraçada des de la Garrotxa.
Jordi.

---

### Post by papapep on 2007-12-17
Benvingut Jordi !

Hauries d'enganxar-nos aquí el que et mostrin les ordres següents, per separat, executades a un terminal:

```
cat /etc/network/interfaces
```


```
ifconfig
```


```
cat /etc/resolv.conf
```

---

### Post by kukat on 2007-12-17
Benvingut!! 

Mira a "Sistema", "Administració", "Xarxa". Allí pots configurar el DNS a la pestanya corresponent. 

Salutacions!

---

### Post by eduardsola on 2007-12-17
Ja t'havia dit que aquí segur que t'ajudarien.

Salut!

---

### Post by idrojsnop on 2007-12-18
Primer de tot donar les gràcies a tothom.

Papapep, aqui tens la resposta, gràcies per interessar-te:

**(La primera ordre)**
idrojsnop@snoopy:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp



auto eth0
______________________________
[B]
(Segona ordre)[/B]
idrojsnop@snoopy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:88:2A:6B:5F  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fe2a:6b5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1254086 (1.1 MB)  TX bytes:386736 (377.6 KB)
          Interrupt:20 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

______________________________
[B]
(Tercera ordre)[/B]

idrojsnop@snoopy:~$ cat /etc/resolv.conf
nameserver 80.58.61.250

______________________________

Moltíssimes gràcies.
Una abraçada des de la Garrotxa.
Jordi.

---

### Post by hakd0c on 2007-12-18
Hola Jordi,

Tens configurada la xarxa per dhcp o sigui que que hi ha algun aparell que et dona la direcció ip, la mascara de xarxa, la porta d'enllaç i les dns, per norma general sol ser el router el que dona aquesta informació.

Segons el meu punt de vista tens tres possibilitats.

1-Canvies la informació que subministra el router als clients de dhcp

2-Poses una ip estàtica la teu ordinador.
 La configuració per ip estatica hauria de ser en el teu cas.
     IP 192.168.1.2
     Mascara de xarxa 255.255.255.0
     Porta d'enllaç 192.168.1.1 (suposo ja que no surt aquesta informacio al detall que ens has passat, aixo ho pots saber fent un route el numero que posa al costat del default es el que hi has de posar)

   DNS posa-hi les que t'agradin.

3- Jo també soc de la garrotxa, per tant et puc donar un cop de ma.

---

### Post by idrojsnop on 2007-12-18
Sí, tinc la xarxa configurada per dhcp. Però això què significa?

Com es canvia la informació que subministra el router als clients de dhcp? és que no vull posar la IP estàtica, perquè per alguns jocs online em suposaria problemes.

Moltes gràcies.
Jordi.

PS: hakd0c, envia'm un privat amb el teu missatger i/o correu. ;)

---

### Post by papapep on 2007-12-18
DHCP [significa]("http://ca.wikipedia.org/wiki/DHCP") que el router t'assigna un [ip]("http://ca.wikipedia.org/wiki/IP") dinàmicament al pc cada cop que hi connectes en vers de tenir-la estàticament desada al sistema i que sempre sigui la mateixa.

Aleshores, per a resoldre el teu problema, al NetworkManager (Sistema > Administració > Xarxa) caldria dir-li que vols el servidor de DNS estàtic i no dinàmic (cosa que no sé si es pot fer, ja que no el faig servir). En tot cas, amb el Wicd, que és un altre gestor de xarxa que pot substituïr el NetworkManager, si que se li pot dir que agafi la ip dinàmicament i, en canvi, els servidors de DNS els agafi estàtics.

A més, al /etc/resolv.conf hi afegiria un altre servidor de DNS per si el que tens cau o té problemes temporals de connexió:

```
sudo nano /etc/resolv.conf
```

i afegeixes una línia on posi:

```
nameserver 80.58.61.254
``` 
(El servidor secundari de Teleagònica.)

Surt desant amb Ctrl+X

---

### Post by hakd0c on 2007-12-19
Quant torna a carregar el dhcp no es carrega el contingut del /etc/resolv.conf ?? jo diria que si que ho fa després ho provo.


No entenc aquesta frase.
```
és que no vull posar la IP estàtica, perquè per alguns jocs online em suposaria problemes.
```

Els jocs no miren si tens ip estàtica o dinàmica, poden necessitar ports redirigits(que no oberts, ja que això en un router no existeix) a una ip, si aquesta es estàtica funciona sempre, si la ip es dinàmica quant el router ten doni una altre deixarà de funcionar.

---

### Post by hakd0c on 2007-12-19
Pos es veritat si modifiques el fitxer /etc/resolv.conf encara que tinguis dhcp no el modifica

---


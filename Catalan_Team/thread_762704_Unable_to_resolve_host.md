---
title: "Unable to resolve host"
date: 2008-04-22
forum: Catalan Team
---

### Post by lluisalguero on 2008-04-22
Hola amics,
com que ja tenia ganes de provar la nova 8.04, vaig actualitzar-me a la beta disponible.

Alt+F2 -> update-manager –devel-release

i després de diverses "penjades" del portàtil, vaig poder actualitzar-lo.

Ara tinc el problema que no em deixa instalar cap programa via consola, synaptic, ni tant sols actualitzar (en tinc 221 de pendents)

Si vaig a la consola i vull instalar-me qualsevol programa, em diu el següent:

```
lluis@lluis-laptop:~$ sudo apt-get install ufraw
sudo: unable to resolve host lluis-laptop
lluis@lluis-laptop:~$ 

```

He buscat per aquest mons de Déu, i com no he trobat solució al problema...copio i pego:

> Quien se anime a probar la version Aplha de Hardy seguramente tendra problemas al intentar iniciar programas que requieren la contraseña del superusuario, desde la terminal sale el siguiente aviso:

sudo: unable to resolve host ubuntu

La manera de solucionaro es bien facil, editar el fichero /etc/hosts y cambiar la linea en que aparece 127.0.0.1 localhost por 127.0.0.1 localhost ubuntu guardar, reiniciar y listo.

Obviament no es pot fer desde la consola, ja que ens sortirà el mateix error.

Seguint llegint i he vist que la solució passa per anar a *Sistema->Preferències->Xarxa*i fer-ho des d'allà.

I ara us direu a que ve tot aquest rotllo...ben fàcil...simplement no em funciona el que he buscat per internet...

Què puc fer?

Gràcies per la vostra ajuda i suport

Lluís

---

### Post by elbuit on 2008-04-22
Una cosa, has comprovat que el /etc/hosts té una línia d'aquest estil?
```
127.0.0.1       localhost
127.0.1.1       lluis-laptop
```
Si no la té, podries iniciar en "mode administratiu" i editar-la amb per exemple:
```
nano /etc/hosts
```
Si no recorde mal quan vaig mirar el sudo, podria tindre una configuració on especificara privilegis per maquina, així sols el caldria un arxiu de configuració per a tota la xarxa.
Sembla, com si no fora capaç d'identificar el localhost.
Ja ens contes

---

### Post by crazyserver on 2008-04-22
jo recomano:
```
127.0.0.1 localhost lluis-laptop
192.168.0.5 lluis-laptop
```
o la teva ip a la segona línia

---

### Post by lluisalguero on 2008-04-22
El problema es com editar aquest arxiu (etc/hosts) si no puc fer servir el sudo...

Ara mateix ho tinc així:

```
127.0.0.1 localhost ubuntu
127.0.1.1 lluis-laptop.ample

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.6 LAPTOP
```

---

### Post by crazyserver on 2008-04-22
doncs el problema el tens aki.. com bé pots veure tens tres noms d'equip i  hauries de decidir-te per un (LAPTOP, ubuntu o lluis-laptop-ample). Millor que posis el mateix nom en tots tres (el localhost deixa'l escrit!;))
La solució passa per arrencar amb una live, muntar el disc on tens instalar l'ubuntu i modificar-lo des de la live.

Sort!

---

### Post by papapep on 2008-04-22
> El problema es com editar aquest arxiu (etc/hosts) si no puc fer servir el sudo...

Lluís, crec que els arbres no et deixen veure el bosc. M'explico:

La ordre "sudo apt-get install ufraw" no et falla per culpa del "sudo", sinó per que quan el teu ordinador intenta connectar amb el repositori de paquets que tens definit a /etc/apt/sources.list no pot per què no és capaç de resoldre (convertir el nom del servidor a una ip a la que connectar) el nom. Aleshores, si fas:

```
sudo nano /etc/hosts
```

m'hi jugo un parell de pèsols (Joaquim Mª Puyal dixit) a què no tens cap problema. 

Per cert, la línia de la ip 127.0.0.1 ha de ser **_sempre_** així:

```
127.0.0.1 localhost
```

Ni més ni menys. Després hi pots tenir altres línies amb altres ip's i noms de host, però aquesta va a missa. Sinó [el dispositiu loopback]("http://ca.wikipedia.org/wiki/Loopback") no funciona correctament.

A banda de rectificar el contingut del /etc/hosts, si et segueix fallant la connexió, enganxa el contingut del /etc/resolv.conf.

---

### Post by papapep on 2008-04-22
> **crazyserver said:**
> doncs el problema el tens aki.. com bé pots veure tens tres noms d'equip i  hauries de decidir-te per un (LAPTOP, ubuntu o lluis-laptop-ample). Millor que posis el mateix nom en tots tres (el localhost deixa'l escrit!;))
La solució passa per arrencar amb una live, muntar el disc on tens instalar l'ubuntu i modificar-lo des de la live.

No hi ha cap problema en tenir diferents hosts definits aquí. Precisament és el lloc per a fer-ho. Pensa que els hosts no tenen per què ser el propi sistema local. 
Pots tenir, per exemple, definit un servidor web propi amb la ip interna de la teva xarxa i així no et cal posar la ip al navegador, símplement ve aquí, troba el nom que has posat al navegador i el converteix a la ip que has posat. És com una mena, ja em perdonareu per la comparació, de nano-servidor de DNS :-)

---

### Post by crazyserver on 2008-04-23
m'ho apunto!XD tot i que era una recomanació per no liar-la i poder provar que estava correctament.

---

### Post by lluisalguero on 2008-04-23
papapep, ho havia intentat anteriorment, però ho he tornat a fer per si de cas...

```
lluis@lluis-laptop:~$ sudo nano /etc/hosts
sudo: unable to resolve host lluis-laptop
lluis@lluis-laptop:~$ 

```

/etc/resolv.conf

```
# generated by NetworkManager, do not edit!



nameserver 80.58.61.250
nameserver 80.58.61.254


domain AMPLE
```

---

### Post by Taiwo on 2008-04-23
I upgraded to Hardy last week; and have been unable to do a software update since the last 9 days. If i run update manager with a check activated it runs forever without any errors or messages. Please can someone suggest want can be done to resolve this issue. Thanks

---

### Post by SiscoGarcia on 2008-04-23
> **Taiwo said:**
> I upgraded to Hardy last week; and have been unable to do a software update since the last 9 days. If i run update manager with a check activated it runs forever without any errors or messages. Please can someone suggest want can be done to resolve this issue. Thanks

We don't understand what you're saying 'cos we speak catalan (this is the Catalan LoCo Team forum).

---

### Post by papapep on 2008-04-24
Doncs hauràs d'editar el fitxer des d'un livecd, esborres la segona línia (127.0.1.1...) i esborres l'Ubuntu de la primera.
Arrenques amb el cd, muntes el disc on tens aquest /etc/hosts i fas això.

---

### Post by agent8131 on 2008-04-24
See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

### Post by lluisalguero on 2008-04-25
> **agent8131 said:**
> See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

Haig de pensar llavors que és un bug? El meu anglés no és precisament el de Oxford, i al menys això és el que m'aparegut entendre.

Tot i això, m'he baixat la iso del 8.04, i faré una instal·lació nova, aquesta, com que Ubuntu era nou per a mi, l'he putinejat "a muerte" i de tant en tant es penja i fa alguna que altra cosa rara.

Gràcies a tots pels vostres consells

Lluís

---

### Post by JAHlive on 2008-04-25
Primer, BONA TARDA :):) com mole aixó de tenir companys catalans 
:lolflag::lolflag:




be, jo acabo d'actualitzar a la versió estable de Ubuntu, però m'he passat de 32 a 64 ;) tot un nou món 

Tinc el mateix problema y no ser que fer, ja he seguit el manual per que puc editar gràcies al terminal Root, perÒ no des de el normal ;)

y tot i aixó no puc fer sudo ...


mercès 

p.d. sabeu quant estarà llest el diccionari en català pel firefox 3 :confused:

L's desde Andorra

---

### Post by JAHlive on 2008-04-25
Primer, BONA TARDA :):) com mole aixó de tenir companys catalans 
:lolflag::lolflag:




be, jo acabo d'actualitzar a la versió estable de Ubuntu, però m'he passat de 32 a 64 ;) tot un nou món 

Tinc el mateix problema y no ser que fer, ja he seguit el manual per que puc editar gràcies al terminal Root, perÒ no des de el normal ;)

y tot i aixó no puc fer sudo ...


mercès 

p.d. sabeu quant estarà llest el diccionari en català pel firefox 3 :confused:

L's des de Andorra

---

### Post by JAHlive on 2008-04-25
perdoneu el doble post :(

---

### Post by papapep on 2008-04-25
> **JAHlive said:**
> perdoneu el doble post :(

Perdonat i arreglat.

Benvingut al fòrum JAHlive :-) Passa't pel fil de benvinguda i explica'ns una mica la teva vida: [http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)

---

### Post by lluisalguero on 2008-04-25
Ja ho he solucionat, a veure si em sé explicar bé com ho he fet...

Anem a Sistema -> Administració -> Xarxa

i el que he fet després de desbloquer-ho, és anar a la pestanya "General" i esborrar el que tenia ficat a "Nom de domini". He acceptat i sense reiniciar tot m'ha funcionat correctament.

Ara haig de comprovar que la xarxa amb la resta de pc's funciona...

---


---
title: "[SOLVED] Connectar/compartir dos ordinadors amb Ubuntu"
date: 2007-12-08
forum: Catalan Team
---

### Post by Curial on 2007-12-08
Bona vesprada,

Voldria compartir arxius entre els dos ordinadors de casa i no tinc gens d'idea de com fer-ho.

Els tinc connectats a traves d'un enrutador zyxel (timofònica) per cable i per descomptat amb ubuntu. El cas és que he intentat configurar una carpeta de l'ordinador"B" per a compartir i li he instal·lat el paquet nfs. He entrat en l'ordinador "A" per lloc-xarxa i no hi veig la carpeta en qüestió, Només la xarxa de windows. (El PC "A" ja tenia instal·lat el paquet nfs).

El cas és que si l'ordinador "B" el deixo funcionar en Windows98 si que el veig.(la veritat es que faig un ús pràcticament nul de W98 des que faig servir l'ubuntu ;-) ).

És possible connectar dos ordinador a casa sense haver de remenar massa? 

Sens dubte, moltes gràcies com sempre!
Salut i força Ubuntu!

---

### Post by jodufi on 2007-12-10
Si que és possible, i de manera fàcil.

Es pot compartir fitxers de manera fàcil mitjançant una xarxa samba (SMB) o una xarxa NFS. El primer sistema és el més recomanable si hi ha algun ordinador amb Windows a la xarxa.

La primera manera també és la més fàcil, simplement has de compartir una carpeta amb SMB (el primer cop s'instal·laran els paquets necessaris). I després explorant la xarxa ja t'apareixeran les carpetes. Hi ha molta literatura sobre el tema a Internet (prova amb samba + ubuntu), per a opcions una mica més avançades mira aquí:

[http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba)

La segona opció és una mica més complicada i, pels meus coneixements, menys flexible, però he aconseguit unes velocitats molt superiors a les aconseguides amb Samba. Escriu nfs + ubuntu i trobaràs moltes explicacions de com utilitzar-ho.

Salut

---

### Post by CarlesOriol on 2007-12-13
Insta&#320;la ssh al servidor

i des d'un ordinador al nautilus esrcrius ssh://ipdelaltre

o ssh://nomusuari@ipdelaltre

Esta "xupat"

---

### Post by Curial on 2007-12-14
Gràcies jodufi, he probat d'instal.lar Samba a l'ordinador que no el tenia i he compartit la carpeta. A l'explorar la xarxa windows me l'ha trobat a la primera.
Així de fàcil creia que havia de ser amb NFS però no aconsegit res.

Es veu que estic creant anticosos, perquè només amb el nom de xarxa windows, ja era un xic reticent a probar-ho amb Samba. :-)

---

### Post by Curial on 2007-12-14
> **CarlesOriol said:**
> 

Esta "xupat"

Carles, gràcies però creu-me si et dic, que no et pots ni imaginar com sóc de maldestre.

---

### Post by papapep on 2007-12-14
Per instal·lar el servidor a l'ordinador al que vols accedir remotament:

```
sudo aptitude install openssh-server
```

A l'ordinador que vols utilitzar per accedir al que fa de servidor:

```
sudo aptitude install openssh-client
```

I un cop hagis fet això, fiques a la barra del Nautilus el que t'ha dit el Carles.

---

### Post by jodufi on 2007-12-15
A mi em passava el mateix Curial, em feia reticència instal·lar samba i primer utilitzava NFS, més ràpid però també el vaig trobar menys intuïtiu i fàcil de configurar. També he sentit a dir que el Samba és una implementació més eficient que el SMB original de microsoft. I crec que actualment Ubuntu està més preparat per a una xarxa Samba que qualsevol altra xarxa, almenys a nivell d'usuari que sense molts coneixements.

Tot i això, ja provaré el SSH que comenta el CarlesOriol i el papapep, a veure com va.

---

### Post by CarlesOriol on 2007-12-15
> **jodufi said:**
> Tot i això, ja provaré el SSH que comenta el CarlesOriol i el papapep, a veure com va.

Ja veuras que més fàcil impossible.

Ah... i tot i les grans habilitats teclejadores d'en papapep podem aconseguir el mateix fent:

Al client: Res! la instal·lació predeterminada d'ubuntu ja ho fa tot.

Al servidor: Insta&#320;lar el ssh. (assumeix el servidor). Això ho podem fer amb el synaptic exercitant sols el dit index de la ma dreta (o esquerra segons configuració ). O exercitant les dues mans escrivint: sudo apt-get install ssh.

A més ens permet:

(Des de terminal fem:)

ssh usuari@ipordinadorremot -X

Entrem en terminal en un altre ordinador i podem executar programes gràfics remotament. Una passada per ensenyar a qualsevol futur ex-usuari de windows.


Un cop proveu l'ssh us oblidareu del smb i el nfs (excepte es clar en els casos on son necessaris :-) )

---

### Post by papapep on 2007-12-15
> Ah... i tot i les grans habilitats teclejadores d'en papapep podem aconseguir el mateix fent:

Al client: Res! la instal·lació predeterminada d'ubuntu ja ho fa tot.


M'agrada assegurar la jugada, i he dit de instal·lar el client ssh per si "per casualitat" s'hagués desinstal·lat. Total, si ja està instal·lat no passa res de res :-)

---

### Post by CarlesOriol on 2007-12-16
Package: ssh
Status: install ok installed
Priority: extra
Section: net
Installed-Size: 32
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: openssh
Version: 1:4.6p1-5build1
**Depends: openssh-client, openssh-server**
Description: secure shell client and server (metapackage)
 This metapackage is a convenient way to install both the OpenSSH client
 and the OpenSSH server. It provides nothing in and of itself, so you
 may remove it if nothing depends on it.
Original-Maintainer: Debian OpenSSH Maintainers <debian-ssh@lists.debian.org>

---

### Post by papapep on 2007-12-16
Val, per un cop, i que no senti precedent, et donc la raó :-P

---

### Post by Curial on 2007-12-16
Bé crec que ara si que m'heu donat munició per preguntar!

N'explico els duptes:

1) Després d'instal·lar l'ssh als dos ordinadors des del G.Synàptic he posat tal com deia en Carles l'altre nom d'usuari+@+IP de l'altre. He suposat  que la IP era la que sortia a Sistema-Administració-Xarxa llengüeta d'ordinadors centrals(Àlies:nomd'usuari-desktop). Es veu que aquesta IP es la mateixa en els dos ordinadors. També he provat de canviar-la, res ha funcionat però.També he posat el nom d'usuari seguit de -desktop sense resultats.

2) Un cop introduït ssh://nomaltreusuari@ipdel'altre, em pregunta una contrasenya, i he provat amb la dels dos ordinadors.He pensat que si vols accedir a l'altre el més lògic era usar la contrasenya d'aquell.

3)Us dic perquè he triat el synaptic i no el terminal (és per comentar la curiositat):
Al fer-ho pel terminal m'ha donat:
"Els paquets no fiables podrien comprometre la seguretat del vostre sistema.
Únicament hauríeu de continuar la instal·lació si n'esteu completament segur.
openssh-server " i l'he aturat.
Des del G.synàptic en el mateix ordinador m'avisava que no estava autenticat (curiosament en el que tenia l'actualització al dia).Encara que la versió de l'ssh era la mateix que comentava en Carles,en tots dos ordinadors.

:confused:

---

### Post by Curial on 2007-12-16
> **CarlesOriol said:**
> 
Entrem en terminal en un altre ordinador i podem executar programes gràfics remotament. Una passada per ensenyar a qualsevol futur ex-usuari de windows.


No era la meva intenció al començar aquest fil preguntar per l'execució remota, però fa temps que n'estic bastant interessat.

> **CarlesOriol said:**
> 
Una passada per ensenyar a qualsevol futur ex-usuari de windows.


Si no sóc ja,a aquestes altures, ex-usuari de windows és perquè a la feina no tinc més remei que treballar amb aquell sistema.:(

---

### Post by lluisanunez on 2007-12-16
Si els ordinadors es connecten via DHCP, el router els assigna una IP en el rang 168.192.X.XXX
Per saber la IP que tenen assignada, pots clicar la icona del NetworkManager amb el botó contrari, i triar "Connection Information". En el meu cas, al menys, aquestes IPs són sempre les mateixes per a cada ordinador.
Alternativament, pots anar a Sistema > Administració > Xarxa i canviar el tipus de connexió, i en comptes de DHCP entrar-hi IPs fixes, dins el mateix rang, per a cada ordinador, sempre que també hi posis correctament les adreces del router, porta d'enllaç i DNS

---

### Post by Curial on 2007-12-16
> **lluisanunez said:**
> Si els ordinadors es connecten via DHCP, el router els assigna una IP en el rang 168.192.X.XXX
Per saber la IP que tenen assignada, pots clicar la icona del NetworkManager amb el botó contrari, i triar "Connection Information". En el meu cas, al menys, aquestes IPs són sempre les mateixes per a cada ordinador.
Alternativament, pots anar a Sistema > Administració > Xarxa i canviar el tipus de connexió, i en comptes de DHCP entrar-hi IPs fixes, dins el mateix rang, per a cada ordinador, sempre que també hi posis correctament les adreces del router, porta d'enllaç i DNS

No se a que et refereixes amb Networkmanager :KS. Dins d'administració tinc dues opcions de xarxa: eines xarxa i xarxa.
Pel que veig el rang DNS és 192.168.x.x. i pel que sembla el parametre IP em dona del rang 127.x.x.x, en aquest últim quan dins del Nautilus scric ssh://altreusuari@127.x.x.x sí que em fa la pregunta de la contrassenya, cosa que amb l'altre no fa.

Referent a la IP fixa, a mi m'apareix com a estàtica, en tot cas no és DHCP. Si desactivo el box "Habilita el mode itinerant" pataplaf: literalment liquido la connexió a internet.

Tinc problemes perquè tots els conceptes de DNS, IP, porta d'enllaç etc són desconeguts per a mí.

---

### Post by lluisanunez on 2007-12-16
Em refereixo a la icona que apareix a dalt a la dreta (dos ordinadors connectats)
Botó contrari al que fas servir normalment > Connection Information

---

### Post by papapep on 2007-12-16
No home!! El 127.0.0.1 és el localhost, no és la ip pública de l'ordinador.

Fes a un terminal (no, si sempre acabo igual jo...):

```
ifconfig
```

Fixa't, a mi em surt el següent:

```
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:C4:04:4D  
          **[COLOR="Red"]inet addr:192.168.1.34[/COLOR]**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fec4:44d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162522285 (154.9 MB)  TX bytes:29252849 (27.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1103601 (1.0 MB)  TX bytes:1103601 (1.0 MB)

```

L'interfície lo és la que tenen tots els ordinadors, és l'anomenat "loopback", i, en aquest cas, eth0 és la meva placa ethernet, amb la seva ip (en vermell) i demes cosetes...

Doncs tu has d'esbrinar la ip dels teus pc's, que és la que has de posar per a connectar de un a l'altre. Evidentment, si et connectes de l'ordinador A a l'ordinador B, has de posar la ip i contrassenya de B per a connectar-t'hi.

---

### Post by Curial on 2007-12-16
> **lluisanunez said:**
> Em refereixo a la icona que apareix a dalt a la dreta (dos ordinadors connectats)
Botó contrari al que fas servir normalment > Connection Information

Sí efectivament allà ho deia.Tinc tendència a mirar sempre a l'altre costat, al costat esquerre vull dir.  :)

Moltes gràcies

---

### Post by Curial on 2007-12-16
> **papapep said:**
> No home!! El 127.0.0.1 és el localhost, no és la ip pública de l'ordinador.

Fes a un terminal (no, si sempre acabo igual jo...):



De veritat t'agraeixo molt la paciència que teniu en algunes ocasions.
T'asseguro que en el meu cas no és feina perduda.

Salut.

---

### Post by ofim on 2011-01-30
Estava buscant com instal·lar el ssh en un ubuntu. El feia servir a l'insti per connectar-me amb el servidor debian. He arribat a aquest fil i encara flipo del que ha posat l'Oriol del Nautilus.
Simplement gràcies.
PD: soc ex-windows, que dieu vosaltres. M'he passat a Ubuntu i és gràcies a fils com aquest que no m'arrepenteixo.

---


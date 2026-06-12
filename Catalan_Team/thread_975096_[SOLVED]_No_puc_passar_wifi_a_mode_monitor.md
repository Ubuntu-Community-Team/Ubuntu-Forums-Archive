---
title: "[SOLVED] No puc passar wifi a mode monitor"
date: 2008-11-08
forum: Catalan Team
---

### Post by Dr.Rwh on 2008-11-08
Hola, tinc un problema. He instalat aircrack-ng i Aircrack-ptw . Però a l'hora de passar a mode monitor, no em deixa, em dona el seguent error.

```

root@SergiC:/home/sergi# iwconfig eth0 mode monitor
Error for wireless request "Set Mode" (8B06) :
SET failed on device eth0 ; No such device.

```

Ho provo desde root ja que si ho provo com usuari em diu que no tinc permisos. Abans de posar el post, he buscat per internet i he trobat que potser em falten els drivers per el chipset de la meva tarjeta. Però com soc novell a linux, dons abans de fer res m'agradaria preguntar ;)

El lspci em dona el seguent:

```

sergi@SergiC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
04:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
04:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
04:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)

```

No se quin es el meu chipset, he trobat aquesta web per internet que m'indica quin driver m'he d'instalar i com fer-ho depenent del model de la meva targeta.

[http://hwagm.elhacker.net/drivers-ng/driver-ng.htm](http://hwagm.elhacker.net/drivers-ng/driver-ng.htm)

Però com no se quin tinc :S

A veure si algu em pot donar un cop de mà , i si necesiteu quansevol altre informació només cal que m'ho demaneu :)

Gràcies de bestreta

Salut

---

### Post by oriolsbd on 2008-11-08
Hola, ara mateix no estic en Ubuntu, de manera que no ho puc confirmar, però em sembla que el dispositiu és "eth0", i no "et0".

---

### Post by Dr.Rwh on 2008-11-08
> **oriolsbd said:**
> Hola, ara mateix no estic en Ubuntu, de manera que no ho puc confirmar, però em sembla que el dispositiu és "eth0", i no "et0".

Em dona el mateix error ;)

---

### Post by PatrickVogeli on 2008-11-08
tens una intel intel 3945, que fa servir el driver iwl3945 i, casi segur, que es dira wlan0, no eth0

salut

---

### Post by Dr.Rwh on 2008-11-08
> **PatrickVogeli said:**
> tens una intel intel 3945, que fa servir el driver iwl3945 i, casi segur, que es dira wlan0, no eth0

salut

el wifi em funcina, pero el que em deixa es passar-lo a mode monitor :D

Si instalo el driver que m'indiques , el podré passar a mode monitor?

EDITAT:

He trobat una web que explica com fer-ho

[http://vive-libre.com/blog/2008/03/06/adutoria-de-seguridad-wireless-con-ipw3945-ubuntu-y-aircrack/](http://vive-libre.com/blog/2008/03/06/adutoria-de-seguridad-wireless-con-ipw3945-ubuntu-y-aircrack/)

, pero em dona error al fer :

sudo apt-get install - linux-ubuntu-modules-$(uname -r) linux-restricted-modules-$(uname -r) linux-image-debug-$(uname -r) linux-image-$(uname -r) linux-headers-$(uname -r)

El error diu:

sergi@SergiC:~$ sudo apt-get install - linux-ubuntu-modules-$(uname -r) linux-restricted-modules-$(uname -r) linux-image-debug-$(uname -r) linux-image-$(uname -r) linux-headers-$(uname -r)
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
E: No s'ha pogut trobar el paquet linux-ubuntu-modules-2.6.27-7-generic
sergi@SergiC:~$ 

A veure si amb aquesta info més algu em pot donar un cop de ma :)

---

### Post by papapep on 2008-11-08
[No hi ha cap paquet linux-ubuntu-modules després de la 2.6.24-21]("http://packages.ubuntu.com/search?keywords=linux-ubuntu-modules&searchon=names&suite=all&section=all")

---

### Post by Dr.Rwh on 2008-11-09
> **papapep said:**
> [No hi ha cap paquet linux-ubuntu-modules després de la 2.6.24-21]("http://packages.ubuntu.com/search?keywords=linux-ubuntu-modules&searchon=names&suite=all&section=all")

Porto moltes hores davant del ordinador, buscant per internet, i no aconsegueixo trobar el perque falla la instalació dels moduls de ipwraw.

si a la consola poso uname -r em diu que tinc la versió 2.6.27-7-generic.

Si no vaig mal encaminat, això vol dir que tinc instalada una versio de paquets (2.6.27-7-generic) que encara no te el paquet de moduls? o com va això? perque si el terminal poso uname -r i em diu que tinc la 2.6.27-7-generic. i desprès intenta instalar els moduls i no els troba, i tu comentes que no hi han...

Estic una micaaaaa perdut xD

Gràcies pel vostre temps ;)

---

### Post by Dr.Rwh on 2008-11-09
m'auto responc, perque tinc nous avensos, un blogaire m'ha dit que instali els paquets per separat. aixi que la linea aquesta:

```
$ sudo apt-get install - linux-ubuntu-modules-$(uname -r) linux-restricted-modules-$(uname -r) linux-image-debug-$(uname -r) linux-image-$(uname -r) linux-headers-$(uname -r)
```

La he instalat per separat, i tot perfecte menys un modul que no es deixa, aquest:

```
linux-image-debug-$(uname -r)
```

He buscat per internet sobre aquet modul, i nomes surten dos forums anglesos i no entenc res del que parlen :S

De totes maneres, em comenten que segueixi la instalacio, i al seguir, el pas seguent es :

```
modprobe -r ipw3945
modprobe ipwraw
```

pero al executarlo em diu:

```
sergi@SergiC:~/ipwraw-ng$ sudo depmod -ae
sergi@SergiC:~/ipwraw-ng$ sudo modprobe -r ipw3945
WARNING: /etc/modprobe.d/ipwraw line 1: ignoring bad line starting with ‘“blacklist’
FATAL: Module ipw3945 not found.
```

---

### Post by PatrickVogeli on 2008-11-09
modprobe -r iwl3945

---

### Post by Dr.Rwh on 2008-11-09
> **PatrickVogeli said:**
> modprobe -r iwl3945

Acabo de fer el que m'has dit i se m'ha desconectat del wifi, i no hi ha manera de tornar a habilitar-lo.

M'has posat :

```
modprobe -r iwl3945 
```

Això volia substituir el?

```
modprobe -r ipw3945
modprobe ipwraw
```

Si és així em podries dir quina és la comanda sencera per habilitarlo i deshabilitarlo, és a dir. El que en els manuals era:

```
modprobe -r ipw3945
modprobe ipwraw

modprobe -r ipwraw
modprobe ipw3945
```

Per carregar-lo i descarregarlo quin és?

t'agrairia una resposta ràpida ja que estic conectat amb fils , i el cable de red es molt curtet i estic asegut al terra... xD

Gràcies!

---

### Post by papapep on 2008-11-09
> Si no vaig mal encaminat, això vol dir que tinc instalada una versio de paquets (2.6.27-7-generic) que encara no te el paquet de moduls?

Clar. Tens instal·lat i funcionant un **nucli** que encara no té (pel que sigui) el corresponent paquet linux-ubuntu-modules. Per tant, no entenc d'on has tret el paquet linux-ubuntu-modules que dius que has instal·lat si als repositoris d'Ubuntu no hi és...?? Has fet servir algun repositori extern?

> La he instalat per separat, i tot perfecte menys un modul que no es deixa

El concepte de que un paquet "no es deixa" instal·lar, és "una miqueta" dispers....ens hauries d'enganxar la ordre i el resultat de la mateixa per intentar entendre què passa.

De la resta d'errors, ni flowers.

---

### Post by Dr.Rwh on 2008-11-09
> **papapep said:**
> Clar. Tens instal·lat i funcionant un **nucli** que encara no té (pel que sigui) el corresponent paquet linux-ubuntu-modules. Per tant, no entenc d'on has tret el paquet linux-ubuntu-modules que dius que has instal·lat si als repositoris d'Ubuntu no hi és...?? Has fet servir algun repositori extern?

Mira, l'he instalat a el terminal posant :

```
apt-get install linux-ubuntu-modules-$(uname -r)
```

En comptes de fer corre la linea :

```
$ sudo apt-get install - linux-ubuntu-modules-$(uname -r) linux-restricted-modules-$(uname -r) linux-image-debug-$(uname -r) linux-image-$(uname -r) linux-headers-$(uname -r)
```

Com em donava error, els he provat per separat, i m'ha deixat en tots excepte el que menciono abans, el linux-ubuntu-modules.

> **papapep said:**
> El concepte de que un paquet "no es deixa" instal·lar, és "una miqueta" dispers....ens hauries d'enganxar la ordre i el resultat de la mateixa per intentar entendre què passa.

De la resta d'errors, ni flowers.

Dons vull dir que al instalar-lo , per separat com he dit abans em deia que no existia linux-ubuntu-modules de la versió de nucli que tinc posada. Però això s'ha solucionat fent anar les comandes com root ;)


Ara el error que tinc es que no em funciona el wifi, com cito al post anterior :(

---

### Post by papapep on 2008-11-09
> Dons vull dir que al instalar-lo , per separat com he dit abans em deia que no existia linux-ubuntu-modules de la versió de nucli que tinc posada. Però això s'ha solucionat fent anar les comandes com root 

Sento insistir, però si el paquet no és als repositoris, ni com a root ni com a res t'ha de funcionar. És basicament impossible instal·lar una cosa que no existeix. Fes això, i veurem què tens:

```
sudo aptitude search linux-ubuntu-modules|grep ^i
```

---

### Post by PatrickVogeli on 2008-11-09
no es per res, pero veig que estas molt molt verd i t'estas posant en un follon considerable. A mi el modul ipwraw no em compila, encara que no faig servir el nucli d'ubuntu, sino un de propi.

Estas fent servir un tutorial que servia fa 2 o 3 versions (gutsy o feisty, no se), ja que a la hardy ja es fa servir el modul iwl3945, no el ipw3945.

Ara, passem endavant. Obviament no et funciona el wifi, modprobe -r iwl3945 descarrega el modul wifi, dit d'altra manera, desconnecta el driver. modprobe ipwraw carrega un altre modul (si el tens, l'has pogut compilar i instal·lar?), que es fa servir per injectar paquets (o el que s'hagi de fer per obtenir les contrasenyes d'una wifi WEP) i no se si serveix per a connectar-se normalment.

Per tornar a connectar normalment, sudo modprobe -r ipwraw i despres sudo modprobe iwl3945 per tornar a carregar el driver normal.

Això de petar wifi la gent es pensa que es molt facil, i el cert es que s'han de tenir certs coneixements i saber buscar-te una mica la vida. Agafar un tutorial y cortar y pegar tot el rato no es el mes indicat, i menys encara si el sistema operatiu no es la mateixa versió que al tutorial i/o si no despres saps desfer el que has fet fins ara a menys que el tutorial ho indiqui.

Trobo que primer hauries d'agafar una minima confiança fent servir el terminal, enterar-te de com funcionen algunes ordres basiques i coneixer una miqueta el sistema de paquets d'ubuntu/debian i els errors relacionats.

salut

---

### Post by Dr.Rwh on 2008-11-09
> **papapep said:**
> Sento insistir, però si el paquet no és als repositoris, ni com a root ni com a res t'ha de funcionar. És basicament impossible instal·lar una cosa que no existeix. Fes això, i veurem què tens:

```
sudo aptitude search linux-ubuntu-modules|grep ^i
```

Executo l'ordre que m'indiques i no diu res 

```
sergi@SergiC:~$ sudo aptitude search linux-ubuntu-modules|grep ^i
sergi@SergiC:~$ 

```

---

### Post by Dr.Rwh on 2008-11-09
> **PatrickVogeli said:**
> no es per res, pero veig que estas molt molt verd i t'estas posant en un follon considerable. A mi el modul ipwraw no em compila, encara que no faig servir el nucli d'ubuntu, sino un de propi.

Estas fent servir un tutorial que servia fa 2 o 3 versions (gutsy o feisty, no se), ja que a la hardy ja es fa servir el modul iwl3945, no el ipw3945.

Ara, passem endavant. Obviament no et funciona el wifi, modprobe -r iwl3945 descarrega el modul wifi, dit d'altra manera, desconnecta el driver. modprobe ipwraw carrega un altre modul (si el tens, l'has pogut compilar i instal·lar?), que es fa servir per injectar paquets (o el que s'hagi de fer per obtenir les contrasenyes d'una wifi WEP) i no se si serveix per a connectar-se normalment.

Per tornar a connectar normalment, sudo modprobe -r ipwraw i despres sudo modprobe iwl3945 per tornar a carregar el driver normal.

Això de petar wifi la gent es pensa que es molt facil, i el cert es que s'han de tenir certs coneixements i saber buscar-te una mica la vida. Agafar un tutorial y cortar y pegar tot el rato no es el mes indicat, i menys encara si el sistema operatiu no es la mateixa versió que al tutorial i/o si no despres saps desfer el que has fet fins ara a menys que el tutorial ho indiqui.

Trobo que primer hauries d'agafar una minima confiança fent servir el terminal, enterar-te de com funcionen algunes ordres basiques i coneixer una miqueta el sistema de paquets d'ubuntu/debian i els errors relacionats.

salut

Paraules molt savies, però deixa'm rectificarte una coseta, si estic provant de fer servir el aircrack-ng no és per petar el cifratge dels veins, sino per comprovar la meva seguretat en el cifratge, i si realment és tant fàcil accedir a una WIFI xifrada.
Amb el wifislax ja ho havia aconseguit, però volia provar si amb ubuntu, sense fer servir cap liveCD era possible dur-ho a terme.

Gràcies per la teva ajuda, i em sembla que deixaré de construir la casa per la teulada...

Gràcies sincerament :)

---

### Post by papapep on 2008-11-09
> Executo l'ordre que m'indiques i no diu res

Code:

sergi@SergiC:~$ sudo aptitude search linux-ubuntu-modules|grep ^i
sergi@SergiC:~$



Doncs el que t'he dit: no el tens instal·lat :)

---

### Post by Dr.Rwh on 2008-11-09
> **papapep said:**
> Doncs el que t'he dit: no el tens instal·lat :)

cert haha.

Ara el que faré sera deixar aquest tema, i esperar a veure si surt un tutorial per la 8.10.

M'agradaria deixar el wifi com abans , ja que ara no em troba cap xarxa sense fils.

He provat això que m'has dit però no funciona.

```
sudo modprobe -r ipwraw
sudo modprobe iwl3945
```

Em diu el seguent:
```
sergi@SergiC:~$ sudo modprobe -r ipwraw
WARNING: /etc/modprobe.d/ipwraw line 1: ignoring bad line starting with '“blacklist'
sergi@SergiC:~$ sudo modprobe iwl3945
WARNING: /etc/modprobe.d/ipwraw line 1: ignoring bad line starting with '“blacklist'
sergi@SergiC:~$ 


```

---

### Post by PatrickVogeli on 2008-11-09
hi ha algun problema amb la linia 1 de l'arxiu /etc/modprobe.d/ipwraw. Sento dir-te que no puc ajudar-te, ja que no se que s'ha de fer. Prova el següent:

afegir blacklist ipwraw a l'arxiu /etc/modules.d/blacklist i afegir la linia iwl3945 a /etc/modules

reinicia i a veure si ja va.

salut

---

### Post by Dr.Rwh on 2008-11-09
> **PatrickVogeli said:**
> hi ha algun problema amb la linia 1 de l'arxiu /etc/modprobe.d/ipwraw. Sento dir-te que no puc ajudar-te, ja que no se que s'ha de fer. Prova el següent:

afegir blacklist ipwraw a l'arxiu /etc/modules.d/blacklist i afegir la linia iwl3945 a /etc/modules

reinicia i a veure si ja va.

salut

A /etc no hi ha cap carpeta que es digui modules.d , hi ha un archiu el modules.Pero no és cap carpeta.

Repasant el que ha fet el pc al executar la comanda que m'has indicat en la pàgina anterior, m'ha fet identificar com a root. I el que ha fet ha sigut eliminar un archiu. Si torno a posar la comanda com a usuari, em diu això:

```
sergi@SergiC:~$ modprobe -r iwl3945
WARNING: /etc/modprobe.d/ipwraw line 1: ignoring bad line starting with '“blacklist'
FATAL: Error removing iwl3945 (/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Operation not permitted
sergi@SergiC:~$ 


```

Això vol dir que quan ho he fet abans, com a root. Ha aconseguit eliminar aquest arxiu, vaig bé?

---

### Post by papapep on 2008-11-09
> A /etc no hi ha cap carpeta que es digui modules.d , hi ha un archiu el modules.Pero no és cap carpeta.

En Patrick no t'ha dit pas que ho sigui una carpeta:

> afegir blacklist ipwraw a l'arxiu /etc/modules.d/blacklist i afegir la linia iwl3945 a /etc/modules


ho has interpretat tu... :-)
Com això altre:

> Això vol dir que quan ho he fet abans, com a root. Ha aconseguit eliminar aquest arxiu, vaig bé?


Quan fas un "modprobe -r el_que_sigui", el que fas és intentar descarregar un mòdul (controlador pels noobies) del nucli.

---

### Post by Dr.Rwh on 2008-11-09
Gràcies a tots per respondre, la solució la he trobat per internet, el archiu ipwraw, al obrirlo deia : "ipwraw blacklist" , li he tret les cometes. i ja està, reiniciar el ordinador i ja funciona perfectament.

Durant molt de temps no donaré més la tabarra ;)

Gracies

---


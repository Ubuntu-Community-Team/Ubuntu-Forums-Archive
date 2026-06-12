---
title: "[SOLVED] No detecta Wi-fi"
date: 2008-11-01
forum: Catalan Team
---

### Post by Dr.Rwh on 2008-11-01
Hola a tots i a totes, és el meu primer missatge, espero apendre aquí.

Als 10 minuts de tenir instal.lat ubuntu 8.10 al meu portatil, em sorgeix el primer problema. No he trobat solució a internet, i he pensat que potser algun expert em podria donar un cop de mà.

El wi-fi està activat, i em detecta moltes xarxes sense fils, però la meva no la detecta. A casa hi ha un altre portatil i el ordinador de torre. El portatil funciona amb Vista i el meu amb Ubuntu, i a mi no em reconeix la meva xarxa, en canvi desde windows si que la troba. 

Actualment funciono amb el cable de red local, però no es gaire comode, ja que necesito que arribi a la meva habitació i ara estic engegat al costat del estudi...

He provat de conectar amb allò que diu de conecta a una xarxa sense fils oculta, però tampoc la troba, i poso bé el identificador.

Gràcies de bestreta :D

EDITAT : SOLVENTAT

---

### Post by Dr.Rwh on 2008-11-02
Entenc perfectament que els nous usuaris maten a preguntes i tal, però agrairia, encara que fos un enllaç per veure com arreglar-ho :(

Gràcies de totes formes :)

---

### Post by jaume69 on 2008-11-02
Pots mirar quin Kernel tens instal.lat.

Em sembla que amb el Kernel vell(**2.6.24**)funciona bé,en canvi amb el (**2.6.27**).,no!,amb Intrepid.

També es pot mirar el **ndiswrapper** a veure com va,treien el **Networkmanager**,però jo no ho he provat.

Llàstima que amb el nou Kernel de Intrepid no funcioni Networkmanager.

En el meu cas.

---

### Post by CarlesOriol on 2008-11-02
Aquest fil és perillosissim...

La pregunta ja és buida de contingut de per si, però la resposta és brutal.
El fet que insisteixis sense aportar res de nou, no serveix absolutament de res. 

Dr. T'aconsello llegir [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965) per tal de reformular-la. 
Cal que ens donis pistes, sense pistes, sense informació les respostes que trobaras son poc concretes ( o psicotropiques com la que ja t'han fet ).

Comença identificant-nos quin ordinador tens, quina placa de xarxa... (com a mínim has especificat la versió del sistema que ja es molt)

(pots fer un lspci al terminal i enviar-nos la resposta)

jaume69: Al meu ordinador no va la webcam, llàstima que en linux no funcioni cap webcam. (ho pilles?)

edito: jaume69. Gràcies a tu acabo de descobrir que la webcam del meu ordinador funciona a l'intrèpid... que guai!! :-)

---

### Post by Dr.Rwh on 2008-11-02
> **jaume69 said:**
> Pots mirar quin Kernel tens instal.lat.

Em sembla que amb el Kernel vell(**2.6.24**)funciona bé,en canvi amb el (**2.6.27**).,no!.

També es pot mirar el **ndiswrapper** a veure com va,treien el **Networkmanager**,però jo no ho he provat.

Llàstima que amb el nou Kernel no funcioni..

Jaume gràcies per respondre, però no em serveix gaire :p

Ara especifico les dades tècniques del meu pc a veure si amb més informació :)

Ubuntu 8.10 (intrepid )
Nucli Linux 2.6.27-7-generic
Gnome 2.24.1

Memòria : 2.0 GiB
Processador 0 : Genuine intel (r) CPU  T2250 @ 1.73 GHz
Processador 1 : Genuine intel (r) CPU  T2250 @ 1.73 GHz


Salut i gràcies

---

### Post by CarlesOriol on 2008-11-02
posa el resultat de lspci ... per veure quina targeta de xarxa tens.

---

### Post by Dr.Rwh on 2008-11-02
> **CarlesOriol said:**
> posa el resultat de lspci ... per veure quina targeta de xarxa tens.


```

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

gràcies :)

---

### Post by jaume69 on 2008-11-02
psicotropiques?,que vol dir?,deu ser algo de la psique,això si que ho sé.

> jaume69: Al meu ordinador no va la webcam, llàstima que en linux no funcioni cap webcam. (ho pilles?)

I t´ho segueixo afirmant,a part de si funciona o no,la qualitat d´imatge de la webcam és llastimosa,tan Ekiga,com l´altre que no recordo.

> [edito: jaume69. Gràcies a tu acabo de descobrir que la webcam del meu ordinador funciona a l'intrèpid... que guai!! 


Millor per tu,me´n alegro.

(Ni linux es tan bó,ni windows tan dolent)

---

### Post by CarlesOriol on 2008-11-02
Ok tens una:

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

En tinc dos d'aquestes funcionant gairebé perfectament:
Una en un acer aspire 5210 (o 5212).
D'entrada t'ha de funcionar sense cap tipus de problema. L'unica problema que em trovat és un error en el botó que activa i desactiva la targeta. En el seu cas quan apaga l'oirdinador i el desconnecta de la corrent aquest al reiniciar-se s'engega amb el wifi desconnectat.

L'altra també en un aspire un 5270 també amb incidencies similars al botó fisic de l'ordinador.

Pots fer alguna prova si la teva màquina té cap d'aquest butons. (un cop apretat triga una estona en trobar xarxa).


Si identifiques la marca i model de l'ordinador igual algú més et pot ajudar.

---

### Post by Dr.Rwh on 2008-11-03
> **CarlesOriol said:**
> Ok tens una:

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

En tinc dos d'aquestes funcionant gairebé perfectament:
Una en un acer aspire 5210 (o 5212).
D'entrada t'ha de funcionar sense cap tipus de problema. L'unica problema que em trovat és un error en el botó que activa i desactiva la targeta. En el seu cas quan apaga l'oirdinador i el desconnecta de la corrent aquest al reiniciar-se s'engega amb el wifi desconnectat.

L'altra també en un aspire un 5270 també amb incidencies similars al botó fisic de l'ordinador.

Pots fer alguna prova si la teva màquina té cap d'aquest butons. (un cop apretat triga una estona en trobar xarxa).


Si identifiques la marca i model de l'ordinador igual algú més et pot ajudar.

Gràcies per la resposta però no té el boto físic. De fet reb totes les conexions inalambriques menys la meva, de fet ni ha una sense xifrar, i és amb la que em conecto.

El model és un Asus z92j

Genuine Intel(R) CPU           T2250  @ 1.73GHz
798.000 MHz

---

### Post by sianeu on 2008-11-03
Tens un problema de comunicació entre el router i la tarja de red.

Has provat si funciona amb algun altre sistema operatiu?. Si el problema es de hardware potser hauràs de canviar el router. 
Si el problema només es amb Ubuntu jo provaria dues coses: 

Primer treu tota la seguretat del router, deixa la xarxa totalment oberta. 

Si no funciona, prova a canviar el gestor de xarxes. Per exemple amb WiCD (et deixo un petit manual de com fer-ho que vaig trobar a la xarxa).

Salut

edito: evidentment treure la seguretat només per provar. Si funciona cal tornar a crear-la poc a poc per detectar el problema.

---

### Post by Dr.Rwh on 2008-11-03
> **sianeu said:**
> Tens un problema de comunicació entre el router i la tarja de red.

Has provat si funciona amb algun altre sistema operatiu?. Si el problema es de hardware potser hauràs de canviar el router. 
Si el problema només es amb Ubuntu jo provaria dues coses: 

Primer treu tota la seguretat del router, deixa la xarxa totalment oberta. 

Si no funciona, prova a canviar el gestor de xarxes. Per exemple amb WiCD (et deixo un petit manual de com fer-ho que vaig trobar a la xarxa).

Salut

edito: evidentment treure la seguretat només per provar. Si funciona cal tornar a crear-la poc a poc per detectar el problema.

Gràcies per respondre, el problema només és amb ubuntu.

Ara provaréel WiCD a veure :)

---

### Post by papapep on 2008-11-03
Em fa l'efecte que tenim un problema de comunicació entre nosaltres...:-)

Dr.Rwh, quan dius: "No detecta Wi-fi", vols dir que realment el teu dispositiu inalàmbric no veu la SSID de la xarxa a la que vols connectar, o que la veus però no ets capaç de connectar-t'hi per alguna qüestió que encara no hem esbrinat?

---

### Post by Dr.Rwh on 2008-11-03
> **papapep said:**
> Em fa l'efecte que tenim un problema de comunicació entre nosaltres...:-)

Dr.Rwh, quan dius: "No detecta Wi-fi", vols dir que realment el teu dispositiu inalàmbric no veu la SSID de la xarxa a la que vols connectar, o que la veus però no ets capaç de connectar-t'hi per alguna qüestió que encara no hem esbrinat?


El wi-fi detecta moltes reds inalambriques però no detecta la meva. Inclus si provo de conectar-me a una xarxa sense fils oculta , tampoc la detecta.

EDITAT: amb el WiCD tampoc detecta la meva xarxa.

---

### Post by sianeu on 2008-11-03
No dius si has provat sense protecció de red. Pot ser que tinguis la SSID de la teva xarxa en estat de "oculta" o que tinguis un filtre de mac... No se si has configurat tu el teu router o està de fàbrica o t'ho ha fet un amic. 
Es estrany que puguis conectar a la xarxa de un veí que la te desprotegida però que no puguis conectar-te a la teva. Prova a desprotegir la teva a veure que passa. Si encara no la veus potser algú podrà aconsellar-te un altre software de red per provar.......

Salut

---

### Post by catximba on 2008-11-03
jo no sé fer això del WiCD, per tant, passe a tàctiques com buscar al Synaptic tot lo del Network Manager que em puga servir.

el que em diu és que "no s'ha trobat una eina de configuració de la xarxa", que vol dir: no pots configurar aquest driver amb el ndiswrapper.

potser és que no l'han adaptat encara al nou Intrepid, oi? de moment estic funcionant amb xarxes que no són la meua perquè la meua només la detecta l'aparell que no va, i ho vull solucionar...

---

### Post by PatrickVogeli on 2008-11-03
catximba, obre un nou fil per al teu problema, gracies

---

### Post by antoni2 on 2008-11-03
sembla que el problema esta al ruter. Treu el xifrat, mira per quin canal emeteix el ruter, o fins i tot truca al servei al client del provehidor (telefonica). Per ultim, jo probaria amb algun altre ruter (potser algu ten pot deixar un).

---

### Post by Dr.Rwh on 2008-11-03
> **antoni2 said:**
> sembla que el problema esta al ruter. Treu el xifrat, mira per quin canal emeteix el ruter, o fins i tot truca al servei al client del provehidor (telefonica). Per ultim, jo probaria amb algun altre ruter (potser algu ten pot deixar un).

Gràcies a tots per respondre, ara no paro per casa, demà us comento a veure que tal :)

---

### Post by open-pitu on 2008-11-03
Bones! T'adjunto la meva resposta d'un altre fil. Crec que seria bo que ho provessis manualment des de el terminal, aquí et deixo les indicacions. Ja diràs si et funciona!

> Anem a provar manualment si funciona el wifi del teu ordinador.

Primer de tot averiguarem l'interfície de la teva targeta

[INDENT]$iwconfig[/INDENT]

Aquí podem detectar quina és (normalment eth1, ra0...)

Si aquí ja no detecta quina interfície de wifi és malament rai... Però ho seguirem intentant.

Suposem que has detectat que la teva interfície és eth1, passem a buscar quines xarxes detecta la teva màquina:

[INDENT]sudo iwlist eth1 scan[/INDENT]

Ara ja només queda connectar-se a la nostra xarxa

[INDENT]sudo ifconfig eth1 up[/INDENT]
[INDENT]sudo iwconfig eth1 essid NomDeLaNostraESSID[/INDENT]
[INDENT]sudo iwconfig eth1 key s:LaContrassenyaDeLaXarxa[/INDENT]
[INDENT]sudo dhclient eth1[/INDENT]

En principi ara hauríes d'estar connectat. Prova si funciona la connexió amb el teu navegador. Si és així crea un fitxer executable amb les comandes que acabes d'executar.

   [INDENT] $sudo gedit /bin/connecta.sh[/INDENT]

Insertes les comandes que acabes d'executar. I Executes:

    [INDENT]$sudo chmod +x /bin/connecta.sh[/INDENT]

Ara des de el terminal quan obris l'ordinador executes connecta.sh i ja et connectaràs a la teva xarxa sense fil.

Si mires coses de shells scripts pots aconseguir que el connecta sigui un miniprograma. Si necessita ajuda digam-ho.

---

### Post by Dr.Rwh on 2008-11-04
Molt bones a tots i a totes.

Ja he solucionat el problema, a continuació exposaré com ho he pogut solventar per així si algu té el mateix problema solucionar-ho.

Vaig reinstalar el router wi-fi, i configurarlo de nou un altre cop, aquest cop treient la seguretat. Encenc el portatil i tampoc la reb.
Vaig provar de configurar la xarxa sense fils del router varies vegades, i a la 3a vaig pensar en canviar el canal per on enviava i rebia, tenia posat el 12. La sorpresa va ser quan vaig passar-lo al 2 i automaticament ubuntu la va rebre, i ja conectà.
Per tant el problema era que ubuntu no llegia fins la red 12, per tant no trobaba la meva xarxa, al canviar la configuració a la red 2, ja funciona.

Gràcies a tots per la ajuda ):P

---

### Post by SiscoGarcia on 2008-11-04
> **Dr.Rwh said:**
> ...
Ja he solucionat el problema, a continuació exposaré com ho he pogut solventar per així si algu té el mateix problema solucionar-ho.
...

Doncs ara només cal que marquis el fil com a resolt.

---


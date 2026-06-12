---
title: "ID baixa a l'aMule, ports i connexió sense fils a ONO"
date: 2008-09-02
forum: Catalan Team
---

### Post by lo gambusí on 2008-09-02
Hola, gent!

Fa quatre dies vam instal·lar connexió a Internet al pis on m'estic durant lo curs acadèmic i vam contractar ONO, telèfon + internet.

No he tingut cap problema amb la connexió a Internet: m'ha reconegut la connexió des del principi, va a una bona velocitat, etc.

A l'hora de posar l'aMule, però, he tingut alguns problemes. Tot i que no ho havia fet mai, m'he informat sobre tot el tema dels ports, seguint els passos d'ADSL Zone (concretament, [d'esta]("http://www.adslzone.net/tutorial-69.2.html") guia) i els he obert, o això pensava.

Quan he anat a connectar l'aMule, però, m'he trobat amb [este]("http://img225.imageshack.us/img225/4529/capturaio2.png") missatge.

Teniu idea què puc haver fet malament? No estic segur de que sigue un problema de l'Ubuntu, però porto ja molta estona buscant per la xarxa i no he trobat cap solució. He llegit [aquí]("http://www.adslzone.net/tutorial-69.4.html") que potser assignant una IP fixa se m'arregle, però no m'he aclarit gaire amb la guia (està feta per a windows).

Gràcies :)

---

### Post by jaume69 on 2008-09-02
Em sembla que has posat els ports **TCP,UDP** de la pàg.de configuració de AdslZone,i no els del teu **Amule**.

(Tot i que,si no és per baixar Pel·lícules o Programassos,per baixar coses senzilles,a mi ja em va bé la ID.Baixa.:))

---

### Post by lo gambusí on 2008-09-03
Sí, jo he posat els ports 85 i 1985, com em deia allí. Hauria d'haver posat uns altres?:confused:

---

### Post by papapep on 2008-09-03
[Mini-segresto el fil durant uns segons]

Jaume69!!! Estem esperant la teva proposta de tema pel mes de setembre!! Ens tens abandonats!!!! :-)

[Ja està, l'allibero]

Per cert, Gambusí, mira a l'apartat de ports de l'Amule. Han de lligar els ports que has obert, siguin els que siguin, amb els que et surt allà. És igual que modifiquis els de l'Amule que els del router/mòdem, però han de ser coherents.
També estaria bé, com tu ja dius, que tinguessis una ip fixa al pc, sinó, no entenc al obrir els ports a quin ordinador (per la IP) li has dit que ha de redirigir el trànsit als ports que has obert.

---

### Post by torracastanyes on 2008-09-03
Els ports que has obert son per a Windows, pero en Linux (si no recordo mal) no es poden emprar ports per sota de 1024.
 També aconsellen els més alts, entre 50000 i 65000.

Sobre la IP fixa, hi ha routers que assignen sempre la mateixa IP segons l'adreça MAC, pero n'hi ha que no. Com que entenc que a aquesta xarxa us conecteu varia gent, comprova la IP quant el conectis, i si canvía, fixa-la.

Trobaràs més imformació aquí:

[http://forum.amule.org/index.php?PHPSESSID=eac2e30cf7c05e954aa4fc7690cb14ff](http://forum.amule.org/index.php?PHPSESSID=eac2e30cf7c05e954aa4fc7690cb14ff)

---

### Post by jaume69 on 2008-09-03
Jo el que faig,he fet,fa uns moments és:

-Obro el Router en el navegador amb la meva IP Predeterminada,no la pública.
(clik dret ratolí a l'icona Wifi,clika Irformació de la Conexió,a Ubuntu)

-Quan sóc a dins,vaig a Avanced Setup,**NAT**(el teu cas sembla que és, **portforwarding**),i aquí ja puc afegir o treure els ports del Amule,TCP;UDP,que m'indica el mateix Amule,Emule,etc.)

No crec que hi hagi gaire diferencies entre Routers en aquest tipus de configuració.


La **IP stàtica** fixa em sembla és més recomanable si tens una web o domini propi,personal,empresarial,negoci,etc.
(Que no és que sigui gaire barata,que diem....!!!)

Apal.li.:)

---

### Post by papapep on 2008-09-03
La ip fixa de la que estem parlant és la de la lan interna, Jaume, no de la ip pública.

---

### Post by tanreb20 on 2008-09-03
Ei gamba!XD

Prova a obrir apart els ports del Amule que et diu el TCP +3 és a dir: si has obert el tcp 4662 obre també el 4665 entens?

Al ubunut-es he trobat multitud de pmanuals i no em recordo de quin pero em va funcionar i ara va bastant bé..

L'unic es que et surtira casi sempre lu d Kad: tallafocs pero no voldra dir res... ya uas!


apa animus q tu pots!

apt-get install llibertat amnistia i estatut d'autonomia!

---

### Post by lo gambusí on 2008-09-06
Bé, he provat los ports que m'ha dit el tanreb i m'ha funcionat, però al no tenir IP fixa no em serveix de gaire.

Respecte la IP fixa, he trobat això al fòrum de ubuntu en castellà:>  edita el archivo /etc/network/interfaces según tus necesidades, básicamente bastaría con cambiar/añadir estas líneas:

iface "interfaz" inet static
address "direccion_ip"
netmask "mascara"

evidentemente tendrás que usar los parámetros que correspondan en tu caso en vez de "interfaz" etc. Tras eso desactiva la interfaz mediante ifdown "interfaz" y después vuelve a levantarla mediante ifup "interfaz"

Para más información puedes dirigirte a las páginas del manual mediante man interfaces; se pueden hacer cosas muy "curiosas" mediante ese archivo.

Eso sí, si solo quieres cambierlo durante un momento, puedes usar ifconfig "interfaz" "direccion_ip"

Ho he provat, i al fer el sudo gedit em surt això> auto lo
iface lo inet loopback

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

Què hauria de canviar?

---

### Post by lo gambusí on 2008-09-07
Ho pujo, perquè al editar-ho no apareix a dalt de tot:)

---

### Post by papapep on 2008-09-07
....no et funciona el network-manager per posar la ip estàtica? t'estalviaràs  mals de cap.

---

### Post by lo gambusí on 2008-09-07
Suposo que et refereixes a Sistema/Administració/Xarxa, no?

Un cop dins, ho deixo així:

[IMG]http://img167.imageshack.us/img167/3227/capturajd4.png[/IMG]

 i li dóno a D'acord, però després no em connecta a la xarxa. Em deixo alguna cosa, potser? L'adreça de passarel·la com puc saber-la?

---

### Post by tanreb20 on 2008-09-07
La pasarela és 192.168.0.1 en el teu cas, es el més probable.


JO intento fer el mateix que diu ell d epsoar la Ip esatica pero no em funciona. un cop he posat les dades la icona del network-manager canvia com si estigues amb cable conectat pero no dona resposta nia pings ni a [www..](www..).

---

### Post by lo gambusí on 2008-09-07
Sí, exacte, me fa lo mateix que tu, tanreb :(

---

### Post by torracastanyes on 2008-09-07
Jo no ho he fet mai, però em penso que per fixar la IP, primer l'hi has de dir al router quina IP vols que t'assigni. Per això has d'entrar a la comfiguració del router.

---

### Post by papapep on 2008-09-07
Estem barrejant conceptes. Una cosa és dir-li al router que sempre t'assigni la mateixa ip de manera _dinàmica_, que és el que dius tu, torrecastanyes. L'altra és assignar-li al pc una ip fixa _estàtica_ passant de routers, dhcp's i altres galindaines.

Si estem parlant de wifi jo no controlo gaire, i menys amb el network-manager que a mi em va fer perdre moltes hores de son fins que el vaig enviar a pastar fang i vaig instal·lar el wicd. Des d'aleshores sóc un home realitzat :-)

L'adreça de passarela, Gambusí, és la mateixa que fas servir per connectar-te al router per configurar-lo. Si no la tens posada és impossible que el pc sàpiga on enviar els paquets quan vols connectar-te a internet, m'explico?

---

### Post by lo gambusí on 2008-09-08
Ostres Papapep, entenc que el wicd et canviés la vida... és brutal!:)

En menys de 10 segons m'ha configurat la connexió. Ara en principi [hauria d'estar funcionant amb IP fixa]("http://img388.imageshack.us/img388/8436/capturakw2.png"), però no tinc clar que ho face. De fet el port UDP em segueix canviant cada cop que obro l'aMule, i em segueix apareixent el missatge de *Kad: Firewalled*. Què n'opineu?

---

### Post by papapep on 2008-09-08
Que pots passar olímpicament del port udp. L'important, en aquest cas concret, no sempre és aixi, és el tcp. :-)

---

### Post by Diegstroyer on 2008-09-09
Indististintament dels ports que obris i encara que tinguis ID Alta, amb ONO ja et pots oblidar de descarregar amb l'aMule,ja que ONO capa les conexions als servidors edk,només pots utilitzar de forma efectiva les descàrregues amb torrents, ja que el protocol està completament ofuscat (xifrat).

Per obrir els ports (encara que no et servirà de res) has d'anar  i mirar en la configuració de l'aMule quins ports tens com a TCP i UDP, anar al router, entrar-hi i dir que t'assigni una IP fixe i obrir els ports al router en aquesta IP.

Molta sort... 

PD: ONO nega en tot moment que capi les connexions, pero cerca informació amb el Google sobre ONO i eMule.

---

### Post by Daerun on 2008-09-09
> **Diegstroyer said:**
> Indististintament dels ports que obris i encara que tinguis ID Alta, amb ONO ja et pots oblidar de descarregar amb l'aMule,ja que ONO capa les conexions als servidors edk,només pots utilitzar de forma efectiva les descàrregues amb torrents, ja que el protocol està completament ofuscat (xifrat).

Si això que dius es així potser el que convindria es fer servir _e_mule via wine, ja que l'emule fa servir protocol ofuscat, i a part está el KAD, que no fa servir servidors...

---

### Post by patrickfromspain on 2008-09-09
l'amule ja te ofuscacio de protocol, al menys a les preferencies hi surt

---


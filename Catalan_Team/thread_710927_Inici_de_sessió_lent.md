---
title: "Inici de sessió lent"
date: 2008-02-29
forum: Catalan Team
---

### Post by Frealof on 2008-02-29
Hola a tothom!

Fa un temps que veig que després d'entrar el nom d'usuari i la contrasenya a la pantalleta d'inici d'Ubuntu, triga bastanta estona a iniciar-se l'entron gràfic (faig servir gnome). 

La màquina es un: AMD Athlon XP 2000+; 1011'4 MB de Ram; GeForce 7300 GT de 512 Mb de ram... No crec que amb això hagi d'anar més lent que quan tenia 256 de Ram i una GeForce MX440...

Alguna idea? Gràcies per endavant ;)

---

### Post by Rubunter on 2008-02-29
A mi em passa exactament el mateix, pero en el meu cas jo tinc 2GB de RAM. Crec recordar que em va lent des que vaig instal·lar l avant windows navigator. A mi em triga uns 30 segons en iniciar-se. Suposo q aixo depen de la quantitat de programes que arrenquis a l'inici.

---

### Post by Frealof on 2008-02-29
Ei, bones!

La qüestió es que de programes que es carreguin a l'inici, que jo sàpiga no n'hi tinc... Com ho podria saber?

Pel què fa al disc dur, esta pràcticament buit, només hi tinc un parell de jocs (Wolfenstein Enemy Territory i RegnumOnline) que abans no em donaven cap mena de mal de cap i ara no puc jugar a cap :( (però això ja es una altra història que ja plantejo a la gent d'NGD i a algun dels fòrums de l'E.T. , joc, no el de l'Spilberg ;))

Bé, esperem que algú que en sàpiga una mica més ens il·lumini :) 

Gràcies de totes maneres.

---

### Post by menut on 2008-02-29
Per saber els programes d'inici que teniu al vostre Ubuntu, aneu a:

[INDENT]Sistema > Preferències > Sessions[/INDENT]

La primera pestanya conté una llista amb ALGUNES de les aplicacions que es carreguen a l'inici, i podeu desactivar-les, eliminar-les o afegir-ne de noves.

---

### Post by CarlesOriol on 2008-02-29
Analitza l'inici amb el bootchart.

primer insta&#320;les el software

**sudo apt-get install bootchart**

i despres mira a la carpeta** /var/log/bootchart **on tindras una gràfica de la inicialització.

Vigila que crea un arxiu a cada inici... així que ho vas esborrant o despres desinsta&#320;les el programa.

---

### Post by Frealof on 2008-02-29
Ei, bones!

Interessant... Li farem un cop d'ull a tot això. ;)

Si hi hagués canvis tan en positiu com en negatiu ja us ho faria saber. Moltes gràcies.

Salut!

---

### Post by rroca1 on 2008-02-29
I ara, què n'he de fer del gràfic?

---

### Post by Frealof on 2008-02-29
Iep!

Ja torno a ser aquí, i amb notícies...

Primer he anat a fer un cop d'ull al què deia en Menut, i he tret d'allà un parell de coses que no faig servir, Evolution alarm notifier i una mini-aplicació de la cua d'impressió (no hi tinc cap mena d'impressora connectada per tant... fora). Teòricament hauria d'anar més ràpid, no?

Instal·lo el Bootchart i cap problema... surto de la sessió i tot correcte. Re-inicio, entro Usuari i Contrasenya... i se'm queda en la pantalla de transició entre Login i l'Escriptori del Gnome... He esperat... he continuat esperant... i al cap de uns minutets d'esperar, he pitjat el botonet de re-inici de la torre (lleig, però es que quan no va ni el teclat...).

Després del re-inici tot ha anat bé, tenint en compte que no ha millorat el temps d'arrencada... tot i així us adjunto el parell de gràfiques que el bootchart m'ha fet, a veure si hi podeu veure alguna cosa que jo, per inexperiència, no hi veig.

Salut!

---

### Post by CarlesOriol on 2008-03-01
Sembla que tens algun controlador del sistema que no funciona correctament. El temps de càrrega del modprobe és molt gran.

---

### Post by Frealof on 2008-03-01
Bones!

El què deia, ni idea ;)

Ara fa una estona i després de tenir apagat el PC tota la nit, m'he mirat el gràfic del bootchart i, sincerament, no ho entenc... el temps de càrrega del modprobe que en l'anterior era "llarg" en aquesta ocasió es molt més curt... el més curiós es que no he fet res per millorar això... alguna idea per fer algun tipus de diagnòstic per saber exactament què falla?

---

### Post by Frealof on 2008-03-02
Bones de nou a tothom!

Ahir em vaig adonar que quan engegava el PC no em carregava els IDE esclaus que tinc, cosa que em va estranyar una mica... Vaig obrir la caixa, i vaig veure que estava mal connectat, en fi, vaig reconnectar-ho TOT de nou i sembla que la cosa ha millorat :).

Us passo la gràfica del bootchart d'avui. Crec que la cosa ha millorat considerablement...

A part d'això... hi ha alguna manera per poder comprovar què falla exactament? Hi ha alguna aplicació o comanda per el terminal?

Gràcies de nou!

---

### Post by papapep on 2008-03-02
I ara quant temps triga a engegar-se completament?

---

### Post by Frealof on 2008-03-03
Ei bones!

Gràcies per fer-hi un cop d'ull :) i disculpeu el retard a contestar...

El temps de càrrega des que pitjo el botó d'encesa del PC fins la finestra de Log in va de uns 52 a 57 segons (ho he provat unes quantes vegades). 

El temps de càrrega de l'escriptòri va de 30 a 45 segons, això quan el carrega, hi ha hagut alguna vegada que al cap de 10 minutets d'esperar a què es carregués he pitjat el botonet de reinici... :(  Lleig, però es que no sabia què fer, només funcionava el ratolí...

Gràcies altre cop per l'ajuda.

---

### Post by Frealof on 2008-03-04
Hola de nou! :)

Avui m'he trobat que al iniciar el gnome m'ha sortit una finestra que em deia que hi havia hagut un error al carregar el gnome daemon... que pel què sembla es dedica a gestionar els temes d'escriptori.

He buscat una estona per la xarxa i he trobat una manera per restablir els temes, barres, etc. 

Creieu que el problema que l'escriptori es carregui més lentament pot ser causat d'aquest "daemon"?

Salut!

---

### Post by Miquel Ubuntero on 2008-03-04
Ep! Això m'interessa.
A mi també m'ha donat el mateix error del "gnome daemon" un parell de cops.
En una ocasió ni tan sols he pogut entrar a l'escriptori. Però a diferència de algú altre que reinica el pc a "cascaporro" amb el botó reset, jo faig "Ctrl-Alt-Del" i torno a estar a la finestra d'entrada on puc triar usuari.
Només hem passa a mi. Als altres 2 usuaris del pc no. Sembla que el meu usuari te algún problema.
Algú  sap que fer?
No se si esborrar el meu usuari i crear-lo de nou??? :confused:

---

### Post by patrickfromspain on 2008-03-04
si us diu lo del gnome-settings-daemon es facil de solucionar: alt+f2 i executeu gnome-settings-daemon

salut!

---

### Post by Frealof on 2008-03-05
Iep!

Si. Aquesta solució que proposes patrickfromspain, ja es la que havia trobat... Gràcies de totes maneres ;) 

Però el què em pregunto es si aquest daemon pot ser la causa que l'escriptori se m'executi tan a poc a poc, ja que m'ha sortit en diverses ocasions (molt poques, tot sigui dit) i al haber ja trobat una solució... ja no em preocupava massa.

I pel què fa a reiniciar a "cascaporro" (bona l'expressió :)) com deia Miquel Ubuntero... quan no funciona el teclat, em sembla que malauradament es la única opció :(

Salut!

---

### Post by Frealof on 2008-03-13
Molt bones

Finalment la necessitat i els diversos problemes que han anat apareixent m'han portat a re-instal·lar Ubuntu de nou. El fet es que no ha servit, l'escriptori continua trigant massa a executar-se. 

Sento la musiqueta de benvinguda però quan acaba, m'haig d'esperar cap a mig minut (quan no més)  a què em carregui ni que sigui un quadre (ja no dic carregar-lo tot per complet), quan abans de fer no sé quina actualització... era acabar la musiqueta i carregar-me l'escriptori de manera gairebé instantània.

Les dos coses que he canviat des de llavors son: 

La targeta gràfica per una de millor amb més memòria i tal. Una Nvidia GeForce 7300 GT i tinc instal·lats els controladors restringits per obtenir l'acceleració gràfica.

La manera de connectar-me a Internet. Abans amb cable, ara, sense fils. He provat de tornar a connectar-me amb el cable però res, no hi ha canvis.

Alguna idea? Gràcies per endavant.

---

### Post by papapep on 2008-03-13
Has provat a entrar en mode gràfic segur?? Hi ha diferència de velocitat?

---

### Post by Frealof on 2008-03-14
Hola a tothom de nou.

Tal com indicava en papapep he provat d'entrar en mode gràfic segur i realment si que s'ha notat un canvi bastant espectacular en la velocitat de càrrega de l'escriptori. Ho he provat tan amb l'usuari root com amb l'usuari normal i corrent i ha anat igual de ràpid.

Salut! I gràcies per respondre ;)

---

### Post by CarlesOriol on 2008-03-14
Has fet un pecat capital ubuntaire ... iniciar sessió com a root.

A veure si trobes el fil que parlavem d'anar en gallumbus per les Rambles. (em fa mandra tornar-ho a comentar)

---

### Post by pserra on 2008-03-14
Doncs a mí em triga 2 minuts  entrant les contrasenyes... tinc un portàtil de 4 anys.... 512 de Ram.... em sembla que m'haure de conformar..
He mirat l'arxiu, i no entenc rés.. considero que és per usuaris avançats...veig el que es carrega però tinc el temor que 'peti'  si intento eliminar-ne un.
He notat un alentiment depassar de Feisty a Gutsy... em sembla que si hi han més actualitzacions passaré d'actualitzar-lo més....
Saluts.

---

### Post by Frealof on 2008-03-14
Hola de nou!

No he trobat el què deies de les Rambles CarlesOriol  ;) Però tot i així justificaré per què he comés sacrilegi...

Si he iniciat una sessió com a root només era per veure si hi havia alguna diferència entre el temps d'inici d'un usuari normal o l'administrador.

Això en el meu cas vol dir Iniciar-veure que el temps es el mateix-sortir-apagar, res més. No he fet cap altre pas. No sé si puc haver danyat el sistema només fent això... espero que no... 

Com que al crear l'usuari normal li vaig donar drets d'administració, intento fer-ho tot des d'allà i l'usuari root deixar-lo tranquil·let que sembla que hi esta molt bé :). Pel què no puc... o no sé com, busco per la xarxa i/o demano ajuda als qui en saben més que jo. Com es el cas que ens ocupa...

Salut!

---

### Post by Rubunter on 2008-03-17
A mi tb em triga excessivament a carregar l'escriptori des que introdueixo la contrassenya. Tarda al voltant d' un minut! Hi ha alguna cosa remarcable al gràfic que he tret del bootchart?

---

### Post by Miquel Ubuntero on 2008-03-18
Es molt estrany!!!
Jo també tinc inici sessió lent. Però als 2 altres usuaris del meu pc no!
Quant faig "sistema-surt", ja hem puc morir esperant.
He canviat la tarja gràfica, perquè en algun lloc vaig sentir parlar malament de la que abans tenia (Ati Radeon 9600). Ara he posat una Radeon 7000. Però igual.
Vaig crear-me un nou usuari i va funcionar be un parell de dies. Desprès, en traspassar  els meus docs al nou usuari, va tornar a anar lent. Pot ser que els meus docs tinguin virus??? O com diuen a casa, soc gafe!!!
Estic molt intrigat.
Si algú te cap suggeriment  ...

---

### Post by Frealof on 2008-03-19
Ei bones!

Si que es curiós, oi? 

No sé si podria ser una Línia vàlida a seguir però... Se m'ha acudit que podria ser alguna falla en el Gnome per si mateix.

La màquina es carrega amb una velocitat que crec que es prou raonable, 25-30s segons les diferents gràfiques de bootchart, fins que apareix la plana d'inici de sessió... Es a partir de què entro la contrasenya que la càrrega es ralentitza molt. Un cop carregat l'entorn si vull canviar d'usuari surto - canvio d'usuari (un altre que he creat completament net)- contrasenya - Escriptori pràcticament carregat a l'instant - surto - torno al meu Usuari... i es carrega sense problemes...

Avui intentaré buscar alguna eina o mètode que em permeti fer algun tipus de diagnòstic del Gnome... Si trobo res, abans de "provar", ho penjaré aquí i a veure què en penseu els qui ho llegiu, ok? ;)

Salut!

---

### Post by Miquel Ubuntero on 2008-03-19
Esperem les teves noticies Frealof ...
Mentrestant. Voldria saber si per tornar a instal·lar l'escriptori Gnome ho poc fer fent "sudo apt-get install gnome-desktop"?
Afecta d'alguna manera als documents o configuracions dels usuaris?
gracies.

---

### Post by papapep on 2008-03-19
El[ (meta)paquet]("http://www.ugr.es/~delealui/doku.php?id=delealui:sistemas_gestion_paquetes") que instal·la l'escriptori Gnome a Ubuntu es diu [ubuntu-desktop]("http://packages.ubuntu.com/search?keywords=ubuntu-desktop&searchon=names&suite=gutsy&section=all").
Normalment, quan es reinstal·len paquets que ja estaven instal·lats es respecten els fitxers de configuració antics, a no ser que es demani quin es vol conservar al moment de reinstal·lar. Una altra cosa és que s'esborri el paquet amb l'opció "purge", que també esborra els fitxers de configuració. 
O sigui, que no és 100% segur, tampoc especifiques a quins fitxers en concret et refereixes, però és áltament probable que els respecti. :-)

EDITO: Per cert, recorda que cada tema ha d'anar a un fil diferent.

---

### Post by Miquel Ubuntero on 2008-03-19
gracies papapep. Tindre en compte lo de respectar el fil.
Salut!

---

### Post by Frealof on 2008-03-20
Molt bones a tothom!

Ahir vaig estar buscant si hi havia alguna eina de diagnòstic per la xarxa però sembla que el senyor gúgel i jo no es portem gaire bé últimament... Finalment en alguna banda vaig llegir que hi havia una carpeta on hi havia una mena de registre del què havia anat passant mentre el PC estava engegat i on després vaig recordar hi ha la carpeteta de les gràfiques del bootchart /var/log/ (hauré de menjar mooooltes cues de pansa ;)) .

Bé, he estat mirant una mica els fitxers (només els he obert i mirat des de entorn gràfic), per veure si hi veia algun error. Els fitxers en qüestió son:

user.log.0
syslog.0
daemon.log.0

Us passo una còpia del syslog.0 (ho he hagut de comprimir perquè sinó no m'ho deixava adjuntar) d'ahir des del moment que he vist un lloc on hi ha algun error. A veure si els qui en sabeu més hi veieu res que pugui servir per identificar el què passa... Jo de moment m'hi perdo bastant amb tot això.

Salut i gràcies!

---

### Post by Frealof on 2008-03-20
Ei!

Ha estat enviar la resposta anterior i m'he trobat que m'ha saltat la pantalla d'inici on has d'entrar l'Usuari per iniciar la sessió.

He fet una còpia del syslog a partir del moment que m'ha fet sortir...


Mar 20 09:50:14 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:50:14 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:50:14 terrako dhclient: bound to 192.168.1.34 -- renewal in 26 seconds.
Mar 20 09:50:14 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:50:27 terrako gdm[6446]: WARNING: gdm_slave_xioerror_handler: s'ha produït un error d'X fatal - S'està reiniciant :0 
Mar 20 09:50:30 terrako kernel: [ 9062.008000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Mar 20 09:50:30 terrako kernel: [ 9062.008000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Mar 20 09:50:30 terrako kernel: [ 9062.008000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Mar 20 09:50:40 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:50:40 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:50:40 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:50:40 terrako dhclient: bound to 192.168.1.34 -- renewal in 25 seconds.
Mar 20 09:50:52 terrako hcid[6348]: Default passkey agent (:1.366, /org/bluez/passkey) registered
Mar 20 09:50:52 terrako hcid[6348]: Default authorization agent (:1.366, /org/bluez/auth) registered
Mar 20 09:50:53 terrako NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 20 09:50:53 terrako NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Mar 20 09:51:05 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:51:05 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:51:05 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:51:05 terrako dhclient: bound to 192.168.1.34 -- renewal in 30 seconds.
Mar 20 09:51:35 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:51:35 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:51:35 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:51:35 terrako dhclient: bound to 192.168.1.34 -- renewal in 25 seconds.
Mar 20 09:52:00 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:52:00 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:52:00 terrako dhclient: bound to 192.168.1.34 -- renewal in 29 seconds.
Mar 20 09:52:00 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:52:29 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:52:29 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:52:29 terrako dhclient: bound to 192.168.1.34 -- renewal in 30 seconds.
Mar 20 09:52:29 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:52:59 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:52:59 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:52:59 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:52:59 terrako dhclient: bound to 192.168.1.34 -- renewal in 27 seconds.
Mar 20 09:53:26 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:53:26 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:53:26 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:53:26 terrako dhclient: bound to 192.168.1.34 -- renewal in 27 seconds.
Mar 20 09:53:53 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:53:53 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:53:53 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:53:53 terrako dhclient: bound to 192.168.1.34 -- renewal in 27 seconds.
Mar 20 09:54:20 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:54:20 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:54:20 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:54:20 terrako dhclient: bound to 192.168.1.34 -- renewal in 26 seconds.
Mar 20 09:54:46 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:54:46 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:54:46 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:54:46 terrako dhclient: bound to 192.168.1.34 -- renewal in 25 seconds.
Mar 20 09:55:11 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:55:11 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:55:11 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:55:11 terrako dhclient: bound to 192.168.1.34 -- renewal in 26 seconds.
Mar 20 09:55:37 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:55:37 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:55:37 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:55:37 terrako dhclient: bound to 192.168.1.34 -- renewal in 26 seconds.
Mar 20 09:56:03 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:56:03 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:56:03 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:56:03 terrako dhclient: bound to 192.168.1.34 -- renewal in 25 seconds.
Mar 20 09:56:28 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:56:28 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:56:28 terrako dhclient: bound to 192.168.1.34 -- renewal in 30 seconds.
Mar 20 09:56:28 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:56:58 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:56:58 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:56:58 terrako dhclient: bound to 192.168.1.34 -- renewal in 29 seconds.
Mar 20 09:56:58 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Mar 20 09:57:27 terrako dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 20 09:57:27 terrako dhclient: DHCPACK from 192.168.1.1
Mar 20 09:57:27 terrako dhclient: bound to 192.168.1.34 -- renewal in 27 seconds.
Mar 20 09:57:27 terrako NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 

Espero que serveixi ;)

---

### Post by papapep on 2008-03-20
> Mar 20 09:50:27 terrako gdm[6446]: WARNING: gdm_slave_xioerror_handler: s'ha produït un error d'X fatal - S'està reiniciant :0 

Fes un cop d'ull al log de l'xorg /var/log/Xorg.0.log (crec recordar que es diu així el fitxer). Té pinta de ser un error del gdm o del mateix servidor X, però probablement hi hagi més pistes a aquest fitxer.

Si fas, per exemple:

```
tail -100 /var/log/Xorg.0.log
```

Veuràs les últimes 100 línies d'aquest fitxer.

EDITO:També podries provar a instal·lar l'xdm (sudo aptitude install xdm) i utilitzar-lo com a eina d'entrada a les X, a veure si realment és problema del gdm.

---

### Post by Frealof on 2008-03-20
Bones!

Gràcies per respondre, he fet un cop d'ull a l'arxiu que em deies Papapep, tan les últimes 100 línies com a tot el fitxer en general

gedit /var/log/Xorg.0.log 

I... no hi he sabut veure res estrany... En tot cas us el penjo aquí a veure què us sembla...

D'altra banda m'agradaria saber, què pot portar instal·lar xdm... a part d'assegurar si el gdm es la causa del problema.

M'enduré el portàtil per anar seguint el fil, no podré "actuar" sobre el PC... però com a mínim quan arribi estaré a punt per fer-ho (espero...) ;) 

Salut i bona setmana "santa".

---


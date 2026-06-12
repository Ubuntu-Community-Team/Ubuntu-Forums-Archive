---
title: "Virtual Box"
date: 2008-02-23
forum: Catalan Team
---

### Post by xoldy on 2008-02-23
Bon dia a tothom, estic configurant el Virtual Box, per crear una imatge del XP, ja que per la carrera em fa falta servir el programari que em dona la UOC per compilar programes en C.

Em dona el missatge que us adjunto, i no se com canviar-li els permisos. és una de les coses que encara no li he pillat el truc. La béstia mM$ que porta dins, necessita usar el usuari root per poder-ho fer, o sigui que el més ràpid seria habilitar l'accés al root perquè iniciï sessió, però també se que aquesta manera irrita bastant als que utilitzeu Linux de fa temps.

Tinc una altra qüestió. El Virtual Box permet configurar la targeta wifi del meu portàtil, o és recomanable utilitzar la connexió que dona el host, i oblidar-me de tunejar el virtual box...

Moltes gràcies per endavant

---

### Post by xoldy on 2008-02-23
Ja he trobat el tema de canviar els permisos, per l'opció d'usuaris i grups. Només calia tancar la sessió perquè els canvis tinguessin efecte. De vegades tinc tendencia a fer el post fàcil, sense pensar el que estic posant.

Si em podeu contestar la segona part del post, que aquesta si que no la controlo...

Gràcies a mi mateix  i als que em contesteu després.

---

### Post by patrickfromspain on 2008-02-23
per configurar la tarjeta wifi del portatil no podras fer servir el Virtualbox, per una rao molt senzilla: no la detecta. El virtualbox fa servir la seva propia tarja de xarxa emulada: Adaptador Ethernet PCI AMD PCNET Family.

L'unica tarja de xarxa que podras fer servir configurant-la al Virtualbox sera un clau USB, tant wifi com ethernet. De totes formes, això no et permetra navegar desde ubuntu amb ella (o, al menys, no de manera directa).

Salut!

---

### Post by xoldy on 2008-02-23
Moltes gràcies Patrick, ara estic utilitzant-lo i em sembla més àgil que el vmware server. Miraré de fer servir el fil que parla de com "activar" els USB per poder posar el pendrive per compartir dades entre el virtualbox i l'ubuntu.

---

### Post by jodufi on 2008-02-23
Si el que vols és compartir dades entre l'Ubuntu i el win dins del virtualbox, no et cal USB ni res de res.

En el virtualbox ves a Devices -> Shared Folders i afegeix una carpeta compartida.

Després, des del terminal del win, executa:
net use x: \\vboxsvr\nom_de_la_compartició

---

### Post by xoldy on 2008-02-24
Hola Jodufi, era exactament el que volia, un espai on passar fitxers d'un lloc a l'altre.
Ho he provat, però no em funciona. He posat una ubicació que penja de /home/xoldy/compartida.

És important la ubucació d'aquesta carpeta?

Moltes gràcies

---

### Post by patrickfromspain on 2008-02-24
Probar a clicar amb el boto dret sobre mi PC conectar a unidad de red (o algo semblant) i alla busques la carpeta compartida.

si no et surt.. revisa-ho tot, que diria que estas fent quelcom malament.

salut!

---

### Post by SiscoGarcia on 2008-02-24
No sé si no acabarem anant off-topic, però com que el títol és ampli hi diré la meua (potser us en penedireu pel rotllo).

A la feina ens van muntar el servidor a una màquina amb CentOS. Per tal d'anar soltant-me amb aquest SO he volgut instal·lar-me una màquina virtual (Virtual Box) que el contingui. El primer que em va passar és que des de la versió viva (LiveCD) no se m'instal·lava, de manera que vaig haver de descarregar-me el DVD amb la versió instal·lable. Després em va passar com al xoldy, que no la podia fer còrrer si no era des de la terminal i com a root (gràficament i com a usuari normal em donava el mateix missatge). Un cop fet això el que em passa és que cada cop que la vull fer anar l'hi he d'instal·lar el SO; de fet ara només l'he de reinstal·lar, amb la qual cosa va més ràpid però no l'obre directament, que és el que entenc que hauria de fer.

Total que finalment em demana nom d'usuari i contrasenya i... s'està una bona estona amb la **pantalla negra** sense que hi pugui fer res.

Alguna idea?:(

Gràcies.

---

### Post by papapep on 2008-02-24
Quina versió, i de quina manera heu instal·lat del VirtualBox? I quina versió de CentOs intentes instal·lar-hi?

---

### Post by SiscoGarcia on 2008-02-24
He instal·lat la versió 1.5.0_OSE de VirtualBox des del Synaptic :( i el CentOS que intento instal·lar-hi és l'última versió, la 5.1

---

### Post by xoldy on 2008-02-25
Jo l'he instal·lat des del synaptic també. ja us miraré la versió.
De fet amb el tema de compartir carpetes des de linux i poder-les veure dins d'un windows és també una assignatura pendent que tinc.

Gràcies a tots

---

### Post by menut on 2008-02-25
Xoldy, tal com ho va dir el company Jodufi, has de crear la carpeta i donar-li un nom (compartida), anar a "Símbolo del sitema" (la consola del Windows) i escriure:


net use x: \\vboxsvr\compartida

Després, ves a "Mi Pc" i voràs la nova carpeta de la xarxa.

---

### Post by SiscoGarcia on 2008-02-25
He descobert quin era el problema amb la instal·lació/reinstal·lació cada cop que feia córrer la màquina virtual. El problema era que no havia desinstal·lat la imatge (.iso) del SO de la pestanya CD/DVD Rom de la configuració de la màquina virtual (captura), de manera que cada cop que l'engegava la feia anar.:oops:

Ara ja l'he desmarcada i no intenta instal·lar res, però no la puc fer córrer. Pot haver algun problema amb la RAM (només 256 MB, captura 2))? La màquina on la faig córrer és un Pentium IV a 1600 MHz amb 512 MB de RAM; potser falta màquina?

Gràcies.

---

### Post by SiscoGarcia on 2008-02-25
Oops!

M'he deixat les captures.](*,)

---

### Post by patrickfromspain on 2008-02-25
home.. amb això que ens ensenyes sera dificil poder-te dir res, no? Quin es exactament l'error? simplement la maquina no engega? Es queda penjada en algun punt? arribes a veure el grub o el lilo? Informacio!! ;)

---

### Post by SiscoGarcia on 2008-02-25
Patrick, l'error l'he explicat abans. 

 	
> Re: Virtual Box
No sé si no acabarem anant off-topic, però com que el títol és ampli hi diré la meua (potser us en penedireu pel rotllo).

A la feina ens van muntar el servidor a una màquina amb CentOS. Per tal d'anar soltant-me amb aquest SO he volgut instal·lar-me una màquina virtual (Virtual Box) que el contingui. El primer que em va passar és que des de la versió viva (LiveCD) no se m'instal·lava, de manera que vaig haver de descarregar-me el DVD amb la versió instal·lable. Després em va passar com al xoldy, que no la podia fer còrrer si no era des de la terminal i com a root (gràficament i com a usuari normal em donava el mateix missatge). Un cop fet això el que em passa és que cada cop que la vull fer anar l'hi he d'instal·lar el SO; de fet ara només l'he de reinstal·lar, amb la qual cosa va més ràpid però no l'obre directament, que és el que entenc que hauria de fer.

Total que finalment em demana nom d'usuari i contrasenya i... s'està una bona estona amb la pantalla negra sense que hi pugui fer res.

Alguna idea?

Gràcies. 

Com ja he dit, la part referent a haver d'instal·lar el SO cada cop ja l'he resolta però encara no el puc fer córrer, després d'introduir nom d'usuari i contrasenya, s'està "pensant" una bona estona i finalment em surt una pantalla negra on no hi puc fer res (he arribat a esperar-me una hora o així, per si és que li falta RAM).

Us cal alguna altra dada? No sé què més afegir, gràcies.

---

### Post by xoldy on 2008-02-27
Podria ser que a l'apartat de configuració de la network adapter, hagi de posar una opció diferent a la de NAT? Podria ser per això que no puc veure cap recurs de xarxa? Les altres opcions no les veig clares, la de host interface i la de internal network.

Moltes gràcies

---

### Post by patrickfromspain on 2008-02-27
ensenyans que tens a la part de shared folders.

EDITO: jo tinc posat nat i cap problema per compartir

---

### Post by xoldy on 2008-02-28
Doncs no ho entenc.
Aqui va el pantallasssu.

Podria tenir a veure amb el grup de treball de la màquina virtual xp?, han de ser les mateixes? A l'ubuntu, s'ha de posar en la captura de pantalla que adjunto?

Moltes gràcies per la vostra paciència

---

### Post by jodufi on 2008-02-28
Diria que tens mal configurada la carpeta compartida.
Realment tens un directori a «/compartida»?
T'adjunto com ho tinc ficat jo.

Després, si escrius:
«net use x: \\vboxsvr\comparida»
al terminal de windows, què et surt?

---

### Post by patrickfromspain on 2008-02-28
opino el mateix! La carpeta /compartida existeix? Jo, per exemple, tinc compartit tot el root. El mes recomanable seria compartir el teu home, suposo (/home/xoldy, per exemple)

salut!

---

### Post by xoldy on 2008-02-28
Hola, gràcies pel vostre temps.
Des del cmd del windows em surt el que us adjunto.

Ara tal i com em suggeriu, he fet una carpeta anomenada compartida al /home/xoldy, i la he compartit amb el nom linux.

quan faig la comanda net use des del windows em surt aquest error.

Segueixo investigant...

---

### Post by SiscoGarcia on 2008-04-07
Hola de nou, després de tants dies. Resulta que finalment me n'he pogut sortir a fer córrer la màquina virtual gràcies al que he llegit en aquest [altre fil]("http://ubuntuforums.org/showthread.php?t=742092"), la qual cosa tot sigui dit no deixa de ser un problema pel contrari del que és habitual (em refereixo a un tema= un fil).

El que em passava és que no podia fer anar el Virtual Box perquè no havia dit quins eren els usuaris d'aquest programa segons es comenta a l'altre fil. Però hores d'ara el problema que tinc és que només puc fer anar CentOS com a root, no com a l'usuari que he creat, però això ja és un tema de CentOS i no d'ubuntu. Perquè... no serà un problema de VirtualBox?

En fi, ... continuarà :(

---

### Post by SiscoGarcia on 2008-04-07
Com que editant no hi ha possibilitat d'adjuntar una imatge de la CentOS corrent (o no sé com fer-ho), l'adjunto aquí.

---

### Post by lFossil on 2008-04-08
Ei hola cracks, ja fa temps que vaig preguntar per si em podíeu ajudar perquè no puc fer anar la màquina virtual. Hem vau dir que tenia alguna cosa malament de la imatge iso però no ho entenc i no sé com trobar-ho. Ja fa temps que intento de tot, però res fructífer, si hem podeu tirar un cable...:)

Us adjunto aquesta imatge: [http://img366.imageshack.us/my.php?image=capturanh6.png](http://img366.imageshack.us/my.php?image=capturanh6.png)

---

### Post by papapep on 2008-04-08
> **SiscoGarcia said:**
> Com que editant no hi ha possibilitat d'adjuntar una imatge de la CentOS corrent (o no sé com fer-ho), l'adjunto aquí.

Sisco, jo no entenc què hem de veure a la impressió de pantalla, ho sento...

---

### Post by papapep on 2008-04-08
> **lFossil said:**
> Ei hola cracks, ja fa temps que vaig preguntar per si em podíeu ajudar perquè no puc fer anar la màquina virtual. Hem vau dir que tenia alguna cosa malament de la imatge iso però no ho entenc i no sé com trobar-ho. Ja fa temps que intento de tot, però res fructífer, si hem podeu tirar un cable...:)

Us adjunto aquesta imatge: [http://img366.imageshack.us/my.php?image=capturanh6.png](http://img366.imageshack.us/my.php?image=capturanh6.png)

Si com tu dius ja tens obert un fil obert hauries de seguir allà. Probablement allà hi haurà informació que en aquest no hi sigui i s'adapti més al teu problema.

---

### Post by SiscoGarcia on 2008-04-10
> **papapep said:**
> Sisco, jo no entenc què hem de veure a la impressió de pantalla, ho sento...

Perdó papapep, només volia mostrar que me n'he sortit. Gràcies.

---

### Post by xoldy on 2008-04-25
Hola a tots, per fi he pogut contactar amb la carpeta compartida, però em temo que ha estat gràcies a la actualització a Hardy. Bé de fet, primer vaig actualitzar, i el virtual box no em funcionava, i vaig començar a veure coses que podien complicar-me una mica la vida i vaig optar per instal·lar de zero.
Una meravella. Va perfecte!!

Salutacions per tots

per cert, com es posa el solved als temes en el nou format de fòrum?

---


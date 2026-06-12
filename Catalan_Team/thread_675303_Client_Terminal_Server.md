---
title: "Client Terminal Server"
date: 2008-01-22
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-01-22
Bones.
Voldria saber si per conectar-me des de el meu PC amb Ubuntu a un altre que tingui Windows XP puc fer servir l'aplicació "Client de Terminal Server"?
Els 2 pc's no estàn en la mateixa xarxa. Si tenen conexió ADSL.
He vist algún post però no ho veig clar.

El que pretenc és conectar-me remotament al pc del meu sogre per poder configurar-li coses que ell no sap fer.

Salutacions cordials, Miquel Ubuntero :)

---

### Post by lluisalguero on 2008-01-22
Si saps la IP pública del pc on et vols connectar, no hi ha cap problema...si és ip dinàmica, ja no ho tinc tant clar com pot anar.

Jo faig servir aquesta aplicació per a visualitzar l'altre pc que tinc que corre baix windows, però el tinc a la mateixa xarxa i només ficant la ip privada ja n'hi ha prou.

També pensa que s'han d'obrir el ports corresponents al router del pc que vulguis (en el teu cas el que porta windows) que en el meu cas, vaig deixar el que porta configurat per defecte, el 5900.

Espero que t'hagui servit d'alguna cosa.

Lluís

---

### Post by Tomàs M. on 2008-01-22
> **Miquel Ubuntero said:**
> Bones.
Voldria saber si per conectar-me des de el meu PC amb Ubuntu a un altre que tingui Windows XP puc fer servir l'aplicació "Client de Terminal Server"?
Els 2 pc's no estàn en la mateixa xarxa. Si tenen conexió ADSL.
He vist algún post però no ho veig clar.

El que pretenc és conectar-me remotament al pc del meu sogre per poder configurar-li coses que ell no sap fer.

Salutacions cordials, Miquel Ubuntero :)

Amb [www.logmein.com](www.logmein.com) tens una connexió segura, i et pots oblidar d'ip's i de ports. Ho has d'instal·lar a l'ordinador remot i accedir-hi amb l'Ubuntu amb només un navegador web (amb el Java Runtime Environment instal·lat; [https://na1.salesforce.com/_ui/selfservice/pkb/PublicKnowledgeSolution/d?orgId=00D300000006VGf&lang=1&id=50130000000Gk2i&retURL=%2Fsol%2Fpublic%2Fsolutionbrowser.jsp%3Fcid%3D02n30000000DBsi%26search%3Dlinux%26orgId%3D00D300000006VGf%26lang%3D1&ps=1](https://na1.salesforce.com/_ui/selfservice/pkb/PublicKnowledgeSolution/d?orgId=00D300000006VGf&lang=1&id=50130000000Gk2i&retURL=%2Fsol%2Fpublic%2Fsolutionbrowser.jsp%3Fcid%3D02n30000000DBsi%26search%3Dlinux%26orgId%3D00D300000006VGf%26lang%3D1&ps=1))
Sort!

---

### Post by lluisalguero on 2008-01-22
> **Tomàs M. said:**
> Amb [www.logmein.com](www.logmein.com) tens una connexió segura, i et pots oblidar d'ip's i de ports. Ho has d'instal·lar a l'ordinador remot i accedir-hi amb l'Ubuntu amb només un navegador web.
Sort!

Està molt bé això que ens mostres, però ficar les dades del meu pc a una web que no conec..."va a ser que no", prefereixo fer-ho amb el terminal server

---

### Post by pespin on 2008-01-22
Sempre pots instal·lar un servidor VNC a l'ordinador on vulguis accedir i també si vols pots agafar un domini amb ip dinamica del pal no-ip o mydns, i així no has d'estar pendent de la IP.:)

---

### Post by abuch on 2008-01-23
Hola,

nosaltres fem servir (en un institut, unes 90 màquines) l'rdesktop per accedir des d'ordinadors Linux a un servidor Windows, per treballar amb una aplicació que només funciona amb Windows. També hi accedeixo des de casa fent servir la IP pública i redirigint el port 3389.

Fem servir rdesktop amb el protocol RCP (Remote Control Protocol) perquè hem vist que era molt més ràpid que fer servir el VNC.

Sobre la problemàtica d'IPs dinàmiques ja han contestat abans.

Aleix Buch

---

### Post by Miquel Ubuntero on 2008-01-24
Gracies a tots. Molta informació, que be!
Ja he probat LogMeIn, i m'ha agradat per lo fàcil que ha estat.

Ara be, només hem val per accedir a un altre pc amb guindous.
Algú sap si hi ha algo semblant a LogMeIn per Linux?

Salut!

---

### Post by Tomàs M. on 2008-01-24
> **Miquel Ubuntero said:**
> Gracies a tots. Molta informació, que be!
Ja he probat LogMeIn, i m'ha agradat per lo fàcil que ha estat.

Ara be, només hem val per accedir a un altre pc amb guindous.
Algú sap si hi ha algo semblant a LogMeIn per Linux?

Salut!

Amb connexió segura, FreeNX, però no l'he provat...

---

### Post by papapep on 2008-01-24
[FreeNX]("http://freenx.berlios.de/") funciona sota SSH, i rendeix esplèndidament bé. Consumeix poc ample de banda i és espectacularment ràpid fins i tot amb servidors de recursos modestos.
Cal tenir clar que és un concepte diferent, per qui no ho sàpiga, a VNC o LogmeIn.
Amb VNC comparteixes la sessió amb l'usuari que està davant de la pantalla remota, amb FreeNX obres una nova sessió gràfica per a tu solet. Des d'el teu ordinador i amb el client de FreeNX obres una nova, només per a tu ningú la veu, sessió Linux (amb l'entorn gràfic que triis Gnome, KDE, XFCE, etc). O sigui, és com connectar-se per ssh però amb l'afegit de l'entorn gràfic.

Amb FreeNX fins i tot pots deixar una sessió que has obert des d'un ordinador, anar a un altre ordinador (a l'altra punta del món si cal) i continuar la sessió amb els programes i en la mateixa situació que la havies deixat.

---

### Post by ilku on 2008-01-25
Aprofitant l'avinentesa que a sortit el freenx, algú em pot dir quin es l'adreça a afegir al source.list per una gnome gutsy. he probat varies i no me sortit.

Gracies.

---

### Post by papapep on 2008-01-25
Doncs, que jo sàpiga no hi ha repositoris per a això. T'has de descarregar els paquets del projecte [FreeNX]("http://freenx.berlios.de/") i de [Nomachine]("http://www.nomachine.com/select-package.php?os=linux&id=1") (la empresa que fa clients per a diferents plataformes).

Amb l'Ubuntu no ho he provat, però amb Debian funciona bé i no hauria d'haver-hi, en principi, massa diferències.

---

### Post by Miquel Ubuntero on 2008-01-26
Hola de nou.
He estat provant LogMeiN i crec que va masa lent. Be, en conectarme
remotament, cada cop que faig un clic amb el ratolí, la pantalla es refresca d'amunt a vall arrivant a trigar 8 o 10 segons, desesperant!
Algú sap si aixó es normal?
He estat mirant configuració però no hi veig res.

---

### Post by orestesmas on 2008-01-26
L'empresa NoMachine va alliberar les llibreries que permeten establir una sessió NX, però no va alliberar el codi del client ni del servidor. El projecte FreeNX intenta suplir aquesta mancança, però de moment tot és una mica manual. Si vols provar el protocol NX amb èxit el més segur és descarregar-te el client i servidor de NoMachine, que són privatius però gratuïts. Són paquets .DEB, que un cop descarregats has d'instal·lar amb "dpkg".

---

### Post by Tomàs M. on 2008-01-27
> **Miquel Ubuntero said:**
> Hola de nou.
He estat provant LogMeiN i crec que va masa lent. Be, en conectarme
remotament, cada cop que faig un clic amb el ratolí, la pantalla es refresca d'amunt a vall arrivant a trigar 8 o 10 segons, desesperant!
Algú sap si aixó es normal?
He estat mirant configuració però no hi veig res.

Quan dius " la pantalla es refresca d'amunt a vall" no sé si vols dir exactament que es refresca o que es desplaça... no serà que et fa scroll perque no has posat "full screen"? A mi el logmein em va a tot drap. Per connectar-me a una màquina vella de casa amb ruindows faig servir logmein, perquè em va més ràpid que el vnc amb la xarxa local, a més evito tenir un forat obert amb una connexió no segura (si mireu els esdeveniments del firestarter us fareu creus dels intents de connexió que hi ha per tot arreu; digueu-me paranoic però jo fins i tot tinc configurat l'SSH perquè només s'hi pugui entrar amb clau i no amb contrassenya).

Edito perquè, evidentment, si fem servir el vnc només a la xarxa local i sense obrir-ne els ports a l'encaminador, ja és una altra història. Per una altra banda, crec que hi ha mètodes per fer que les connexions vnc siguin segures.

---

### Post by Miquel Ubuntero on 2008-01-27
Hola tomàs.
Lo de la pantalla vui dir que, la imatge va apareixen d'amunt a vall.
En fer clic a qualsevol lloc, desapareix la imatge i torna a apareixe.
Triga uns 8 o 10 seg. Fins ara no ho he fet amb full screen. si tinc tems ja provaré full screen aquest vespre.
gracies, Miquel.

---

### Post by Tomàs M. on 2008-01-27
Doncs ho sento però no en tinc ni idea. Suposo que tens el plugin java de Sun instal·lat, no? Crec que sí perquè si no, em sembla que no podries accedir. Potser prova de desinstal·lar-lo i tornar-lo a instal·lar. Des de la Gutsy que és als repositoris, cerca els paquets sun-java6-jre i sun-java6-plugin al Synaptic.
Sort!

---


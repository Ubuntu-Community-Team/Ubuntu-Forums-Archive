---
title: "[SOLVED] Virtualbox I Els Usb"
date: 2008-01-10
forum: Catalan Team
---

### Post by kukat on 2008-01-10
Fa ja un temps que faig servir el Virtualbox per accedir a Guindows sense sortir de Linux, i hem funciona de meravella!! Un programa meravellós que quasi no es nota que està funcionant...:)  El necessite per a un parell de programes (més que res per que a l'institut donem eixos programes...) i per al ToneportUX1, l'aparell per a grabar la guitarra i el saxo...

Algú hem pot ajudar a configurar els USB? He provat amb tot el que diuen  per la xarxa, però sense resultats... :( No funcionen.  Seria magnífic poder configurar els USB de Virtualbox per a poder instal.lar el ToneportUX1, ja que fa falta la connexió USB per a que funcione... Seria ja l'últim que hem faltaria per a no sortir a Windows pràcticament mai, cosa que m'alegraria molt...

Tinc una carpeta compartida de Ubuntu al Windows Virtual, cosa que hem va molt bé, però ara hem faltaria el tema dels USB per a l'aparell de grabació de música.

Gràcies adelantades a tots!

---

### Post by orestesmas on 2008-01-10
VirtualBox es presenta en dos "sabors". L'un és GPL, però no té suport per USB. L'altre és privatiu, i inclou suport per USB (i tres cosetes més), tal i com s'explica en [aquesta pàgina]("http://virtualbox.org/wiki/Editions").

O sigui que si vols suport per USB has de fer servir la versió privativa (hi ha paquets per ubuntu gutsy). L'elecció eés teva.

---

### Post by CarlesOriol on 2008-01-10
Aquesta si... (que es meva :-) )

[http://bitacoras.enging.com/doku.php?id=virtualbox:usbengutsy&s=virtualbox](http://bitacoras.enging.com/doku.php?id=virtualbox:usbengutsy&s=virtualbox)

---

### Post by kukat on 2008-01-10
No funciona :( . Son els mateixos passos que vaig fer fa ja unes setmanes i no hem va funcionar... 
Tinc que tindre la verssió privativa per a fer servir aquestos passos? 
He canviat açó:
[I]# USB devices (usbfs replacement)

SUBSYSTEM=="usb_device",		MODE="0666"[/I]

I he creat el fitxer a:
kukat@kukatmaulet:~$ sudo gedit /etc/udev/rules.d/40-permissions.rules
 
I he ficat el contingut que expliques... He fet alguna cosa mal o tinc que tindre la verssió privativa?

Per cert, tinc els VirtualBox Guest Additions instal.lat. Tinc que configurar alguna cosa al Virtualbox? 

Moltíssimes gràcies, els passos que has fet són prou més senzills que els que havia vist per la xarxa:)

Salut!

---

### Post by orestesmas on 2008-01-10
Perdona, em sembla que t'he malinterpretat. Segurament ja fas servir la versió privativa però no et funcionen els USB perquè a la gutsy no es munta per omissió el directori /proc/bus/usb.

Per tal que et funcioni, o bé fas allò que t'ha dit el Carles (solució permanent), o bé muntes el sistema de fitxers "proc" a mà (ho hauràs de fer cada vegada que reinicïis)

Per muntar el proc:

```
sudo mount -t proc none /proc/bus/usb
```

Llavors ja pots arrencar VirtualBox normalment i t'ha de reconèixer els dispositius USB

---

### Post by kukat on 2008-01-10
Tinc la versió "OpenSource" m'he donat compte que ho posa a la finestra d'entrada del programa. 

L'altra versió és de pagament o té un periode d'evaluació o alguna cosa així? Si l'instal.le s'esborrarà la màquina que ja tinc?
Gràcies!

---

### Post by CarlesOriol on 2008-01-10
No té res del que dius però té una cosa pitjor... és que no és lliure.

Però com és per fer anar programari privatiu me la XXXXXXXXX <- Automoderat

---

### Post by kukat on 2008-01-10
=D>  També es veritat!!   En aquest cas si, per que dubte molt que un usuari de Guindows vullga fer el contrari:) (fer anar Ubuntu)

Doncs instal.laré la versió privativa, amb l'esperança de que no s'esborre la màquina que ja tinc creada. I si es així, doncs l'instal.laré altra vegada...Que tenim que fer! 

Moltes gràcies!!! A veure si ja puc fer funcionar el Toneport

---

### Post by papapep on 2008-01-10
XXXXXXXXX == (campamento)  [[Nou stàndar català de censura]("http://youtube.com/watch?v=jyf8nM20GpI")]

---

### Post by kukat on 2008-01-10
:biggrin::biggrin::biggrin: jajajajajajaj. Que bons els del Polònia!! Sort que tenim el youtube i el tv3 a la carta, si no no se el que fariem aci al País Valencià!!! (La Carrasqueta està a uns kilòmetres de casa i tv3 ja no es veu...:()
 
Doncs vaig a instal.lar el Virtualbox Privatiu i ja vos conte.

---

### Post by kukat on 2008-01-10
Ja tinc la versió Privativa, i després de comprovar que tots els passos de Carles estaven igual, i de muntar l'unitat com a dit Orestesmas, hem surt la seguent finestra d'error:

[IMG]http://img132.imageshack.us/img132/2219/capturavirtualboxerrorev0.png[/IMG]

Alguna suggerència?

---

### Post by orestesmas on 2008-01-10
Com l'has instal·lat aquesta versió? A mà a través d'un .deb o afegint el lloc del VirtualBox al fitxer sources.list i llavors amb apt-get (o equivalent)?

Què veus si fas un
```
ls -l /proc/bus/usb
```?

---

### Post by kukat on 2008-01-10
L'he instal.lat amb un .deb de la web oficial de Virtualbox.

I hem surt açó (molt llarg, a vorem si hem bannejen...)

<i> Ho esborre que ocupa molt i ja no es necessàri </i>

---

### Post by orestesmas on 2008-01-11
Perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó, perdó...

M'he equivocat amb l'ordre. Primer DESMUNTA això que has muntat rebotant la màquina o fent:
```
sudo umount /proc/bus/usb
```

i ara munta-ho correctament:

```
sudo mount -t usbfs none /proc/bus/usb
```

Fixa't que l'error era que t'havia dit que muntessis el sistema virtual de fitxers "proc", quan allò que havies de muntar era el sistema virtual de fitxers "usbfs"

I'm zorry...

---

### Post by kukat on 2008-01-11
gràcies gràcies gràcies gràcies gràcies gràcies gràcies gràcies gràcies gràcies gràcies gràcies!!! :)

Ja funciona!! He fet el que m'has dit i ja detecta el USB a la màquina virtual. Ara a provar si funciona el ToneportUX1.... a vorem...

Salutacions!! :guitar:

---

### Post by kukat on 2008-01-11
](*,)](*,)](*,)](*,)

No funciona el que volia fer. Quan insta&#320;le el TonePortUX1 no el reconeix com si estigués connectat.  I a la pestanya "Dispositivos", "Dispositivos USB"  si que està "Line 6 TonePort UX1 (0001)" Però està "desactivat", no es pot clicar. 

Podeu [veure una foto.]("http://img179.imageshack.us/img179/8238/capturawxpjordicorriendst4.png")

És l'únic que hem falta per a no tindre que "anar" a Windows cada vegada que vullga grabar alguna cosa a la guitarra o al saxo. 

Una noia de Quebec (formiii) [va fer anar un driver usb per a Linux]("http://ubuntuforums.org/showthread.php?t=640785"), però no es una usuaria molt activa (he estat investigant...jejej) La meva única alternativa era el Virtualbox. 

Estic obert a qualsevol suggerència, inclús "Pots vendre l'aparell i comprar-te tal cosa" o alguna cosa per l'estil... Ja vorem que faig!! 

Salutacions

---

### Post by orestesmas on 2008-01-11
M'aventuro a afirmar que pot ser un problema de permisos. Quan muntes el /proc/bus/usb amb l'ordre que t'he dit el propietari i el grup queden com a "root", amb permisos de lectura només, per la qual cosa els usuaris normals no hi poden escriure.

Pots provar de canviar el propietari dels fitxers i directoris a tu mateix, o de donar permisos d'escriptura a tothom (això darrer és el més efectiu, però també el menys recomanable des d'un punt de vista de seguretat. Ara bé, com que en tancar la màquina tot això desapareix, no hi veig un problema especial)
```
sudo chown -R ElTeuNomDUsuari /proc/bus/usb
```

Si vols fer-ho tot en una línia li pots passar paràmetres al mount la propera vegada que ho facis (suposant que el teu ID d'usuari sigui el 1000):
```
sudo mount -t usbfs -o devuid=1000,devgid=1000,devmode=0664 none /proc/bus/usb
```

Ja diràs què tal. De moment només l'encerto a mitges...

---

### Post by kukat on 2008-01-12
Moltíssimes gràcies!!!!!!!!!!!!!!!!!!!!!!!!!:lolflag:

Ja funciona!!!!!!!!! De meravella!!!! 

Ara a tocar!!:guitar:

Salut!!

---

### Post by Daerun on 2008-02-01
Perdoneu per ressucitar aquest tema, però és que tinc el mateix problema que en kukat, y seguint totes les indicacions no he sigut capaç d'arreglar-lo. En el meu cas el que vull és que el VirtualBox em reconegui l'scanner (un Benq 3300U), però quan entro a la màquina virtual, em trobo que no detecta res:

[IMG]http://img.photobucket.com/albums/v495/Daerun/posts/Captura-1.png[/IMG]


Tot i que els dispositius "hi són" (si clico amb el botó dret allà mateix, apareixen, però en gris, perquè no es poden seleccionar).

---

### Post by Daerun on 2008-02-01
Hey, ho he trobat!! :D He seguit les indicacions d'[AQUEST]("http://www.ubuntu-es.org/index.php?q=node/34908") Howto, el punt 6, concretament (TOTES les indicacions: proposa dues solucions, però cal seguir les dues), i ha funcionat, ja he pogut seleccionar l'escáner a la màquina virtual!

EDITO: creieu convenient que enganxi aqui el dit punt 6 del tuto aquest, per a major comprensió de la solució, o n'hi ha prou amb l'enllaç?

---

### Post by CarlesOriol on 2008-02-02
El punt 6 és curtet de traduir no? ;-) (si ho fas adjunta una referència a l'original)

---

### Post by Daerun on 2008-02-02
Doncs vet aqui el que he fet per poder fer servir un escàner connectat via usb dins la màquina virtual windows de VirtualBox:


Primer cal assegurar-se que hem configurat correctament i hem concedit tots els permisos d'execució necessaris al virtualbox per a poder-lo fer servir correctament. Tot està explicat en els posts anteriors.

Aleshores creem un grup d'usuaris anomenat "usbusers", en el què cal que incloguem els usuaris que faran servir el virtualbox+escàner (Sistema > Administració > Usuaris i Grups > Gestiona els grups > Afegeix grup). En el meu cas, es va assignar el 1002 com a identificador d'aquest grup.



Busquem l'arxiu /etc/fstab, i hi afegim la següent línia:

* none /proc/bus/usb usbusers devgid=1002,devmode=664 0 0* 

On "1200" és l'identificador del grup "usbusers"; si el vostre és diferent, l'haureu de canviar, és clar.



Ara entrem al Terminal i escribim:

[I]$ VBoxManage list usbhost


Amb això ens apareixerà un llistat dels dispositius usb que tenim connectats; un d'ells serà l'escàner, i se'ns mostrarà una cosa semblant a això:


[/I][I]UUID:               5763f299-2206-4eb1-b283-998feb4d7ea4
VendorId:           0x0a12 (0A12)
ProductId:          0x0001 (0001)
Revision:           5.37 (0537)
Address:            /proc/bus/usb/002/003
Current State:      Busy


El Vendorid i el Productid apareixen automàticament quan s'agrega l'escàner a la Configuració de la màquina virtual, però no està de més anotar-se'ls per si de cas; el mateix amb el UUID. El que més ens interessa és la Address; ara fem:

[/I]*$ sudo chmod 777 /proc/bus/usb/002/003*
 
(o l'Adress que a vosaltres us surti).



Després d'això només ens quedarà arrencar la màquina virtual. Mentre s'està encenent, passem el ratolí sobre la icona usb (a baix, a la dreta). Apareixerà un quadret que dirà "No USB devices attached"; però si cliquem amb el botó dret, podrem seleccionar l'escàner (o cualsevol altre cosa que haguem configurat).

Un defecte que he trobat d'aquest mètode, és que l'últim pas, el de buscar la adressa i donar-hi permisos, s'ha de repetir cada vegada que apaguem la màquina virtual, perquè la direcció no és fixa, si no que canvia cada vegada que tornem a encendre el Virtualbox.



Aquest Howto està extret d'[AQUI]("http://www.ubuntu-es.org/index.php?q=node/34908") i el va realitzar l'usuari neco. A part d'aquest tutorial, hi podreu trobar com instal·lar VirtualBox, com instal·lar els seus Guests Additions, algunes combinacions de tecles, com afegir directoris compartits, i com configurar el networking.

---


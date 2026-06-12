---
title: "Distro GNU/LINUX per a Pendrive en català?"
date: 2008-06-03
forum: Catalan Team
---

### Post by kukat on 2008-06-03
Que passa gent?

Algú sap d'una distro GNU/Linux en català per a instal.lar en el pendrive, que  ocupe poc espai i que estiga prou bé? He vist alguna cosa de Catux, però pareix que fa temps que ha desaparegut....Si pot ser, que siga fàcilment instal.lable..jejejeje. He provat ja amb Feather Linux (en anglés) sense resultats i anava a fer-ho amb UbuntuIES, però ocupa 1GB i no està en català.....


Igual es pedir massa...però bé. Si no hi ha en català, alguna en anglés que no siga excessivament complicada....

Moltíssimes gràcies per adelantat a tots!! :guitar:

---

### Post by Miquel Ubuntero on 2008-06-05
Hola company.
El que aquí expliquen:
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)
a mi hem va anar be amb Ubuntu 7.10
Les instruccions son en anglès però un cop tens instal·lat Ubuntu pots triar l'idioma.
Si tinc temps el cap de setmana, pot ser ho provaré i ja t'explicaré.
Si l'anglès és un problema, fes-no saber, que m'ofereixo a traduir-ho quant ho provi.
Salut!

Per cert, el meu pendrive es de 1GB i amb Ubuntu 7.10 va ocupar 750 MB.
Ja veurem com va amb Ubuntu 8.04 .....

---

### Post by PauGNU on 2008-06-06
Bones

La veritat és que el tema dels liveusb, per mi, no acaba de funcionar bé. Exceptuant un creador de liveusb de Fedora que es pot fer servir tant des del windows com des de GNU/Linux, la resta requereix massa passos que no solen ser molt intuïtius.

Així que:
[https://fedorahosted.org/liveusb-creator](https://fedorahosted.org/liveusb-creator)

---

### Post by Rubunter on 2008-06-06
Jo tinc el XUbuntu 8.04 instal·lat en un Pen de 4GB amb 3 particions. Fins ara m'ha anat bastant bé, tot i que només l'he provat amb el meu pc. Bé, també ho he provat amb un mac, però no vaig aconseguir arrancar des del pen. Aprofitant l'avinentesa...algú sap com arrancar des del pen amb mac?

---

### Post by SiscoGarcia on 2008-06-06
> **Rubunter said:**
> Aprofitant l'avinentesa...algú sap com arrancar des del pen amb mac?

Aquesta me la sé:

Un problema... un fil ;)



EDITO: Això no només és off-topic sinó que a més és "off-forum", diria jo. Suposo que aquesta informació la trobaràs més fàcilment en algun fòrum sobre Mac, no creus?

---

### Post by MorlanXaos on 2008-06-06
Jo vaig tindre bastants problemes per instal.lar el Linux en un pendrive.

Finalment, i la manera mes sencilla ha sigut aquesta:

_Components:_

Pendrive 4GB 22€
Ubunto 8.04 LTS
Ordinador DELL amb Win XP

_Coses a evitar:_

Com que el Ubunto, quant detcta que hi ha un XP, llavors vols instalar el Grub i aixo es una cosa que vull evitar ja que es el ordinador portatil de la feina.

_Soluciò_

* Desmontar el disc dur del portatil (3 tornillos)
* Efectuar el arranc del ordinador amb la tecla d'arranc alternatiu (F10, F12..)
* Possar el CD d'el Ubuntu
* Arrencar l'Ubunto, i instlar-lo en el USB
* Acabat tot aixo, tornar a instalar el disc dur, i a partir d'ara ja puc fer l'arranc alternatiu amb el pendrive.

No es massa elegant, i possiblement hi ha altres alternatives però funciona.

_Problemes sense solucionar:_

El pendrive nomes em funciona en aquest ordinador

---

### Post by kukat on 2008-06-06
Ostres, gràcies. Ja prove alguna de les solucions i vos compte!! Però crec que la del Fedora igual es més senzilla...ja vos dic alguna cosa!

Moltíssimes gràcies!

---

### Post by Miquel Ubuntero on 2008-06-06
Hola de nou.
Tal com vaig dir, ja ho he provat i m'ha anat be. Tinc l'Ubuntu 8.04 en un pendrive 1GB.
Si us sembla be, podeu llegir com ho he fet al meu blog.
[Http://miquel66.caliu.cat](Http://miquel66.caliu.cat)

salut!

---

### Post by pespin on 2008-06-07
Ostres, he vit a les instruccions del teu blog que particiones el disc com a FAT16. Això ho fas per alguna cosa en concret? No em sembla la millor opció havent-hi sistemes d'arxiu com ext3 no creus?

---

### Post by Miquel Ubuntero on 2008-06-07
Hola pespin.
A mi també hem va semblar extrany el tema de formatar amb Fat. Però simplement he seguit les instruccions que donen a [www.pendrivelinux.com](www.pendrivelinux.com)
que és la web on més informació i més fiable donen referent a Linux i els pendrive.
Si tinc temps, pot ser ho provo amb Ext3.

Salut!

---

### Post by Miquel Ubuntero on 2008-06-07
Hola de nou.
Seguint amb el tema distro GNU/LINUX en català, fa una estona he provat Ubuntu 7.10 en un pendrive però amb Windows corrent. O sigui, fa servir Qemu, que pot estar instal·lat en un pendrive o si vols un H.D. extern.
Va prou be. Pots desar dades i afegir/eliminar programari com si estes instal·lat.
Només li trobo una pega. Al panell de control de programari de windows apareix que tens instal·lat al Qemu. O sigui, no m'agrada que deixi rastre, per si es vol fer correr en un pc de feina. Ja m'enteneu, suposo.

Algú sap de res semblant, però que no deixi cap rastre al pc.
Ah! Cal tindre en compte que a de ser quelcom per un pc sense arrencada usb.

Aquesta ja és més difícil, no? ;)

Salut!

---

### Post by SiscoGarcia on 2008-06-09
> **Miquel Ubuntero said:**
> Hola de nou.
Tal com vaig dir, ja ho he provat i m'ha anat be. Tinc l'Ubuntu 8.04 en un pendrive 1GB.
Si us sembla be, podeu llegir com ho he fet al meu blog.
[Http://miquel66.caliu.cat](Http://miquel66.caliu.cat)

salut!

Hola Miquel, dues coses:

1.-  He provat d'instal·lar-me l'ubuntu 8.04 a un pendrive d'1 GB i no me n'he sortit, no és "bootable"; ara no tinc temps però potser demà compararé els fitxers del pen amb els del liveCD a veure què hi trobo. Tens alguna idea al respecte?

2.- Quan vaig veure l'altra intervenció que has fet en aquest fil, redreçant [ací]("http://www.pendrivelinux.com/2008/05...ll-from-linux/"), vaig pensar que es podria traduir (ja ho has fet) i posar-ho al wiki, et sembla que ho fem? Penso que pot servir perquè algu altre s'ho pugui muntar.

Ja diràs.

---

### Post by Miquel Ubuntero on 2008-06-09
Hola Sisco.
1. Lo del Ubuntu 8.04 que no has pogut fer i dius que no es botable, suposo que et refereixes al PC. En aquest cas, si el PC no es botable per usb, tens l'opció des de guindous fer correr Ubuntu 7.10 aquí t'ho expliquen en anglès: [http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/)

2. El link que hem poses en la teva segona questió no hem funciona. Pero si el que hem preguntes es per posar al wiki el que sigui del meu blog, endavant. Tothom està convidat a compartir tot (el poquet de moment!) que hi ha al meu blog.

Salut!

---

### Post by SiscoGarcia on 2008-06-09
Miquel,

1.- No, el PC sí que és botable des d'USB, el que m'ha passat és que no he pogut muntar bé el pendrive, de manera que selecciono d'arrencar des d'USB perquè llenci el live-USB i no ho fa, no el detecta. Això és el que no m'ha funcionat, però demà espero tenir una estona i poder-ho provar.

2.- Perdó, l'enllaç era a [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/) no sé què ha passat abans. En qualsevol cas, el que volia dir ja ho has respost i quan pugui ho passo al wiki, crec que hauria de dir-se [https://wiki.ubuntu.com/CatalanTeam/Recursos/ubuntu8.04-liveUSB](https://wiki.ubuntu.com/CatalanTeam/Recursos/ubuntu8.04-liveUSB) hi esteu d'acord?

Merci.

---

### Post by Miquel Ubuntero on 2008-06-10
Hola de nou.
Be, si no et xuta el pendrive o no es munta, jo porvaria amb un altre pendrive. Sovint a mi m'ha passat quelcom semblant, pot ser depent del fabrican o qualitat del dispositiu. (Tot aixó ho fabriquen a la xina o qui sap :)

El nom a posar al wiki, perfecte, per mi endavant.

Salut company!

---

### Post by SiscoGarcia on 2008-06-10
Hola,

No he pogut provar el live-USB però he creat el [wiki]("https://wiki.ubuntu.com/CatalanTeam/Recursos/ubuntu8.04-liveUSB"). Ara es tractaria que el modifiquéssiu i ho provéssiu.

---

### Post by kukat on 2008-06-11
Després de "lluitar" amb algunes distribucions per a "pendrive", al final vaig provar UBUNTU IES. [http://ubuntuies.com/](http://ubuntuies.com/), que inclou un instalador facilíssim que et deixa escollir entre uns 400 MB i uns 700 MB (lleugera i normal). I et deixa altra partició per a les dades. 

Vaig a provar si puc canviar-li l'idioma al Català (supose que si....) Et deixa també escollir entre Gnome i XFce, així que està prou completa!!

Salut!

---

### Post by Curial on 2008-06-11
> **Miquel Ubuntero said:**
> Hola de nou.
Tal com vaig dir, ja ho he provat i m'ha anat be. Tinc l'Ubuntu 8.04 en un pendrive 1GB.
Si us sembla be, podeu llegir com ho he fet al meu blog.
[Http://miquel66.caliu.cat](Http://miquel66.caliu.cat)

salut!

ai caram! si pensava que no es podia fer un usb en live amb menys de 4Gb.

De fet tinc en una de 2Gb la 7.10 i de tant en tant l'haig de reinstal·lar perquè alguna cosa peta.

Tanmateix no se per on vaig llegir que això escurça la vida útil del pendrive.

Això que comenta en MorlaXaos ja ho vaig provar i no em va funcionar, suposo que per la capacitat del llàpis.(2Gb)

Salut

---

### Post by Curial on 2008-06-11
Aquí ho vaig preguntar jo:

[http://ubuntuforums.org/showthread.php?t=697785](http://ubuntuforums.org/showthread.php?t=697785)

i apareix [http://slax.org/](http://slax.org/) que no em va agradar massa però és força lleuger.

Salut

---

### Post by SiscoGarcia on 2008-09-16
Finalment, quan ja no hi pensava, me n'he sortit de fer un ubuntu bootable en una clau usb d'1 Gb i em funciona. He fet cap no recordo com a [aquest article de la wikipedia]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") i he descarregat i instal·lat el [fitxer .deb del launchpad]("https://launchpad.net/liveusb/+announcement/973"); finalment només he hagut de posar un CD live a la lectora i connectar la clau. Per consola invoco el programa liveusb, s'obre la interfície gràfica, faig la tria corresponent i només he d'esperar una bona estona.

Només he provat el live usb, encara he de provar-ho en mode persistent, es pot triar quina mena de clau usb vols crear, si només arrancable o també amb una partició on desar-hi dades.

Suposo que el resultat no és diferent del proposat a l'enllaç a pendrivelinux però ho trobo molt més senzill.

Us adjunto el .deb per si ho voleu provar.

---

### Post by RainCT on 2008-09-17
També hi ha una altre aplicació semblant creada per Canonical, [https://launchpad.net/usb-creator](https://launchpad.net/usb-creator), que està disponible als dipòsits de l'Intrepid.

---

### Post by LitusMayol on 2008-09-20
Sinó a mi m'ha funcionat: l' **[Unetbootin]("http://www.somgnu.cat/unetbootin-creant-claus-usb-amb-gnulinux/")**. 

Sort!

---


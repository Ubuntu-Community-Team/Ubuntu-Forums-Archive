---
title: "[SOLVED] VirtualBox support driver error"
date: 2008-05-25
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-05-25
Bones.
tot just he actualitzat d'Ubuntu 7.10 a 8.04. Tot be menys VirtualBox.
Hem dona el següent error en inicar una MV:
The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..

He desinstal·lat VirtualBox, he esborrat la carpeta ".VirtualBox", he reiniciat el pc, i he tornat a instal·lar VirtualBox, peró hem dona de nou l'error.
Algú altre li ha passat?
Te sol·lució?
La versió que tinc és la 1.5.6_OSE

Gracies.

---

### Post by papapep on 2008-05-25
> He desinstal·lat VirtualBox, he esborrat la carpeta ".VirtualBox"

Si les coses funcionen com cal, un:

```
sudo aptitude purge nom_del_paquet_del_virtualbox
```

hauria de fer aquesta tasca i qualsevol altra que faci falta. Jo provaria a fer-ho així i després reinstal·lar-lo.

---

### Post by CarlesOriol on 2008-05-26
Pot ser que tinguessis abans insta&#320;lada la versió del web i ara la del repositori?

Si es així prova d'eliminar la OSE i insta&#320;lar l'altra.

---

### Post by Miquel Ubuntero on 2008-05-26
Hola de nou.
El problema inical a quedat resolt amb el "purge" que papape va recomenar.
Ara be, continua sense funcionar.
El nou missatge es el següent:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED

He provat, sense exit, instal·lar "virtual-ose-modules". Com que amb Synaptic habien molts, els vaig instal·lar tots i res:confused:

Hem sembla que ara tinc una mica de lio al cap! :confused::confused:

Us faria res de dir-me com començar de nou?

El que més hem lia es el tema dels ose-modules. No tinc clar quin es el adecuat. 

referent al comentari d'hen Carles Oriol, sempre instal·lo amb aptitude.

Moltes gracies pel vostre interés.

---

### Post by patrickfromspain on 2008-05-26
pot ser que ja estiguis fent servir el kernel 2.6.24-17-generic? Si es aixi, encara no hi ha el móduls per a aquest kernel, toca esperar suposo.

---

### Post by CarlesOriol on 2008-05-26
Encara que segur que ja ho has fet:

Has comprovat que el teu usuari està al grup vboxusers?

---

### Post by Miquel Ubuntero on 2008-05-27
Hola.
En resposta a les vostres preguntes:
-Si que estic com a usuari al grup vboxusers.
-Tinc kernel 2.6.22-14. Curios, el mateix kernel que tenia amb Ubuntu 7.10

Per cert, avui he llegit al manual de VirtualBox "Supported host operating systems, Ubuntu fins la 7.10". O sigui, crec que ho tinc xungo :(

La pregunta del "millón" (segur que no soc el primer en preguntar, però googlegant no ho he trobat): Es pot tirar enrere? Puc recular a Ubuntu 7.10?

Salut!

---

### Post by Diegstroyer on 2008-05-27
Proba el següent:
[LIST=1]
[*]Elimina virtualbox y tots els moduls instal·lats
[*]Ves a la pàgina de VirtualBox i descarregat la versió privativa
[*]Instal·la el paquet .deb baixat (segurament necessitaràs fer un **--force-all** al dpkg, ja que pot donar errors utilitzant el Gdebi)
[/LIST]

A mi es de la única manera que he aconseguit que funcioni, ja que com comenten, encara no està el kernel llest.

PD: si has borrat la carpeta oculta del teu home, hauràs perdut les maquines virtuals que hi havien, es a dir, ara hauràs de tornar-les a instal·lar.
PD2: en instal·lar la versió privativa, hauràs de tornar a posar-te al vboxusers.

---

### Post by papapep on 2008-05-27
Abans de fer el que et proposa en Diegstroyer, podries provar a fer un:

```
sudo /etc/init.d/vboxdrv setup

```

---

### Post by patrickfromspain on 2008-05-27
mm si fas servir hardy... hauries d'instal·lar el kernel que et toca: sudo apt-get install linux

salut

---

### Post by CarlesOriol on 2008-05-27
Jo tinc l'altra versió en Hardy i funciona sense problemes.

---

### Post by Miquel Ubuntero on 2008-05-27
Hola Patrickfromspain.
A veure que et sembla aixó:

miquel@miquel-desktop:~$ sudo apt-get install linux
[sudo] password for miquel: 
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
linux ja es troba en la versió més recent.
The following packages were automatically installed and are no longer required:
  libxalan110 linux-headers-2.6.24-16-generic libxerces27
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 0 no actualitzats.
miquel@miquel-desktop:~$ uname -r
2.6.22-14-generic
miquel@miquel-desktop:~$ 

No u veig clar!

Hola Diegstroyer (caray, he hagut de llegir el nom 2 cops) ;)
Aquí: [http://www.virtualbox.org/](http://www.virtualbox.org/)
no trobo el paquet.deb
només un paquet.run que no puc baixar-lo :confused:
T'hen recordés com vas aconseguir el .deb?
gracies.

---

### Post by patrickfromspain on 2008-05-27
ves al synaptic, i mira a ver si tens instal·lat el linux-image-2.6.24-16-generic o el 17.

---

### Post by Diegstroyer on 2008-05-27
El paquet l'has de buscar [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

A mi ara em va perfecte, a més, amb suport per a USB. :popcorn:

I no cal que t'emboliquis amb kernels ni res, ja que et compila el que necessites.

---

### Post by Miquel Ubuntero on 2008-05-28
Hola de nou.

Referent al linux image, tinc instal·lats el 2.6.22-14, 2.6.24-16 i 
2.6.24-17. Molts! no? :confused:

Referent al link d'en Diegstroyer, és el que ja conec, però en intentar vaixar-me l'arxiu per Platform Linux i386 anomenat VirtualBox-1.6.0-Linux_x86.run, no es baixa, sino que sembla que s'executen moltes línees
tipus comandos de terminal sense cap resultat :confused::confused:

No se on, googlegant, he llegit que hem caldria un arxiu .deb
però no el trobo.

Moltes gracies a tots pel vostre suport. Continuaré investigant.
A veure si entre tots treiem l'aigua clara ;)

---

### Post by Miquel Ubuntero on 2008-05-28
Bones.
He reinstal·lat de nou. Ja veieu que no hem rendeixo.

Un cop instal·lat de nou, seguint una proposta d'en Papapep e fet:

miquel@miquel-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
miquel@miquel-desktop:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
miquel@miquel-desktop:~$ 

Ajuda algo aquesta informació?

---

### Post by papapep on 2008-05-28
Bé, a la llista també porten parlant tot el dia del tema. Feu-li un cop d'ull i ho entendreu tot plegat: [http://comments.gmane.org/gmane.linux.ubuntu.user.catalan/10415](http://comments.gmane.org/gmane.linux.ubuntu.user.catalan/10415)

---

### Post by oriolsbd on 2008-05-28
Hola a tots.

Avui ja han pujat els mòduls de Virtualbox per al kernel 2.6.24-17, de manera que si es fa una actualització i s'instal·la els paquets "virtualbox-ose-modules-generic" i "virtualbox-ose-modules-2.6.24-17-generic" ja hauria de funcionar. Com a mínim, a mi m'ha tornat a funcionar.

Salut!

---

### Post by Diegstroyer on 2008-05-28
[http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb?BundledLineItemUUID=pkZIBe.pNBwAAAEaBshblzGu&OrderID=kN9IBe.p_QsAAAEa.cdblzGu&ProductID=lo5IBe.oSVAAAAEZ7akZKqcY&FileName=/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb]("http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb?BundledLineItemUUID=pkZIBe.pNBwAAAEaBshblzGu&OrderID=kN9IBe.p_QsAAAEa.cdblzGu&ProductID=lo5IBe.oSVAAAAEZ7akZKqcY&FileName=/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb")

Proba-ho ara, has de triar la versió per ubuntu 8.04 x86! Que és per a la arquitectura i386. No entenc per que tries el paquet run...

T'he posat l'enllaç directe a dalt, recorda que segurament hauràs d'utilitzar el --force-all i desinstal·la la versió ose abans.

---

### Post by Miquel Ubuntero on 2008-05-29
Hola!
Uau! Crec que la noticia de l'Oriolsbd es bona. Gracies :)

El nou link d'hen diegstroyer ok. Ara si.

Estic ansios d'arribar a casa i provar-ho. Avui no se si tindré temps, ho intentaré.
En quan ho provi us ho comento.
Gracies de nou a tots.
Salut!

---

### Post by MiquelBLL on 2008-05-30
Tambe vaig tenir problemes alb el Vbox al instal.lar la 8.04, no em funcionaba i em surtien els mateixos missatges, vaig buscar i vaig trobar el VBox 1.5.6 d'una web que ara no recordo i vaig seguie tot el que deia, i em funciona i reconeix usb i tot, si endollo el mp3 o reconeix pero no el mobil... Al fer actualitzacions tornaba a no funcionar, el vaig tornar a instal.lar i ja torna anar. Ara a sortit la 1.6 sera cuestio d'intentar instal.lar i veurer si funciona.

---

### Post by Miquel Ubuntero on 2008-06-01
Hola a tots.
Ja puc fer correr el VirtualBox.
En un altre disc dur del meu pc,també tenia Ubuntu 7.10 i en actualitzar-lo a 8.04, es va quedar amb kernel 2.6.24-17 funcionant tot be, inclòs V.B.
Dons be, suposo que en el meu H.D. alguna cosa va anar malament amb l'actualització. Ja cansat de fer proves, avui he formatat i instal·lat ubuntu 8.04. En actualitzar el sistema quedant a 2.6.24-17 tot be.
Dons au, moltes gracies a tots els que s'han interessat pel meu problem.
Salut! :guitar:

---

### Post by papapep on 2008-06-01
La meva gata i jo (bé, a ella em sembla que a ella li agrada bastant...) volem formular la més ferma oposició a aquesta proposta totalment esbojarrada i fora de lloc. No només fomenta la distorsió de la imatge personal, sinó que em provoca una calor i una urticària a la closca que no vegis....:-P

PD: els que ja sortiu amb adornament capilar habitualment no sigueu dropus, home, com a mínim canvieu-lo...

---


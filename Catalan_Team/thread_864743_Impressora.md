---
title: "Impressora"
date: 2008-07-19
forum: Catalan Team
---

### Post by xevi on 2008-07-19
Hola, 
Tot just m'inicio en Ubuntu (8,04)
provo d'instal.lar una impressosa Brother mFC-465cn.
He baixat i instal.lat el controldor.
Segons el fòrum he fet sudo aptitude search cups|grep i\ per (imagino) saber si els té instal.lats.
el resultat és
[sudo] password for wh1: 
p   apcupsd-cgi                     - APC UPS Power Management (web interface)  
i   bluez-cups                      - Bluetooth printer driver for CUPS         
i   cups-pdf                        - PDF printer for CUPS                      
i   cupsddk                         - CUPS Driver Development Kit               
i   cupsddk-drivers                 - CUPS Driver Development Kit - Driver files
i   cupsys                          - Common UNIX Printing System(tm) - Server  
i   cupsys-bsd                      - Common UNIX Printing System(tm) - BSD comm
i   cupsys-client                   - Clientprogramme für das Common UNIX Printi
i   cupsys-common                   - Common UNIX Printing System(tm) - common f
i   cupsys-driver-gutenprint        - printer drivers for CUPS                  
i   gnome-cups-manager              - CUPS printer admin tool for GNOME         
i   hal-cups-utils                  - CUPS integration with HAL                 
i   libcupsimage2                   - Common UNIX Printing System(tm) - image li
i   libcupsys2                      - Common UNIX Printing System(tm) - libs    
i   libgnomecups1.0-1               - GNOME-Bibliothek zur CUPS-Integration     
i A libgnomecupsui1.0-1c2a          - UI extensions to libgnomecups             
i   mfc465cncupswrapper             - Brother CUPS Inkjet Printer Definitions   
i   python-cups                     - Python bindings for CUPS 

Haig d'entendre que ho està. Em segueix sense detectar el driver correcte. La impresora està en xarxa (però he provat en local i em fa el mateix, és a dir res.)
Algú em pot ajudar?
Molt agrait

---

### Post by Morfeo99 on 2008-07-20
Jo potser sigui encara mes nou que tu a ubuntu, pero tinc instalades les impressores de brother models dcp 150C i la 135C en 2 ordinadors sense cap problema, amb escàner funcionant correctament... Amb això vull dir que les impressores brother son plenament compatibles amb ubuntu.
El teu model el desconec, però intentaré explicar els passos que jo vaig fer perquè es quasi segur que son els mateixos per tu...

Primer de tot:
Gestor de paquets Synaptic, fes una cerca introduint nomes el model de l' impressora i seleccionant "dependencies".
Marca i instal.la brother cups-wrapper-extra i brother-lpr-drivers-extra.

Fes una altra cerca per nom de:brscan2-0.2.4-0, marca i instal.la.
Encara que no t'ho demani, reinicia l'ordinador.

Amb això, després hauries de conectar l'impressora i automàticament la detecta! Si no et detecta be el teu model, et sortira la llista de possibles models, només hauras d'escollir el teu i llestos.

Per escanejar,vas a l'escaner d'imatges Xsane (aplicacions-gràfics-scàner d'imatges xsane ) i si no et detecta el model ho dius per aqui i ja posaré els detalls perquè rutlli.

Aclareixo que amb amb els models dcp150c i dcp135c rutlla perfectament, i per la meva experiencia hauria de rutllar amb qualsevol model brother.

Qualsevol cosa en que pugui ajudar...

---

### Post by Morfeo99 on 2008-07-20
Per cert, si intentes seguir els passos que indiquen a la web de brother no aconseguiràs que rutlli l'impressora.. 
He intentat contactar amb ells per aclarir el tema, però el meu anglès es tant limitat que ja m,ha vingut justet per poder registrarme al fòrum!!

---

### Post by patrickfromspain on 2008-07-20
[http://uint32t.blogspot.com/2008/06/linux-printing-brother-mfc-465cn.html](http://uint32t.blogspot.com/2008/06/linux-printing-brother-mfc-465cn.html)

he trobat aquesta web on hi diu com fer-ho

salut

---

### Post by xevi on 2008-07-22
Hola a tothom, 
moltes gràcies, he aconseguit que imprimeixi,
L'escànner però se'm segueix resistint. He provat amb les instruccions instal.lant el brscan2, però em dona error:
wh1@wh1-desktop:~$ dpkg -i brscan2-0.2.4-0.i386.deb
dpkg: Angeforderte Operation benötigt Superuser-Rechte
wh1@wh1-desktop:~$ sudo dpkg -i brscan2-0.2.4-0.i386.deb
[sudo] password for wh1: 
dpkg: Fehler beim Bearbeiten von brscan2-0.2.4-0.i386.deb (--install):
 Kann auf das Archiv nicht zugreifen: No such file or directory
Fehler traten auf beim Bearbeiten von:
 brscan2-0.2.4-0.i386.deb
A partir d'aquest moment no puc segur.
L'Xsane no em troba l'escànner, òbviament.

moltes gràcies de nou.
Xevi

---

### Post by papapep on 2008-07-22
Ostres Xevi, intentar resoldre el tema amb els missatges del sistema en alemany és una mica heavy, què vols que et digui....

Per cert, "Kann auf das Archiv nicht zugreifen: No such file or directory" entenc que deu ser que no li dius correctament el lloc on ha de trobar el fitxer brscan(etc) que vols instal·lar.

---

### Post by xevi on 2008-07-22
Hola de nou, 
disculpeu, no he caigut en el detall
us adjunto l'error novament.
Val a dir que instal.lat el controlador segons m'indicàveu, però crec entendre que no el troba?
Ho sento no fa gens que remeno amb Linux i em costa bellugar-m'hi.
L'error:
wh1@wh1-desktop:~$ sudo dpkg -i brscan2-0.2.4-0.i386.deb
dpkg: s'ha produït un error en processar brscan2-0.2.4-0.i386.deb (--install):
 no es pot accedir a l'arxiu: No such file or directory
S'han trobat errors en processar:
 brscan2-0.2.4-0.i386.deb

El controlador crec s'ha instal.lat a usr/local/brother....

Gràcies
xevi

---

### Post by papapep on 2008-07-22
> no es pot accedir a l'arxiu: No such file or directory

El que et deia abans, o no tens el fitxer que intentes instal·lar, o no el tens al directori des d'on executes la ordre. Si no li dius exactament, el dpkg no sap on trobar-lo.

---

### Post by enricXIII on 2008-07-22
A veure xevi (aclareixo: soc el morfeo99 que he cambiat).
Mira amb el sinaptic cercant el brscan2, si el tens instalat o no. Si esta instalat,quan et surti en la cerca, el "quadradet" que te a l'esquerra estarà de color verd, si no ho està, instal-lal. ( jo de terminal vaig molt justet,jeje..)
Encara et quedarà, en cas de que no et detecti automàticament l'escàner, un parell de cosetes per fer desde terminal.

Entra a terminal i posa (per saber el Vendor id i producte id de l'escàner):

lsusb

Entre altres, et sortirà una linia que diu alguna cosa com:

Bus 001 Device 003: ID 04f9:01ec Brother Industries, Ltd

Anota la numeracio que et surti a tu, en el meu cas pots veure que es: 04f9 i 01ec

Escriu al terminal:

sudo gedit /etc/udev/rules.d/45-libsane.rules

S'obrirà un arxiu en blanc a on has de posar:

# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01ec", MODE="666", GROUP="scanner"
LABEL="libsane_rules_end"

ATENCIÒ: substitueix el model d'impressora que jo he posat (DCP-115C) per el teu! i el id vendor (049f) i el id product (01ec) per les que tens anotades anteriorment. 

Desa el fitxer i ja pots reiniciar l'ordinador. Et detectarà l'escàner amb l'xsane.. o plego!! JAJAJA! 

Ah! fes tot això amb l'impressora en dollada.
Amb aquests passos hauria de rutllar qualsevol model de brother.
Perdoneu si m'he enrotllat molt o no ha quedat prou clar com fer-ho, estic obert a qualsevol suggeriment.

---

### Post by enricXIII on 2008-07-22
A veure xevi (aclareixo: soc el morfeo99 que he cambiat).
Mira amb el sinaptic cercant el brscan2, si el tens instalat o no. Si esta instalat,quan et surti en la cerca, el "quadradet" que te a l'esquerra estarà de color verd, si no ho està, instal-lal. ( jo de terminal vaig molt justet,jeje..)
Encara et quedarà, en cas de que no et detecti automàticament l'escàner, un parell de cosetes per fer desde terminal.

Entra a terminal i posa (per saber el Vendor id i producte id de l'escàner):

lsusb

Entre altres, et sortirà una linia que diu alguna cosa com:

Bus 001 Device 003: ID 04f9:01ec Brother Industries, Ltd

Anota la numeracio que et surti a tu, en el meu cas pots veure que es: 04f9 i 01ec

Escriu al terminal:

sudo gedit /etc/udev/rules.d/45-libsane.rules

S'obrirà un arxiu en blanc a on has de posar:

# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01ec", MODE="666", GROUP="scanner"
LABEL="libsane_rules_end"

ATENCIÒ: substitueix el model d'impressora que jo he posat (DCP-115C) per el teu! i el id vendor (049f) i el id product (01ec) per les que tens anotades anteriorment. 

Desa el fitxer i ja pots reiniciar l'ordinador. Et detectarà l'escàner amb l'xsane.. o plego!! JAJAJA! 

Ah! fes tot això amb l'impressora en dollada.
Amb aquests passos hauria de rutllar qualsevol model de brother.
Perdoneu si m'he enrotllat molt o no ha quedat prou clar com fer-ho, estic obert a qualsevol suggeriment.

---

### Post by xevi on 2008-07-23
Hola, 
gràcies EnricXIII he pogut finalment fer funcionar l'scanner.
Solament una qüestió més, Ho he pogut fer seguint les teves indicacions i connectant la impressora en local amb USB.
Tinc alguna possibilitat de fer-la anar en xarxa?
La impressió em funciona correctament en xarxa però l'scanner, no.
He provat novament amb les indicacions anteriors, tinc instal.lat el brscan2 (segons el synaptic) però em dona el mateix error.
La veritat és que no sé com indicar-li a l'ordre la local.lització de l'arxiu. 
Disculpeu, ben segur són obvietats, però són un món desconeguts per mi.

Interpreto que la localització (de quan vaig descarregar i instal.lar és usr/local/Brother/sane/) però desconec com indicar-li a l*ordre d'instal.lació.
Moltes gràcies
Xevi

---

### Post by enricXIII on 2008-07-23
Segur que es pot, però com que mai he necessitat fer-ho...no se com continuar. El que tinc clarissim es que si et rulla en xarxa per imprimir, l'scaneig també es pot fer!
Si tinc alguna solució ho faré saber per aqui...

---

### Post by papapep on 2008-07-23
Fes a un terminal:

```
brsaneconfig2 -a name=MFC465C-SCANNER model=MFC-465C IP=111.222.333.444
```

Sent 111.222.333.444, la ip del teu multifunció.

---

### Post by xevi on 2008-07-25
Hola, 
gràcies Pep. He provat amb el text que m'has indicat. Imagino que l'IP (Host) és el que trobo a la configuració de la impressora (una cosa així com 192.168.1.3 perüo sempre m'apareix el mateix missatge d'error.

wh1@wh1-desktop:~$ brsaneconfig2 -a name=MFC465CN-SCANNER model=MFC-465CN IP=192.168.1.3
Invalid IP address or NODENAME

Solament he afegit la "N" del model de la màquina i he provat amb totes les Ip que he trobat.

Ben segur em cal un manual de principiant, però acaba sent esgotador.

moltes gràcies
Xevi

---

### Post by papapep on 2008-07-25
> Invalid IP address or NODENAME

T'està dient que un d'aquests dos valors no és correcte. Assegura't quin nom té (NODENAME) el dispositiu de cara a la xarxa, i la ip, i fica-ho correctament a l'ordre que et vaig indicar. No té més secret, en teoria, aquest tema.

---

### Post by xevi on 2008-07-25
Hola Pep, 
disculpa, per que haig de sembla estúpid però no me n'ensurto.
El nom ha de coincidir amb el que el gestor d'impressores té (MFC-465CN), tot i que la impressora tot i estar enxufada al rooter, m'apareix no a la xarxa, si no com si pengès en local d'un dels ordinadors. Malgrat estar en xarxa.
En les configuracions de la impressora a "connexió" m'apareix aquest host (que intepreto per la seva forma és la IP)
Així, nom i IP haurien de ser correctes, no?
Veig que el salt a Linux està resultant massa al buit.
Moltes, moltes gràcies
Xevi

---


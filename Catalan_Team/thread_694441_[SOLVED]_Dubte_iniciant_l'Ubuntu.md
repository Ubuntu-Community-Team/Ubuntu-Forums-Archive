---
title: "[SOLVED] Dubte iniciant l'Ubuntu"
date: 2008-02-12
forum: Catalan Team
---

### Post by Joan Marc on 2008-02-12
Hola,
Llegint aquest fragment del fil [http://ubuntuforums.org/showthread.php?t=386821&page=3](http://ubuntuforums.org/showthread.php?t=386821&page=3) , m'ha sorgit un dubte
> **eselma said:**
> 
Un suggeriment: quan parles de que es pot fer la mida de la partició d'intercanvi més petita que la RAM o fins i tot suprimir-la, crec que els ordinadors portàtils bolquen la imatge de rearrencada precisament a aquesta partició; això caldria advertir-ho, crec.

El cas és que quan arrenco l'Ubuntu des de les opcions del Grub, la pantalla queda tota negra, i al cap d'un instants apareix la pantalla que em surt abans del Grub (concretament la de la casa ASUS) un pel esborrada i a línies, i després em surt la pantalla per iniciar sessió de l'Ubuntu.
És normal això? Té relació amb el que ha dit l'eselma?
Per què tingueu més informació, la meva Swap té uns 3Gb, i la meva RAM és de 2Gb.

Gràcies.

PD: No era la meva intenció molestar a ningú amb el meu off-tòpic total del fil *wiki i tutorial de instal·lació de ubuntu en català*. Perdoneu-me.

---

### Post by CarlesOriol on 2008-02-12
Passa en algunes gràfiques. Concretament en ati i intel.

Pots cercar de jugar amb els paràmetres d'inici del **/boot/grub/menu.lst** 
Als carregadors trobaràs línies com: kernel		

/boot/vmlinuz-2.6.22-14-generic root=UUID=bab38601-cbc8-4b96-87cb-2136c2668b1b ro **quiet** **splash** 

Si elimines el **quiet** i el **splash** com a mínim veuràs el que està fent. (És emprenyador sobretot quan comprova el disc que triga molta estona i dona la sensació que s'ha penjat.)

Una altra opció més guapa és anar fent proves amb paciència afegint **vga=unnombre** però això ja depèn de la gràfica que tinguis. (aquí cal cercar els valors de resolució adequats a la teva gràfica)

Has de tenir en compte que **qualsevol actualització del kernel et tornarà a posar els valors predeterminats** i hauràs de tornar a modificar-ho.

------------------------

Reflexió: És necessaria una swap de 3 Gb?

Per cert... passa pel fil de benvinguda a presentar-te que així sempre és més fàcil de saber qui és qui.

---

### Post by eselma on 2008-02-12
> **Joan Marc said:**
> Hola,
Llegint aquest fragment del fil [http://ubuntuforums.org/showthread.php?t=386821&page=3](http://ubuntuforums.org/showthread.php?t=386821&page=3) , m'ha sorgit un dubte

[COLOR="DarkGreen"]Originally Posted by **eselma** 
Un suggeriment: quan parles de que es pot fer la mida de la partició d'intercanvi més petita que la RAM o fins i tot suprimir-la, crec que els ordinadors portàtils bolquen la imatge de rearrencada precisament a aquesta partició; això caldria advertir-ho, crec.[/COLOR]

El cas és que quan arrenco l'Ubuntu des de les opcions del Grub, la pantalla queda tota negra, i al cap d'un instants apareix la pantalla que em surt abans del Grub (concretament la de la casa ASUS) un pel esborrada i a línies, i després em surt la pantalla per iniciar sessió de l'Ubuntu.
És normal això? Té relació amb el que ha dit l'eselma? Per què tingueu més informació, la meva Swap té uns 3Gb, i la meva RAM és de 2Gb. 

No, crec que no té cap relació; com diu l'Oriol, segurament són característiques de la tarja gràfica que encara conserva en memòria (pròpia o assignada a la tarja, no la RAM general dels sistema) restes de la pantalla anterior.

En aquell comentari em referia a que en activar el mode de "suspendre a disc" un ordinador portàtil (per estalviar bateria) i poder tornar a engegar en el punt en que estava. Lògicament pot ser necessària tanta quantitat de  *swap* com tinguessis a la RAM, i potser alguns kB de més. En el teu cas, 3 GB són més que suficients, i segurament excessius (si no et dediques a editar grans fitxers gràfics o video).

Quant a l'*off topi*c, tranquil, no has molestat a ningú; senzillament són normes de *netiquette* precisament adreçades a poder localitzar la informació més fàcilment i mantenir la coherència del fòrum. Estàs disculpat; una cosa que caracteritza aquest fòrum, pel que veig, és el "bon rotllo". Que duri!

---

### Post by Joan Marc on 2008-02-12
Gràcies per contestar.

CarlesOriol; Vols dir que no és una mica perillós que un principiant com jo remeni l'arxiu del Grub? Esque em fa una mica de respecte...

Què vols dir amb *veuràs el que està fent* si elimino **quiet splash**?

El **vga=unnombre** on ho he de posar? La meva gràfica és una Ati, i tinc una resolució de 1024x768. 

Pel que dius de la Swap de 3Gb, com que vaig llegir en alguns llocs que havia de ser el doble de la RAM instal·lada, però en alguns llocs deia que tampoc en calia tanta, dons vaig posar el que em va semblar :).

I per cert, ara em pasaré pel fil de benvinguda ;)

Eselma: Gràcies per l'explicació i pels ànims :)

---

### Post by papapep on 2008-02-12
El que estaria bé Joan Marc, és saber quina gràfica tens en concret.
Enganxa, si us plau, el que et surti fent:

```
lspci
```

---

### Post by Joan Marc on 2008-02-12
Aquí ho teniu:
```
gami@gami:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon X2300
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
```

Gràcies.

---

### Post by papapep on 2008-02-12
I quina versió de kernel fas servir??

```
uname -a
```

---

### Post by Joan Marc on 2008-02-12
Et poso el resultat:
```
gami@gami:~$ uname -a
Linux gami 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

Gràcies.

---

### Post by papapep on 2008-02-12
He estat buscant una mica i crec que si arrenques i pots arribar a veure l'escriptori, si executes l'opció "Controladors restringits", o alguna cosa semblant, que hauries de tenir al menú d'Administració se t'haurien de instal·lar els controladors correctes per a la teva gràfica.

---

### Post by Joan Marc on 2008-02-12
Sí, tens raó papapep.
He intal·lat els controladors d'ATI, però l'única cosa que ha canviat és que ara no apareix la pantalla d'ASUS distorsionada, sinó que és tot negre fins que surt la pantalla d'inciar sessió.
Bé, tampoc hi ha cap problema que sigui així, però sempre és més bonic que surti el que realment ha de sortir.
Hi ha solució per això?

---

### Post by papapep on 2008-02-12
Doncs no ho se, però com que és un tema purament estètic, doncs tampoc em preocuparia massa. A mi personalment sempre m'ha agradat més anar veient com carregava les diferents parts del sistema (que és el que et deia el Carles de treure el quiet i splash de la línia d'arrencada del /boot/grup/menu.lst).

---

### Post by lluisanunez on 2008-02-12
> **Joan Marc said:**
> 
Què vols dir amb *veuràs el que està fent* si elimino **quiet splash**?

Si elimines la comanda *quiet splash* veuràs els missatges que van apareixent del que s'està carregant: detecció de la xarxa, càrrega de drivers i de serveis... a mi m'agrada més així, abans linux sempre carregava donant tots els missatges, i més d'una vegada he detectat canvis i això pot ser útil en cas de problemes. Més encara si et fa esperar amb la pantalla negra...

---

### Post by Joan Marc on 2008-02-12
D'acord, ho provaré doncs!

Gràcies a tots!

---

### Post by Joan Marc on 2008-02-12
Un petit problema, quan vull guardar el menu.lst, em surt l'advertència adjunta que no em deixa guardar.
Què faig?

---

### Post by papapep on 2008-02-12
Doncs executar la ordre o programa que has fet servir per editar el fitxer a fi de fer-ho com a administrador.

Si ho has fet des de l'entorn gràfic, fes Alt + F2 i fica dins la finestra que et sortira **gksudo nom_de _l'editor**.

Si ho has fet des d'el terminal:

```
sudo nano /boot/grub/menu.lst
```

Per cert, FES UNA CÒPIA DEL FITXER ABANS D'EDITAR-LO!!!!

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

---

### Post by Joan Marc on 2008-02-12
Gràcies, jasta.
Els missatges van tan de pressa que se'm faria molt dificil detectar si alguna cosa no es carrega bé! xD

Bona nit.

---

### Post by ilku on 2008-02-15
Mirat aquest link per veure allo de vga=numero en el teu cas em sembla que és 791
[http://ubuntuforums.org/showthread.php?t=593507&highlight=vga%3D791]("http://ubuntuforums.org/showthread.php?t=593507&highlight=vga%3D791")

Potser aixo t'ajuda

---


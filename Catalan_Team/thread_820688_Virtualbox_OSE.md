---
title: "Virtualbox OSE"
date: 2008-06-06
forum: Catalan Team
---

### Post by lFossil on 2008-06-06
Bones, ja fa temps que vaig darrera de fer funcionar el virtualbox però no ho he pogut aconseguir d'ençà que vaig començar en l'ubuntu. Vaig tenir bastants problemes, vaig seguir tot un post llarguíssim però al final no hi vaig solucionar res.
Ara he pogut solucionar alguns problemes que tenia per acabar d'actualitzar de Gutsy a Hardy i he provat de fer funcionar el Virtualbox que se m'ha canviat i ara fica Virtualbox OSE i em surt una informació que abans no em sortia, quan l'inicio, [[IMG]http://img171.imageshack.us/img171/5691/capturavirtualboxavssj5.th.png[/IMG]]("[URL=http://img171.imageshack.us/my.php?image=capturavirtualboxavssj5.png)"]aquesta[/URL]
i després quan fico iniciar la màquina em surt [[IMG]http://img379.imageshack.us/img379/7174/capturavirtualboxerrorai7.th.png[/IMG]]("[URL=http://img379.imageshack.us/my.php?image=capturavirtualboxerrorai7.png)"]aquest[/URL] altre.
Algú en sap res?

Salut i gràcies!!

---

### Post by SiscoGarcia on 2008-06-06
lFossil, al menys a mi no em funcionen els enllaços que hi has posat; no sé ben bé quin és el problema però diria que és un tema de sintaxi, ho pots comprovar i, si és el cas, canviar-los?

Merci.

---

### Post by lFossil on 2008-06-06
Sí, aquí ho fico en ordre com havia dit abans:

[[IMG]http://img405.imageshack.us/img405/9496/capturavirtualboxavsxj1.th.png[/IMG]](http://img405.imageshack.us/my.php?image=capturavirtualboxavsxj1.png)

[[IMG]http://img524.imageshack.us/img524/3955/capturavirtualboxerrorlh3.th.png[/IMG]](http://img524.imageshack.us/my.php?image=capturavirtualboxerrorlh3.png)

---

### Post by papapep on 2008-06-06
Bàsicament, el problema sembla que sigui que allà on tinguessis tant la iso de les guest-additions com el fitxer .vdi de la màquina virtual, no són on el Virtualbox s'espera....

---

### Post by lFossil on 2008-06-07
Sí, i com ha d'estar?

---

### Post by papapep on 2008-06-07
> Sí, i com ha d'estar?

No entenc la pregunta. El que et diu el Virtualbox és que no tens el fitxer on li vas dir que seria quan vas crear la màquina virtual i, per tant, si no el troba no pot arrencar. El lloc en concret, tu sabràs :-)

---

### Post by lFossil on 2008-06-07
Bé, he provat de crear una altra màquina virtual mirant l'antic post que vaig  posar sobre el virtualbox però em surt el mateix que abans, només un avís per això.
Ara ja només em surt això:
[[IMG]http://img372.imageshack.us/img372/2905/capturavirtualboxerrorqq8.th.png[/IMG]](http://img372.imageshack.us/my.php?image=capturavirtualboxerrorqq8.png)

---

### Post by papapep on 2008-06-07
Enganxa el que et surti en fer a un terminal:

```
uname -a
```

i també:

```
aptitude search virtualbox
```

---

### Post by lFossil on 2008-06-07
Primer:

jasiel@jasiel-laptop:~$ uname -a
Linux jasiel-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

Després:

jasiel@jasiel-laptop:~$ aptitude search virtualbox
c   virtualbox                      - innotek VirtualBox                        
i   virtualbox-ose                  - x86 virtualization solution - binaries    
p   virtualbox-ose-dbg              - x86 virtualization solution - debugging sy
v   virtualbox-ose-guest-modules    -                                           
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-2. - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-38 - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-ge - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-op - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-rt - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-se - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-modules-vi - virtualbox-ose-guest module for linux-imag
p   virtualbox-ose-guest-source     - x86 virtualization solution - guest additi
p   virtualbox-ose-guest-utils      - x86 virtualization solution - guest utilit
v   virtualbox-ose-modules          -                                           
i A virtualbox-ose-modules-2.6.22-1 - virtualbox-ose modules for linux-image-2.6
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose modules for linux-image-2.6
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose modules for linux-image-2.6
p   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.
p   virtualbox-ose-modules-386      - virtualbox-ose module for linux-image-386 
p   virtualbox-ose-modules-generic  - virtualbox-ose module for linux-image-gene
p   virtualbox-ose-modules-openvz   - virtualbox-ose module for linux-image-open
p   virtualbox-ose-modules-rt       - virtualbox-ose module for linux-image-rt  
p   virtualbox-ose-modules-server   - virtualbox-ose module for linux-image-serv
p   virtualbox-ose-modules-virtual  - virtualbox-ose module for linux-image-virt
p   virtualbox-ose-source           - x86 virtualization solution - kernel modul
v   virtualbox-source               -                                           
jasiel@jasiel-laptop:~$

---

### Post by papapep on 2008-06-07
Com que, si molt no m'equivoco, el paquets de mòduls per a la versió 2.6.24-18 encara no s'han publicat, hauràs d'arrencar amb una versió anterior (bé, de fet, hauries d'arrencar amb la versió de la qual tens instal·lats els mòduls). O sigui, per explicar-me millor, que el Virtualbox es queixa que no troba els mòduls de la versió de kernel que estàs fent servir que li permetrien executar-se.

Com ho pots fer això?
Doncs primer has de saber quina versió del paquet *virtualbox-ose-modules* tens instal·lada. Al llistat que has passat just falta el número final (entenc que deus tenir instal·lada la .17-generic, però). Si maximitzes la finestra del terminal i tornes a fer:

```
sudo aptitude search virtualbox
```

segur que podràs veure tot el nom del paquet (o això espero :-))

Cal, també, modificar un fitxer per a poder triar a l'arrencada quin kernel vols fer servir, sinó l'Ubuntu fa servir la última versió instal·lada i aleshores no podràs fer servir el Virtualbox.

Enganxa el contingut del fitxer **/boot/grub/menu.lst**, si us plau. Si és massa gran, passa'l com a adjunt.

---

### Post by lFossil on 2008-06-07
Refent al del principi, no hem surt cap nombre al final.
Adjunto això per a que ho vegis tu mateix.

[[IMG]http://img361.imageshack.us/img361/483/capturaob1.th.png[/IMG]](http://img361.imageshack.us/my.php?image=capturaob1.png)

Aquí tens el /boot/grub/menu.lst
Ho sento no he sabut adjuntar :

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash locale=ca_ES

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro quiet splash locale=ca_ES
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro quiet splash locale=ca_ES
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro quiet splash locale=ca_ES
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.17-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro quiet splash locale=ca_ES
initrd		/boot/initrd.img-2.6.17-12-generic
quiet

title		Ubuntu 8.04, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu 8.04, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro quiet splash locale=ca_ES
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 8.04, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=8c58112b-6ee6-4ca0-b9c1-3f61ba0bf0e5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by papapep on 2008-06-07
Doncs jo sí que el veig :-D
Tens instal·lat el paquet de mòduls de la versió 2.6.24-14-generic.

Anem a veure quins kernels tens instal·lats:

```
sudo aptitude search '~i'|grep linux-image
```

Per adjuntar l'únic que cal fer és crear un fitxer de text amb el contingut que es vol adjuntar, i buscar-lo clicant damunt el clip que hi ha a l'editor de posts (entre la cara somrient i la fletxa curvada a l'esquerra).

---

### Post by lFossil on 2008-06-07
Gràcies per l'instrucció:)
Aquí tens:

jasiel@jasiel-laptop:~$ sudo aptitude search '~i'|grep linux-image
[sudo] password for jasiel: 
i A linux-image-2.6.17-10-generic   - Linux kernel image for version 2.6.17 on x
i   linux-image-2.6.17-12-generic   - Linux kernel image for version 2.6.17 on x
i A linux-image-2.6.20-16-generic   - Linux kernel image for version 2.6.20 on x
i   linux-image-2.6.22-14-generic   - Linux kernel image for version 2.6.22 on x
i   linux-image-2.6.24-18-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-generic             - Generic Linux kernel image                
i A virtualbox-ose-modules-2.6.22-1 - virtualbox-ose modules for linux-image-2.6
jasiel@jasiel-laptop:~$

---

### Post by Diegstroyer on 2008-06-07
Has d'obrir les propietats generals de la màquina virtual i anar als dispositius CD/DVD i eliminar les guestadditions.iso de la llista de .isos per a ser muntades en el dispositiu, ja que les guestadditions han canviat en la versió dels repositoris d'ubuntu, que ara és OSE. 

També tindràs el problema dels kernels, ja que els kernels s'estan actualitzant molt depressa i els mòduls per al virtualbox van amb dos o tres dies de retard, t'aconsello instal·lar la versió privada anant a la pàgina i descarregant-la.

---

### Post by lFossil on 2008-06-10
Ja les he eliminat però em segueix passant el mateix.

Provare de fer això que dius de la versió privada

Salut¡¡

---

### Post by lFossil on 2008-06-10
He eliminat la viretualbox del afegeix/elimina i m'he descargat la versió 
sun  xVM Virtualbox i em dona el següent error quan inicio la màquina:

[[IMG]http://img176.imageshack.us/img176/4176/capturamaquinavirtualxpdo3.th.png[/IMG]](http://img176.imageshack.us/my.php?image=capturamaquinavirtualxpdo3.png)

---

### Post by Diegstroyer on 2008-06-11
Proba anant al synaptic i posant virtualbox, elimina totes les entrades de virtualbox i reinstal·la amb Gdebi.(després proba sudo dpkg -r virtualbox)

Quan estiguis instal·lant de nou,  et dirà de passar l'arxiu .vdi (que és la màquina virtual) al nou format, digues que sí i a veure que tal. (Has de tornar a ficar-te a usuaris i grups i tornar a afegir el teu usuari a vboxusers i reiniciar la sessió).

A veure que tal.

PROVA EL QUE DIU A SOTA PRIMER!

---

### Post by Diegstroyer on 2008-06-11
Mira també la seqüència  d'arrencada de la màquina virtual, a veure quins dispositius tens marcats!

Per cert, si estàs intentant instal·lar un SO nou, potser que no sigui capaç de llegir el dispositiu, canvia d'unitat en les preferències de VirtualBox i torna-ho a intentar, si et passa el mateix, fes una iso del CD i munta-la al la màquina virtual.

---

### Post by lFossil on 2008-06-11
i reinstal·la amb Gdebi.?¿?¿

Què vols dir?

---

### Post by CarlesOriol on 2008-06-11
Que facis doble clic damunt.

---

### Post by lFossil on 2008-06-12
He fet el que m'has dit, he anat al gestor de paquets synaptic i he eliminat el virtualbox i després l'he toornat a marcar per a instal·lar-lo altre cop.
No m'ha dit res d'aixo de l'arxiu .vdi i quan he anat a fer 
sudo dpkg -r virtualbox m'ha aparegut això:


jasiel@jasiel-laptop:~$ sudo dpkg -r virtualbox
[sudo] password for jasiel: 
dpkg - avís: es descarta la petició de desinstal·lar virtualbox, del qual
 només els fitxers de configuració queden en el sistema. Useu --purge per
 a esborrar també aquests fitxers.
jasiel@jasiel-laptop:~$

---

### Post by lFossil on 2008-06-15
Alguna idea?   :confused:

---

### Post by Diegstroyer on 2008-06-17
Has de instal·lar el de la página web de Virtualbox:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Tria la versió per 8.04 que et correspongui i instal·la-ho, a veure que tal.

Tu t'estaves reinstal·lant la versió OSE desde el Synaptic.

---

### Post by lFossil on 2008-06-17
D'acord, he fet això que em dius però em torna a sortir el mateix quan inicio una maquina dins del virtualbox:

[[IMG]http://img403.imageshack.us/img403/8946/capturamaquinavirtualxppp4.th.png[/IMG]](http://img403.imageshack.us/my.php?image=capturamaquinavirtualxppp4.png)

---

### Post by oriolsbd on 2008-06-18
Hola.

Em sembla que, si et surt aquest missatge, vol dir que ja tens ben instal·lat el VirtualBox (si no, et sortirien els missatges del principi), però que en intentar iniciar el sistema des del disc dur que té assignat, no el troba apte per a arrancar cap sistema.

El fitxer ".vdi" que tens assignat a aquesta màquina virtual, ja hi té instal·lat algun sistema operatiu? Si no has mogut el fitxer ".vdi" entre diferents màquines virtuals, la pregunta equivalent seria: Has instal·lat ja el sistema operatiu en aquesta màquina virtual?

---

### Post by lFossil on 2008-06-18
No, no ho he fet, perquè em dona problemes.
No trobo la iso del cd que tinc amb el windows xp

---

### Post by oriolsbd on 2008-06-19
Doncs, per l'últim missatge que mostres, sembla que ja tens el Virtualbox preparat per a instal·lar un Sistema Operatiu.

Salut!

---

### Post by lFossil on 2008-06-19
Sí però no puc instal·lar el sistema operatiu perquè no trobo la iso del cd

---

### Post by Diegstroyer on 2008-06-19
Doncs donat un passeig per l'aMule... jejejeje. O millor, per un torrent...

---

### Post by lFossil on 2008-06-21
D'acord ho tindré en compte!! jeje ja ho provaré.

---

### Post by lFossil on 2008-07-09
EEEEi bones! Notícia, per fí he pogut fer anar el virtualbox!
Me passejat per l'emule com m'han dit i he obtingut una altra versió del windows xp, però crec que esta amb portuguès.
L'he iniciat pero em deia això:

Disco 0 de 5013 MB em Id 0 no barramento 0 em atapi [MBR]
  C: Partiçao1 [Desconhecida]      5005 MB < 5004 MB livres>
     Espaço naô particionado          8 MB



i clar no sé que fer

---

### Post by lFossil on 2008-07-09
Bé, si segueixo i clico a:

C: Partiçao1 [Desconhecida] 5005 MB < 5004 MB livres>

Em surt això:

Formatar a partiçao utilizando sistema de arquivos NTFS (rapido)

Formatar a partiçao utilizando sistema de arquivos FAT (rapido)

Formatar a partiçao utilizando sistema de arquivos NTFS

Formatar a partiçao utilizando sistema de arquivos FAT

Bé, algú sap que hauria de fer?
Gràcies per adelantat!!

---

### Post by oriolsbd on 2008-07-09
Hola.

Posa-li la primera opció (NTFS ràpid). Si et diu que no pot perquè el disc (que és un disc virtual) no ha estat mai particionat, utilitza la tercera opció (NTFS a seques).

Salut!

---

### Post by papapep on 2008-07-09
Em sap greu nois, però la manera d'instal·lar windows no forma part de l'objectiu d'aquest fòrum. Agrairé no feu posts al respecte.

---

### Post by lFossil on 2008-07-09
D'acord, ja m'apanyaré, gràcies de totes formes

---

### Post by lFossil on 2008-07-11
bones!, se m'ha aparegut un nou problema i és que no em carrega els usb (maldito windows), també m'agradaria compartir dades entre els dos sistemes operatius, tot i que he seguit els passos d'altres fils, l'únic que he pogut fer es crear la carpeta de en shared folders, però no trobo el terminal del guïndows, algú em pot tirar un cop de ma?

---

### Post by oriolsbd on 2008-07-11
Hola,

Per obrir un terminal de Windows, ves a "Inici->Executar" i executa "cmd". Ja tens un terminal.

La versió OSE de VirtualBox no permet utilitzar USB dins les màquines virtuals. Per a fer-ho, hauries de tenir instal·lada la versió completa (que no és lliure però sí gratuïta).

A més, per tal que funcioni l'USB amb VirtualBox a Ubuntu, en principi has d'editar el fitxer /etc/init.d/mountdevsubfs.sh:
sudo gedit /etc/init.d/mountdevsubfs.sh

I canviar les línies:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Per:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

És a dir, treure la "parrilla" de l'inici de les línies. De tota manera, jo ho he fet i mai no m'ha acabat funcionant... :-(
Després has de reiniciar Ubuntu.

Tens l'explicació completa aquí:
[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html)

A veure si tu tens més sort que jo. :-)

Salut!

---

### Post by dafaktor on 2008-07-12
Ei, acabo de publicar una entrada al meu blog on explico com he aconseguit que els usb funcionin...

Per si us serveix: [http://blogdenfaktor.blogspot.com/2008/07/ports-usb-en-virtualbox-i-hardy-heron.html](http://blogdenfaktor.blogspot.com/2008/07/ports-usb-en-virtualbox-i-hardy-heron.html)

---

### Post by lFossil on 2008-07-14
Una cosa, ja no tinc el virtualbox OSE, tinc el Sun xVM Virtualbox, és el mateix, o canvia la cosa?:confused:
Merci!

---

### Post by oriolsbd on 2008-07-15
Aquesta és la versió completa (no del tot alliberada, encara que sí gratuïta) amb la qual pots fer el que diu en Dafaktor per tal d'utilitzar USB a la màquina virtual. Fa pocs mesos que Sun ha comprat Virtualbox.

Salut!

---

### Post by lFossil on 2008-07-17
Hola nois, he resolt el tema dels usb gràcies al blog d'en d'afaktor, no obstant segueixo intentant el tema de compartir dades entre ubuntu i w xp.
He seguit els passos en aquest [fil]("http://ubuntuforums.org/showthread.php?t=705171&highlight=virtualbox")

M'he quedat a la part de ficar al terminal de windows 
net use x: \\vboxsvr\compartida
però em surt això: 
[URL=http://img399.imageshack.us/my.php?image=capturawxpsestexecutantpi5.png][IMG]http://img399.imageshack.us/img399/8554/capturawxpsestexecutantpi5.th.png[/IMG][/URL

De totes formes no crec haver creat bé la carpeta al shared folders.

---

### Post by lFossil on 2008-07-17
Hola nois, he resolt el tema dels usb gràcies al blog d'en d'afaktor, no obstant segueixo intentant el tema de compartir dades entre ubuntu i w xp.
He seguit els passos en aquest [fil]("http://ubuntuforums.org/showthread.php?t=705171&highlight=virtualbox")

M'he quedat a la part de ficar al terminal de windows 
net use x: \\vboxsvr\compartida
però em surt això: 
[[IMG]http://img399.imageshack.us/img399/8554/capturawxpsestexecutantpi5.th.png[/IMG]](http://img399.imageshack.us/my.php?image=capturawxpsestexecutantpi5.png)

De totes formes no crec haver creat bé la carpeta al shared folders.

---

### Post by oriolsbd on 2008-07-17
Hola, has instal·lat les Guest Additions? Suposo que sí, però no les veig executant a la barra de tasques. 

Apart d'això, com has definit en la màquina principal la carpeta compartida? S'ha de fer a l'apartat "Carpetes Compartides" de la definició de la màquina virtual en el Virtualbox, i com a nom de recurs li has de posar "dades_compartides" (que és com has posat en la comanda "net use").

Salut!

---

### Post by Daerun on 2008-07-18
Jo estic tenint el mateix problema, no aconsegueixo que el finestres del virtualbox em trobi la carpeta compartida. He trobat aquest blog

[http://tuxlink.wordpress.com/2008/01/06/compartir-carpetas-virtualbox-ubuntu-graficamente/](http://tuxlink.wordpress.com/2008/01/06/compartir-carpetas-virtualbox-ubuntu-graficamente/)


on expliquen la manera de fer-ho a Hardy, ja que segons sembla, la compartició de carpetes és diferent a versions prèvies,i el procediment és aquest: [http://tuxlink.wordpress.com/2008/05/09/compartir-carpetas-en-ubuntu-804/](http://tuxlink.wordpress.com/2008/05/09/compartir-carpetas-en-ubuntu-804/).

Si realment és això el que cal fer, en el meu cas tinc un problema, ja que diu que el primer pas és anar al menú Sistema > Administració > Carpetes compartides.... però aquest menú no existeix! (o jo no el tinc).

---

### Post by oriolsbd on 2008-07-18
No s'ha de configurar a través de la carpeta, sinó a través del propi VirtualBox. He fet una captura de pantalla de com ho tinc jo configurat:

[IMG]http://lh5.ggpht.com/oriolsbd/SIDcVB1MYkI/AAAAAAAAChY/92c4BMpWl9Y/Captura.png?imgmax=800[/IMG]

Per accedir des de la màquina virtual Windows a les meves dues carpetes que hi he compartit, he de fer:
net use x: \\vboxsvr\Fitxers
net use z: \\vboxsvr\Instalables

Les carpetes que es comparteixen per a una màquina virtual només les pot veure aquesta. O sigui, s'han de configurar per a cada màquina virtual.

Salut!

---

### Post by Daerun on 2008-07-18
Bé, doncs m'oblido del menú aquell :P Però el problema segueix sent el mateix:com li passa a en Fossil, la màquina virtual no detecta les carpetes compartides.

---

### Post by patrickfromspain on 2008-07-19
Jo aquest ultim cop tambe he tingut problemes amb les carpetes compartides a virtualbox, hem passava exactament el mateix. El curios es que reinstal·lant els guest additions ho he solucionat, curios.

salut

---

### Post by Miquel Ubuntero on 2008-07-19
Bones.
Jo tambe hem vaig quedar encallat en el punt que es fa servir el comando "net use ..." A les hores vaig descobrir que aquest pas tambe es podia fer d'una altre manera. Anant a "Mi PC, clic al boto dreta i fen servir "Conectar a Unidad de Red". S'explica amb molt detall (graficament) en aquest link (al apartat num 9): [http://tuxlink.wordpress.com/2008/01/06/compartir-carpetas-virtualbox-ubuntu-graficamente/](http://tuxlink.wordpress.com/2008/01/06/compartir-carpetas-virtualbox-ubuntu-graficamente/)

A mi hem va solventar el tema, espero a vosaltres tambe.

salut!

---

### Post by Daerun on 2008-07-19
Jo ho he intentat de les dues maneres, amb el net use, i gràficament amb "Conectar a unidad de red", però el problema és que, en el primer cas, em dona el mateix error que a en Fossil, i en el segon, allà on hauria d'aparèixer la carpeta compartida, a l'apartat "VirtuaBox Shared Folders", no hi apareix res, és buit.

---

### Post by Daerun on 2008-07-19
He trobat enun altre fòrum una possible solució: desinstal·lar les GuestAdditions que venen "de sèrie" amb el VirtualBox, i instal·lar la versió 1.60 que es pot baixar aqui:

[http://www.virtualbox.de/download/1.6.0/VBoxGuestAdditions_1.6.0.iso](http://www.virtualbox.de/download/1.6.0/VBoxGuestAdditions_1.6.0.iso)

A mi m'ha funcionat :grin:

---

### Post by lFossil on 2008-07-25
Ja ho he sol·lucionat, instal·lant les GuestAdditions!!
Saluts a tos i gràcies!

---


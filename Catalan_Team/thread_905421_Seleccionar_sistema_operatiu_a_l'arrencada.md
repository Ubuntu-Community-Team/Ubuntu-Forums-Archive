---
title: "Seleccionar sistema operatiu a l'arrencada"
date: 2008-08-30
forum: Catalan Team
---

### Post by bolidoone on 2008-08-30
No me donat compte fins ara,quan inicio l'ordinador arranca directament ubuntu,no puc seleccionar Win Xp.

Tinc dos discs durs,un SATAII de 300 Gb. amb win Xp que funcionaba correctament,i despres,tinc un Ide de 60 Gb. on tinc instal.lat Ubuntu.

Ara quan inicio l'ordinador,arranca directament Ubuntu,que tindria que fer per poder seleccionar amb quin sistema vui arrancar,no utilitzo gaire Win Xp pero la meva tarja Avermedia Hybrid+fm pci nomes funciona amb Win i de vegades grabo algunes coses del TDT.(M'agrada tenir les carreres de les motos grabades :))

---

### Post by papapep on 2008-08-30
Si només és per la placa aquesta que esmentes, crec que pots enviar a pastar fang el win:

[http://zonabuologica.wordpress.com/2007/12/04/configurar-avermedia-avertv-hybrid-fm-pci-chip-saa7134/](http://zonabuologica.wordpress.com/2007/12/04/configurar-avermedia-avertv-hybrid-fm-pci-chip-saa7134/)

Pel tema de recuperar l'entrada del win, enganxa aquí:

- El contingut de /boot/grub/menu.lst.
- El resultat de fer:

```
sudo cfdisk -P s /dev/sda
```

i 

```
sudo cfdisk -P s /dev/sdb
```

(suposant que **sda** i **sdb** siguin els teus dos discs durs)

---

### Post by bolidoone on 2008-08-30
He intentat fer que funciones AverTV,pero la explicacio que donen al blog es per un sistema de 32 bits,segueixos els pasos pero no em surten les mateixes coses,seria millor fer un altre fil per AverTV.

Respecte al tema dels discs durs,et diu aixo:
Tabla de particiones para /dev/sda

               Primer     Último
 Nº Tipo       Sector      Sector   Despl.  Longitud  Tipo sist. fich. (ID) Indicad.
-- ------- ----------- ----------- ------ ----------- -------------------- ----
 1 Primari           0   586083329     63   586083330 HPFS/NTFS (07)       Ninguno
   Pri/Lóg   586083330   586099394      0       16065 Espacio libre        Ninguno

Tabla de particiones para /dev/sdb

               Primer     Último
 Nº Tipo       Sector      Sector   Despl.  Longitud  Tipo sist. fich. (ID) Indicad.
-- ------- ----------- ----------- ------ ----------- -------------------- ----
 1 Primari           0   112358609     63   112358610 Linux (83)           Inicio
 2 Primari   112358610   117226304      0     4867695 Extended (05)        Ninguno
 5 Lógica   112358610   117226304     63     4867695 Linux swap / So (82) Ninguno

---

### Post by patrickfromspain on 2008-08-31
ens has de posar que hi tens al teu arxiu /boot/grub/menu.lst

salut

---

### Post by bolidoone on 2008-08-31
Com ho faig per mostrar-te el contingut d'aquest arxiu? amb un comand?

---

### Post by papapep on 2008-08-31
Fes Alt+F2, i a la finestreta que et sortirà, posa:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by bolidoone on 2008-08-31
el resultat es molt estes,se que hi ha alguna manera de reduir-ho,pero no ho se fer,t'ho poso tal cual i m'expliques com fer per no posar tantes linies altra vegada.



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
# defoptions=quiet splash

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b4e74711-9599-49d9-926a-290f7a853466 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b4e74711-9599-49d9-926a-290f7a853466 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by patrickfromspain on 2008-08-31
el resultat es el que es, tranquil. Una altra vegada, si ho prefereixes, pots posar [CO DE] al principi i [/CO DE] al final (sense l'espai en mig), pero poc mes pots fer. O enganxar un arxiu amb el que sigui.

Es possible que quan vas instal·lar l'ubuntu desconnectesis el disc dur que tenia el windows?

El problema esta en que el grub no sap que hi ha una particio o disc amb windows, per això no te l'ensenya.

Podries provar posant aixo al final de tot:

title		Windows 
root		(hd1,0)
savedefault
makeactive
chainloader	+1

a veure si funciona.

Salut

---

### Post by bolidoone on 2008-08-31
Queda una cosa aixi,pero no funciona:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=b4e74711-9599-49d9-926a-290f7a853466 ro

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
# defoptions=quiet splash

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b4e74711-9599-49d9-926a-290f7a853466 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b4e74711-9599-49d9-926a-290f7a853466 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows
root (hd1,0)
savedefault
makeactive
chainloader +1

---

### Post by papapep on 2008-08-31
> Queda una cosa aixi,pero no funciona:


No surt com a opció al Grub? o quan hi accedeixes no arrenca el windows..? cal que siguis més explícit...

---

### Post by bolidoone on 2008-08-31
no surt com a opcio a grub,quan engego,surt directament la carga de Ubuntu,a no ser que tingui que mantenir pulsada alguna tecla per poder accedir a la seleccio del sistema.

---

### Post by papapep on 2008-08-31
mmm....i quan apareix el menú de selecció del grub prement fletxa avall no pots anar fins l'opció de Windows??

---

### Post by bolidoone on 2008-08-31
Suposo que et referixes prement esc per entrar al menu,ho provo ara mateix.

---

### Post by bolidoone on 2008-08-31
Ok,si premo Esc i entro al menu,si que surt la opcio Windows,al premer esa opcio es queda la pantalla negra posan't Starting Up... pero es queda aixi,pot ser per haber modificat la linia en /boot/grub/menu.lst ??

---

### Post by Diegstroyer on 2008-08-31
Hola! salutacions!

sudo gedit /boot/grub/menu.lst

Per a que t'apareix-hi el menú de selecció sense prémer cap tecla has de cercar "hiddenmenu" i posar # davant seu, després busca "timeout" i treu-li el símbol # del davant (si hi ha el valor 0 després de timeout, canvia'l per 10).

Ara, quan arrenquis l'ordinador apareixerà el menú de selecció durant 10 segons :)

Per solucionar el problema de l'arrencada del disc de WinXP, pots anar provant el següent, tecleja "e" en el menú  de selecció de SO sobre l'entrada de WinXP, elimina la part que diu "savedefault".

Si no funciona aleshores, ves provant valors en hd(X,Y), si tens el WinXP en un altre disc, segurament has de fer anar el valor de X.

Quan estigui a casa et busco unes comandes que ajuden a resoldre el problema, però potser així o soluciones.

Els canvis que facis amb aquest mètode no són permanents, així que si ho soluciones hauràs de reeditar el menu.lst.

---

### Post by bolidoone on 2008-08-31
He fet algunes destroses en l'ordinador aquesta tarda,i vaig donar moltes voltes per configurar la tarja grafica aixi que... he desfet tot,he tornat a instalar-lo tot amb una mica mes de seny,ara t'explico,intentare no deixar-me res.

Tinc un Athlon 64bit i tinc windows a un disc dur sataII de 300 Gb.que acavo d'instalar un altre cop,despres,he tornat instalar Ubuntu 8.04. a un altre disc dur de 60 Gb IDE,ara arrenco l'ordinador,quan carga grub premo Esc y al menu nomes surten les tres opcion de Ubuntu,no surt windows ara he fet:
sudo gedit /boot/grub/menu.lst

per canviar les linies que m'has dit,i abans de tocar res,em surt aixo:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=f4dc4af4-45ab-40f8-9e0e-08d207b9eca0 ro

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
# defoptions=quiet splash

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f4dc4af4-45ab-40f8-9e0e-08d207b9eca0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f4dc4af4-45ab-40f8-9e0e-08d207b9eca0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Anava a fer els canvis pero les linies que em comentes las veig,pero ja tenen els simbols que em dius, Vaig be?

---

### Post by Diegstroyer on 2008-08-31
Doncs fes el que et comento més el que t'havien dit abans, es a dir, afegeix:

title		Microsoft Windows XP Professional
root		(hd1,0)
makeactive
chainloader	+1

I proba a veure si va, si no pots provar:

title		Microsoft Windows XP Professional
root		(hd0,1)
makeactive
chainloader	+1

Has d'anar variant els valors de hd, si ho soluciones comenta-ho, en breu et passo les ordres si això o resulta (recorda que ho has de fer prement e al menú de selecció del SO sobre l'entrada del WinXP).

---

### Post by bolidoone on 2008-08-31
una petita aclaracio,aquestes linies les poso amunt o sota de:

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Diegstroyer on 2008-08-31
A sota, si no et sortirà com si fos SO ubuntu,no passaria res pq això no afectaria en res al funcionament.

Pots posar:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Altres SO:
root

title		Microsoft Windows XP Professional
root		(hd1,0)
makeactive
chainloader	+1

---

### Post by bolidoone on 2008-08-31
Be,anem progresant,ara,quan engego,ja em surt el menu,puc seleccionar el sistema que vulgui,si no faig res en tres segons,inicia ubuntu,he provat a iniciar windows,es posa pantalla negra posan't al damunt starting up...
pero es queda aixi,llavors tinc que fer reset des de el botó de la torre,llavors,despres em diu que falta ntldr i tinc que seleccionar desde la bios el lloc des d'on vui que arranqui.
Suposo que al instal.lar ubuntu s'ha carregat ntldr de windows,puc fer alguna cosa per reparar-lo?

---

### Post by SiscoGarcia on 2008-08-31
Hola bolidoone, no sé com resoldre el problema que esmentes en l'última intervenció, però si encara tens l'opció d'arrencar d'ubuntu, encara no has modificat al teu menú d'arrencada ni el temps que triga a arrencar ni que et surti el menú. Com ja t'ha dit Diegstroyer has de fer el següent:

```
sudo gedit /boot/grub/menu.lst
```

Amb la qual cosa edites el menú i pots modificar-lo. Allà hi veuràs:

A la línia 17 hi diu "timeout 3", sense cometes. T'està dient que tens 3 segons per triar una opció d'arrencada. Pots canviar el 3 per qualsevol altre nombre de segons que vulguis.

A la línia 20 hi diu "hiddenmenu", sense cometes, que vol dir que el menú d'arrencada està amagat. Si comentes la línia (hi poses al davant # coixinet) fas que no la tingui en compte, és a dir, en aquest cas que no amagui el menú, per la qual cosa t'apareixerà sempre que no ho tornis a canviar, de manera que no hauràs de pitjar cap tecla per fer que surti.

Espero que et serveixi.

---

### Post by patrickfromspain on 2008-09-01
prova a posar aixo:

title Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
root (hd1,0)
makeactive
chainloader +1

salut

---

### Post by Diegstroyer on 2008-09-01
En les meves respostes et poso que apretis "e" sobre la selecció del SO WinXP. aleshores podràs editar les opcions d'arrencada de forma temporal, has d'anar variant els valors de hd fins que trobis on és el gestor d'arrencada de WinXP, que hauria d'estar en 1,0 o 1,1

Pots provar el que et comenten a dalt també si no ten en surts.

---

### Post by bolidoone on 2008-09-01
Bona nit a tothom,avui he començat a treballar i tinc menys temps per mirar aixo pero he provat varies coses i aquest son els resultats:

He provat a premer "e" sobre la seleccio de SO Win XP com en diu Diegstroyer,la forma inicial i es a hd 1.0 i arrencant aixi es que la pantalla a starting up i no fa res mes,al canviar a 1.1 em diu que no troba boot.

Llavors he fet el que em deia Patrickfromspain,he canviat les linies del fitxer:

i estaven aixi:
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Altres SO:
root

title Microsoft Windows XP Professional
root (hd1,0)
makeactive
chainloader +1

i les he deixades aixi:
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Altres SO:
root

title Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
root (hd1,0)
makeactive
chainloader +1

Llavors,em segueix sortint el grub de ubuntu,amb la opcio de altres SO,i al seleccionar win xp surt un altre cop starting up pero sota posa que falta ntldr i tinc que reiniciar.

suposo que li falta alguna cosa al win,que amb les linies que em comenta Patrickfromspain si que troba on hi es win,pero al faltar NTLDR no carrega,no se si vaig ben encaminat.

El mes futut es que win solament lo nesecito per la tarja avertv que per lo que veig als foros,ningu s'ensurt a ferla funcionar,si no fos per aixo,ja l'hauria enviat a pastar fang.

---

### Post by papapep on 2008-09-02
Al [segon post]("http://ubuntuforums.org/showpost.php?p=5694153&postcount=2") d'aquest fil ja et vaig comentar que creia que sí que hauria de funcionar (tot i que això seria tema per un altre fil). Has provat el que posa a l'enllaç que et vaig passar?

---

### Post by bolidoone on 2008-09-02
Si Papapep,lo que pasa que la meva placa porta un xip Phillips i es una mica mes futuda de fer-la funcionar,ho vaig provar,pero no funciona,he trobat uns altres que tenen el mateix problema.

---

### Post by papapep on 2008-09-02
Clar que porta un Phillips, porta aquest:

> 01:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

i aquest és el que esmenten a l'enllaç. Insisteixo, si vols mirar de fer-la funcionar obre un altre fil i mirem què es pot fer, ja que "sembla" que ha de funcionar sense gaire maldecaps.

---


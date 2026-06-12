---
title: "Bluetooth i Ubuntu Hardy 8.04"
date: 2008-05-13
forum: Catalan Team
---

### Post by pespin on 2008-05-13
Donçs bé, en el seu dia em passava una cosa semblant amb la gutsy, i és que tot i veure i emparellar el mòbil amb el dispositiu de l'ordinador no puc navegar-hi amb el nautilus.

Amb la gutsy es va arreglar instal·lant el paquet **gnome-vfs-obexftp**, però després d'actualitzar a Hardy avui he intentat fer-lo anar i torna a no funcionar. De fet, em munta el dispositiu com a disc dur al nautilus però en entrar al directori, aquest està buit.

Dins el suposat directori del mòvil al nautilus, hi intento crear un altre directori per a veure que passa i em surt l'error que adjunto al post. Bàsicament di uque no troba el directori, fet que fa pensar que definitivament hi ha quelcom que no està funcionant.

He estat llegint sobre el tema i crec que és degut al sistema de fitxers virtual que utilitza el gnome, que l'han canviat per un de més nou però que no té encara tantes extensions, com és el cas del obex.
Algú me'n pot fer cinc cèntims? Algú ha aconseguit navegar amb el nautilus per un dispositiu bluetooth a la hardy?


Per cert, enviar arxius de l'ordinador cap al mòbil funciona. Al intentar el camí invers el mòbil em dona un "Fallo de envio".


Gràcies per llegir/respondre.

---

### Post by pespin on 2008-05-13
Deixo aquí més informació:

$ dmesg | grep Bluetooth
[   62.366939] Bluetooth: Core ver 2.11
[   62.375453] Bluetooth: HCI device and connection manager initialized
[   62.375463] Bluetooth: HCI socket layer initialized
[   62.520792] Bluetooth: L2CAP ver 2.9
[   62.520805] Bluetooth: L2CAP socket layer initialized
[   62.579415] Bluetooth: RFCOMM socket layer initialized
[   62.579456] Bluetooth: RFCOMM TTY layer initialized
[   62.579461] Bluetooth: RFCOMM ver 1.8
[  326.655230] Bluetooth: HCI USB driver ver 2.9

$ lsusb | grep Bluetooth
Bus 001 Device 006: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter



Deixo una screen de l'error que em dóna el nautilus en intentar crear un fitxer de text pla dins el directori del dispositiu bluetooth (que per si no ho he dit abans, és un mòbil Nokia N70).

---

### Post by CarlesOriol on 2008-05-13
Ostres... això a mi no m'havia anat bé mai i ara per veure si et podia ajudar m'he connectat a meu telèfon fantàsticament bé.

Comentari: El gnome-vfs ha canviat en aquesta versió al gvfs. Prova de desinstalar-ho a veure si funciona.

---

### Post by pespin on 2008-05-13
> **CarlesOriol said:**
> Ostres... això a mi no m'havia anat bé mai i ara per veure si et podia ajudar m'he connectat a meu telèfon fantàsticament bé.

Comentari: El gnome-vfs ha canviat en aquesta versió al gvfs. Prova de desinstalar-ho a veure si funciona.

Estàs utilitzant Hardy? Quant a la connexió fantàstica et refereixes a poder navegader pel disc dur del mòbil amb el nautilus?

En intentar eliminar el gvfs m'esborra el nautilus diria:

```
Suprimeix els següents paquets:
blueman
gnome-volume-manager
gvfs-backends
nautilus
nautilus-cd-burner
nautilus-data
nautilus-sendto
nautilus-share
rhythmbox
ubuntu-desktop
```

---

### Post by papapep on 2008-05-13
> El gnome-vfs ha canviat en aquesta versió al gvfs. Prova de desinstalar-ho a veure si funciona

Tu a mi no m'enganyes, tu no ets en ratzinguer-Z, [tu ets en Marvin]("http://en.wikipedia.org/wiki/Marvin_the_Paranoid_Android")....kamikaze....

---

### Post by pespin on 2008-05-13
Informació relativa al problema:

[https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/211252](https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/211252)

[https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/211252/comments/9](https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/211252/comments/9)


Té pinta que passa amb els telefons que utilitzen Symbian (i el N70 diria que l'utilitza) :mad:


> 
Tu a mi no m'enganyes, tu no ets en ratzinguer-Z, tu ets en Marvin....kamikaze....
xDD Jo he pensat una cos semblant jjaja

---

### Post by CarlesOriol on 2008-05-14
No.... jo volia dir que desinstalessis el gnome-vfs si havies insta&#320;lat res.

No tinc cap telèfon amb symbian per provar-ho. Ho he fet amb ericssons.

---

### Post by papapep on 2008-05-14
> Ho he fet amb ericssons. 

No farè cap comentari al respecte. No faré cap comentari al respecte. No faré cap comentari al respecte....

---

### Post by pespin on 2008-05-14
> **CarlesOriol said:**
> No.... jo volia dir que desinstalessis el gnome-vfs si havies insta&#320;lat res.


No hi ha cap paquet que sigui "gnome-vfs" en si, suposo que et deus referir al "gnome-vfs-obexftp". Aquest ja el tinc desinstal·lat a veure si així funcionava, i res de res, segueix passant el mateix.


```
$ sudo aptitude search gnome-vfs
p   gnome-vfs-obexftp                                 - GNOME VFS module for OBEX FTP                               
i   libgnome-vfs2.0-cil                               - CLI binding for GnomeVFS 2.20                               
p   libgnome-vfsmm-2.6-1c2a                           - C++ wrappers for GnomeVFS (shared library)                  
p   libgnome-vfsmm-2.6-dev                            - C++ wrappers for GnomeVFS (development files)               
p   libgnome-vfsmm-2.6-doc                            - C++ wrappers for GnomeVFS (documentation) 
```

---

### Post by jaume69 on 2008-05-14
[QUOTE="pespin"]Per cert, enviar arxius de l'ordinador cap al mòbil funciona. Al intentar el camí invers el mòbil em dona un "Fallo de envio".
[/QUOTE]

Jo tinc instal.lats aquests paquets i em funciona bé.
Per navegar en els arxius del mòbil desde Nautilus també ho podia fer però no podia obrir les imatges.deia que l'arxiu no contenia res.
(Vaig provar enviar fotos desde el mòbil al ordinador i no m'ho feia o costava molt..,sense el paquet Bluetooth de Compartir Arxius Bluet.)

P.D.El meu Bluetooth és USB.

---

### Post by pespin on 2008-05-14
També ho havia provat amb el programa que comentes i res de res.


Pel que he llegit hi ha 2 erros separats:

1- No poder enviar del mòbil a l'ordinador. Això passa per error del bluez-utils amb dispositius que utilitzen Symbian.

2- No poder accedir als arxius amb el nautilus. Al Launchpad he vist un que ha posat una screenshot i li passava el mateix. El directori que apunta al dispositiu bluetooth mitjançant obex està buit.

---

### Post by eselma on 2008-05-15
> **CarlesOriol said:**
> No tinc cap telèfon amb symbian per provar-ho. Ho he fet amb ericssons.

Abans (fa uns anys) Ericsson usava Symbian, crec que va ser el primer a fer-ho. Symbian és el S. O. de 32 bit que usa el meu antic i fidel Psion.

---


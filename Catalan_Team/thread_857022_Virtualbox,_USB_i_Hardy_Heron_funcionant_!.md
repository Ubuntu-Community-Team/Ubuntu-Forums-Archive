---
title: "Virtualbox, USB i Hardy Heron: funcionant !"
date: 2008-07-12
forum: Catalan Team
---

### Post by dafaktor on 2008-07-12
Hola companys,

fa temps que intento que els usb funcionin en un XP virtual executant el Virtualbox en la Hardy Heron.

Per fi ho he aconseguit i he fet una entrada al meu blog.:lolflag:

Si algú té aquests mateixos problemes, podeu probar els quatre passos que jo he seguit i estaria molt bé que confirmessiu que a vosaltres també us ha anat bé.

Apa, l'adreça de l'entrada del meu blog és: [http://blogdenfaktor.blogspot.com/2008/07/ports-usb-en-virtualbox-i-hardy-heron.html](http://blogdenfaktor.blogspot.com/2008/07/ports-usb-en-virtualbox-i-hardy-heron.html)

Siau !!

---

### Post by oriolsbd on 2008-07-12
Ei, m'ha funcionat!!! :-)

Fa molt temps que hi anava al darrere. De moment ho he provat amb un pendrive i em funciona. Ara començaré amb un PocketPC que tinc, i algun altre dispositiu.

Moltes gràcies.

Per cert, un comentari respecte de l'entrada al teu blog. En les línies que s'han d'afegir als diferents fitxers de configuració, hi falten els canvis de línia. :-)
Són importants, perquè si no, no funciona.

Quan es fa "sudo gedit /etc/init.d/mountdevsubfs.sh", les línies que cal "descomentar" són:

```
mkdir -p /dev/bus/usb/.usbfs
domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
```

Quan es fa "sudo gedit /etc/udev/rules.d/40-permissions.rules", les línies que haurien de quedar on tu indiques són:

```
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
     ,GROUP="vboxusers", MODE="0660", GROUP="dialout" 
LABEL="usb_serial_end"
```

I, en el fitxer "/etc/fstab", les línies a afegir són:

```
#USB virtualbox
usbfs /proc/bus/usb usbfs devgid=125,devmode=666 0 0
```

Per a la resta de companys, NO POSEU AQUESTES LÍNIES ALS FITXERS SENSE LLEGIR EL POST D'EN DAFAKTOR. En el seu blog indica exactament quines línes són per afegir, quines per substituir, etc.

Salut i gràcies de nou!

---

### Post by dafaktor on 2008-07-12
Ei, m'alegra que t'hagi funcionat i gràcies per això dels salts de línia, no me n'havia adonat...

Ja he editat l'entrada.

Vagi bé...

---

### Post by Daerun on 2008-07-13
Ep, doncs a mi m'ha sortit un problema: quan arrenca la màquina virtual s'apodera del ratolí i del teclat i els boqueja, de manera que no puc fer absolutment res. :shock:

---

### Post by Rubunter on 2008-07-13
> **Daerun said:**
> Ep, doncs a mi m'ha sortit un problema: quan arrenca la màquina virtual s'apodera del ratolí i del teclat i els boqueja, de manera que no puc fer absolutment res. :shock:
Instal·la el GuestAdittions

---

### Post by Daerun on 2008-07-13
No no, si és que ja ho tinc instal·lat, i de fet ahir em funcionava correctament, el problema és que ara, quan arrenca la màquina virtual (un güindows), abans inclús que s'inicii,i sense haver fet res, passa a prendre el control del ratolí, que es queda bloquejat, amb el punter a mitja pantalla.

---

### Post by oriolsbd on 2008-07-13
Si prems el botó Ctrl dret s'alliberarà el ratolí. Això és perquè en aquest punt encara no ha començat a funcionar les Guestadditions (ho fa quan s'acaba d'arrancar el sistema operatiu de la màquina virtual).

Salut!

---

### Post by Daerun on 2008-07-13
Perdò per desviar el fil original d'aquest tema, però a veure si m'explico bé: no sé si serà cosa del guestadditions, però no és que es bloquegi mentre s'arrenca el SO, és que no importa l'estona que m'esperi, el ratolí es queda inmobilitzat i inutilizat; de fet la única manera que tinc de recuperar el control sobre l'ordinador és resetejar a sac.

---

### Post by Daerun on 2008-07-15
Bé, he descobert el problema... crec... Tant el meu teclat com el meu ratolí es conecten per usb. Quan afegeixo la modificació del fstab

#USB virtualbox
usbfs  /proc/bus/usb usbfs  devgid=124,devmode=666 0 0


em sorgeix el problema ja dit. Si deixo el fsatb tal cual, doncs la cosa rutlla.

---

### Post by lFossil on 2008-07-15
Ei gràcies, a mí també m'ha funcionat!!

---


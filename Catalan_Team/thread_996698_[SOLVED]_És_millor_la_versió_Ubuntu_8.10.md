---
title: "[SOLVED] És millor la versió Ubuntu 8.10 ?"
date: 2008-11-29
forum: Catalan Team
---

### Post by ernestux on 2008-11-29
Hola,

Val la pena actualitzar de la versió Ubuntu 8.04 (suport a llarg termini) a la nov 8.10 , que no té suport a llarg termini.
Tinc el virtualbox per fer córrer el W , hauré de tornar a configurar-lo?
Quines millores heu comprovat ?

Gràcies,
Ernest

---

### Post by Miquel Ubuntero on 2008-11-29
Hola!
Home, millor, és una mica aviat per preguntar. Fins que no ho provem una mica més, no?
Referent a Virtual Box, ho acabo d'actualitzar des de Ubuntu 8.04 a Ubuntu 8.10 i no he tingut cap problema, el Virtual Box funciona be i no he hagut de configurar res.
Salutacions cordials des de Amer:popcorn:

---

### Post by ernestux on 2008-11-30
Hola,
He actualitzat de ububtu 8.04 a 8.10. I en les 2 vegades que m'ha preguntat he dit que guardés la configuració. I ara tinc un problema amb el virtual box.  No s'obra i surt aquest error:

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing :

He comprovat que tinc el paquet DKMS, instal·lat.

He fet: 	portatil@ernest: $ /etcinit.d/vboxdrv setup,  i em surt:

Usage:  /etcinit.d/vboxdrv {start |stop|restart|status}   .

Em surt això i no sé com puc fer-ho, o entrar-ho.

Gràcies

---

### Post by oriolsbd on 2008-11-30
Hola, primer has d'executar-ho amb permisos de superusuari (amb un sudo). A més, et falta una "/". O sigui, has de fer:

```
sudo /etc/init.d/vboxdrv setup
```

Salut! :-)

---

### Post by oriolsbd on 2008-11-30
Per cert, aquest "problema" que has tingut amb el VirtualBox no ha estat només pel canvi de versió d'Ubuntu. Cada cop que hi ha un canvi del kernel (encara que no canvïis de versió d'Ubuntu) ho hauràs de fer. Avui ho he hagut de fer també jo mateix perquè abans d'ahir hi va haver una actualització del Kernel a Ubuntu 8.10. :-)

---

### Post by ernestux on 2008-11-30
perdoneu, ja havia fet: portatil@ernest: $ /etc/init.d/vboxdrv setup, i em surt:

Usage: /etcinit.d/vboxdrv {start |stop|restart|status}

Però aquesta darrera línia no la sé executar.

---

### Post by oriolsbd on 2008-11-30
Quina versió tens instal·lada de VirtualBox?

---

### Post by ernestux on 2008-11-30
Hola,
Ja he mirat altres posts. T'enganxo això:

portatil@ernest:~$ sudo aptitude search '~i'|grep linux-image
i   linux-image-2.6.24-17-generic   - Linux kernel image for version 2.6.24 on x
i   linux-image-2.6.24-18-generic   - Linux kernel image for version 2.6.24 on x
i   linux-image-2.6.27-9-generic    - Linux kernel image for version 2.6.27 on x
i   linux-image-generic             - Generic Linux kernel image                
i   virtualbox-ose-modules-2.6.24-1 - virtualbox-ose module for linux-image-2.6.

portatil@ernest:~$ uname -a
Linux ernest 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

Sinó, el desinstal·lo i el torno a instal·lar.

Gràcies

---

### Post by oriolsbd on 2008-12-01
Hola, més que les versions del "linux-image", buscava la del virtualbox en sí. Des de Synaptic (o Adept, depen del que utilitzis) la podràs veure.

De moment, veig que tens la versió OSE. Jo utilitzo l'altra (la no-OSE). No sé si això pot tenir-hi alguna cosa a veure. Quan jo poso una opció incorrecta en el vboxdrv, em diu que tinc totes aquestes opcions:
```
Usage: /etc/init.d/vboxdrv {start|stop|stop_vms|restart|force-reload|status|setup}
```

Com veus, em surten moltes més que a tu. Per això crec que pot ser tema de la versió del VirtualBox. Potser sí que anirà bé desinstal·lar i tornar a instal·lar, però sobretot no ho facis amb l'opció "purge", o perdràs les màquines virtuals. Espera si algú que té la versió OSE et pot donar alguna pista més.

---

### Post by PatrickVogeli on 2008-12-01
prova amb aixo: sudo apt-get install dkms virtualbox-ose-source i despres executa el virtualbox.

salut

---

### Post by ernestux on 2008-12-01
He fet el que deies, però ja tenia instal·lats els 2 paquets.
La solució ha estat fer córrer el Virtualbox des de la terminal i ha protestat aconsellant que baixés el paquet linux-headers-generic, i ha fet:
 
S'han instal·lat els paquets següents:

linux-headers-2.6.27-9 (2.6.27-9.19)

linux-headers-2.6.27-9-generic (2.6.27-9.19)

linux-headers-generic (2.6.27.9.13)

He reiniciat (re setup) i ara ja em va bé el Virtualbox.

Gràcies,

---


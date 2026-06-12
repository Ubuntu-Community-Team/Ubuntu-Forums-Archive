---
title: "Imatge al GRUB"
date: 2008-08-23
forum: Catalan Team
---

### Post by LitusMayol on 2008-08-23
Bones familia!

He probat de posar una imatge de fons al grub tot seguint [aquest]("http://www.vcubells.net/arxiu/2008/01/19/845/") manual que em va facilitar en **papapep**.

Però quan engego no obre la imatge i em diu *"Failed to read splash image (hd0,2)/boot/grub/final.xpm.gz"*.

Aquesta és la meva 1a linia del GRUB i la que fa referència a l'splashimage:
```
splashimage=(hd0,2)/boot/grub/final.xpm.gz
```


Algú se li acut que pot ser?

Merci!

---

### Post by papapep on 2008-08-23
Fes:

```
sudo fdisk -l /dev/sda
```

i

```
ls -la /boot/grub/final.xpm.gz
```

i enganxa-ho tot, au :-P

---

### Post by LitusMayol on 2008-08-23
Primera ordre:
```
litus@mayolets-desktop:~$ sudo fdisk -l /dev/sda
[sudo] password for litus: 

Disc /dev/sda: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003345b

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1               1         182     1461883+  82  Intercanvi Linux / Solaris
/dev/sda2   *         183       15805   125491747+  83  Linux
/dev/sda3           15806       19457    29334690   83  Linux
litus@mayolets-desktop:~$ 

```

Segona:
```
litus@mayolets-desktop:~$ ls -la /boot/grub/final.xpm.gz
-rw-r--r-- 1 root root 7086 2008-08-23 18:20 /boot/grub/final.xpm.gz
litus@mayolets-desktop:~$ 

```

au! ;)

---

### Post by papapep on 2008-08-23
mmm.....doncs no sé....a no ser que hagis tingut algun problema en el procés de creació de la imatge que no hagis advertit...quants cops has provat el procés?

Jo provaria a posar o treure (en funció de si n'hi ha o no) **un** espai entre 

*splashimage=(hd0,2)*  i  */boot/grub/final.xpm.gz*

---

### Post by papapep on 2008-08-23
Fes una prova:

Agafa el fitxer de la imatge, descomprimeix-lo, obre'l amb el Gimp, torna'l a desar, i torna'l a comprimir. Si li canvies el nom al fitxer i modifiques la línia del grub t'asseguraràs de que no et confons amb el primer fitxer. 
A veure què tal.

---

### Post by LitusMayol on 2008-08-23
Ni posant espais, ni tornant a fer la imatge... 

No sé que feR!:confused:

---

### Post by papapep on 2008-08-23
Has provat lo de descomprimir i tal o has repetit el procés des de 0?

---

### Post by LitusMayol on 2008-08-23
> **LitusMayol said:**
> [...] ni tornant a fer la imatge...

Amb això em referia a que he tornat a fer tot el procés. I res.

---

### Post by papapep on 2008-08-23
Bé, i lo de descomprimir, i tal??? per què no ho proves???

---

### Post by LitusMayol on 2008-08-23
Fet! ;) I res.

---

### Post by papapep on 2008-08-23
Se m'han acabat els mistos noi. I com que és tema de estètica pura, ja ho trobaràs algun dia d'aquests  :-P

---

### Post by LitusMayol on 2008-08-23
Espero sobreviure...! heheh

Merci de totes maneres **papapep**! ;)

---

### Post by SiscoGarcia on 2008-08-23
Hola Litus i papapep,

Jo no sé llegir entre línies com en papapep ;) així que dono per fet que la imatge comprimida final.xpm.gz existeix i és a la carpeta grub de boot. Se m'acut que el problema tingui a veure amb la mida i els colors de la imatge desitjada, és possible?

Fixat en el tutorial del Cubells i veuràs que ha de ser de 640x480 pixels i de 14 colors. Jo tinc la que ha creat ell i no he tingut cap problema a fer-la anar en unes quantes màquines.


```
Si vosaltres voleu fer-ne un personalitzat per al vostre sistema lliure, la feina és ben fàcil.

Solament heu de crear una imatge, la que vulgueu, i després convertir-la en una indexada amb una paleta de 14 colors com a màxim, i d’una grandària de 640×480 pixels amb extensió xpm.

És a dir, heu d’executar la següent comanda:

$ convert -resize 640x480 -colors 14 inicial.png final.xpm && gzip final.xpm

L’execució de l’anterior comanda us crearà un fitxer empaquetat anomenat final.xpm.gz.
```

Espero haver estat d'ajuda :)

---

### Post by manelfus on 2008-08-23
Perque  tans mals de cap ?? ?


"apt-get install startupmanager"



i millor en mode grafic  que rulant amb el gurb ? no se perdo per la meva intromissio pero per donar un pass s'ha de moure un peu.

salut

---

### Post by orestesmas on 2008-08-24
Què hi tens a les 2 particions linux? Quin és el teu fitxer /etc/fstab?

Si tu poses (hd0,2), i tenint en compte com numera les particions el GRUB, vol dir que tens el /boot a /dev/hda3

Ho dic perquè a vegades es posa el directori /boot en una partició a banda, i llavors la teva línia del GRUB hauria d'ometre el /boot:

```

splashimage=(hd0,2)/grub/final.xpm.gz

```

---

### Post by patrickfromspain on 2008-08-24
Editat

---

### Post by LitusMayol on 2008-08-24
Bones!

@**SiscoGarcia**. Si si, té el format adequat i tot i així re de re... Però merci! :)

@**manelfus**. Ja l'he tingut l'**startupmanager** i li tinc molta tirria. xD I tampoc, abans de fer el post el vaig instal·lar vaig probar-ho i re de re... 

@**orestesmas**. Tinc tres particions. 
[LIST=1]
[*]**La *swap*(com els GEI dels mossos però dels EUA)**
[*]**La partició amb Ubuntu**
[*]**La partició amb UbuntuStudio** (ja ja ho sé, ho trobes una burrada tenir-lo en una partició apart! ;) )
[/LIST]

I en aquest ordre. El GRUB és el del **UbuntuStudio**, per tan és *(hd0,2)*. I no. La carpeta és la típica i tòpica:
```
litus@mayolets-desktop:/media/disk$ ls
bin    dev   initrd          lib         media  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img      lost+found  mnt    root  sys  var
cdrom  home  initrd.img.old  medi        opt    sbin  tmp  vmlinuz

```


@**patrickfromspain**. Editat??

Merci a tots igualment!

---

### Post by papapep on 2008-08-24
> La swap(com els GEI dels mossos però dels EUA)

Tiu! que era [SWAT]("http://en.wikipedia.org/wiki/SWAT"), no swap... :-D

Jovenalla....

I de fet, mirant-m'ho bé, la partició sda2, pel grub és (hd0,1), no (hd0,2), sinó vaig errat. No comença per 1, comença per 0.

---

### Post by oriolsbd on 2008-08-25
Hola, has dit que li tens tírria a l'startupmanager. Per què no proves el "qgrubeditor"?

Apart de poder-li indicar una "splash image", et permet agafar una imatge que tu tinguis i convertir-la al format que necessita el grup (amb el botó "Create" de l'apartat "splash image").

Prova-ho, a veure si et funciona.

Salut!

---

### Post by Joan Marc on 2008-08-25
> **papapep said:**
> I de fet, mirant-m'ho bé, la partició sda2, pel grub és (hd0,1), no (hd0,2), sinó vaig errat. No comença per 1, comença per 0.
Bé, sempre pots fer un
```
$ sudo grub
> find /boot/grub/stage1
```
Per saber on tens el grub instal·lat no?
Saluts!

---

### Post by LitusMayol on 2008-08-26
> **Joan Marc said:**
> Bé, sempre pots fer un
```
$ sudo grub
> find /boot/grub/stage1
```
Per saber on tens el grub instal·lat no?
Saluts!

El Grub sé seguríssim que està al (Hd0,2). L'he estat *canviant* perquè en lloc de posar "***Ubuntu 8.04 Kernel blabalbala-rt***" posés "**UbuntuStudio**" i "**Ubuntu**".

Tampoc patiu massa, citant a en **papapep**: "*és un tema d'estètica*" i podré seguir endavant sense ell! ehhe





(tot i que si ho soluciono us faré un post esplicant com ho he fet ;))

---


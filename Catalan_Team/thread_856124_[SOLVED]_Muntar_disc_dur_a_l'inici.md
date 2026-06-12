---
title: "[SOLVED] Muntar disc dur a l'inici"
date: 2008-07-11
forum: Catalan Team
---

### Post by Daerun on 2008-07-11
Fa poc he reinstal·lat el Hardy de nou. Tinc dos discos durs, i per algun motiu, el segon, on hi tinc només dades, no m'el "munta" a l'inici: és a dir, que no m'apareix la seva icona a l'escriptori, ni al AWN; tamnateix, sí que el tinc al menú Llocs, i si hi clico, aleshores sí, apareix i es mostra de manera normal. He buscat la manera d'editar el fstab perquè ho faci d'inici, però per algun motiu, totes les opcions que he provat no han funcionat. La última que he provat és aquesta:

# /dev/sdb1
UUID=10645F33645F1B34    /media/sdb1 ntfs-3g defaults,locale=es_ES.UTF-8 0 0

la anterior va ser aquesta:

# /dev/sdb1
/dev/sdb1 /media/Documents ntfs-3g auto,defaults,uid=10645F33645F1B34 0 0

i abans d'això ho vaig provar d'una altra manera, que no he conservat, que tampoc funcionava. A veure si em podeu donar un cop de mà  :confused:

---

### Post by CarlesOriol on 2008-07-11
Xequeja el disc amb ntfs. Deu tenir errors. (et caldrà fer-ho en hasefrog)

Si el muntes a maneta ho pots forçar. (mount .... force ) Però vigila que segur que no està bé o no has tancat bé el hasefrog.

---

### Post by Daerun on 2008-07-12
Perdo per la ignorància,però que es hasefrog? :confused:

---

### Post by patrickfromspain on 2008-07-12
es el putu-windows :D

---

### Post by Daerun on 2008-07-12
Ara se n'hi diu així? :lolflag:

---

### Post by papapep on 2008-07-12
Ja fa temps :-) : [http://es.wikipedia.org/wiki/Hasefroch](http://es.wikipedia.org/wiki/Hasefroch)

---

### Post by Daerun on 2008-07-14
Bé, sempre s'aprèn alguna cosa nova :mrgreen:

El disc no tenia cap error, i ho he arreglat instal·lant el Disk Manager

[http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)

un cop obert, he  seleccionat el disc dur de la discòrdia porquè es configurés (és la paraula que fa servir el DM) i aparagués en iniciar.

---

### Post by CarlesOriol on 2008-07-15
Puja la nova linia del fstab per que ho veiem.

---

### Post by Daerun on 2008-07-15
Aqui está:

#Entry for /dev/sdb1 :
UUID=10645F33645F1B34    /media/Documents    ntfs    defaults,nls=utf8,umask=0222    0    0

L'ha afegida el Disk Manager, s'entén. Seria interessant veure si funciona afegint-la a mà, prescindint del DM?


EDITO per comentar que,efectivament, afegir-la a mà, havent desinstal·lat el Disk Manager, també funciona.

---

### Post by Daerun on 2008-07-16
Doncs, com he dit, funciona, però ara em trobo que en aquest disc dur no hi tinc plens privilegis: no puc retallar arxius, n'hi enganxar-ne d'altres localitzacions, i quan copio els seus arxius a la carpeta Home apareixen amb el cadenat.

---

### Post by papapep on 2008-07-16
I si canvies l'umask "0222", per "022"?

---

### Post by lluisanunez on 2008-07-16
Hola,
després d'actualitzar a Hardy m'ha passat una cosa semblant: la partició que tenia amb nom "data" i muntada a /media/data, apareix muntada al mateix lloc però ha perdut el nom i ara es diu "269.0 GB media". Si obro les propietats > permisos em diu **The permissions of "data" could not be determined**
Així està a /etc/fstab:
```
# /dev/sda2
UUID=5b3c0a9f-7dd8-4dd1-b506-0fc1c38cfa4d /media/data    ext3    defaults        0       2
```

---

### Post by Daerun on 2008-07-16
> **papapep said:**
> I si canvies l'umask "0222", per "022"?


Doncs no, fent això em surt un missatge d'error

"No es pot muntar el volum
mount: només l'usuari root pot muntar /dev/sdb1 a /media/Documents"


lluisanunez, que em corregegi algú, però jo diria que el problema ve per aquest "2" que apareix al final de la línia, que hauria de ser un "0"... però no canviis res sense que algú ho confirmi :p

---

### Post by papapep on 2008-07-16
Si poses "umask=0000" segur que et funcionarà (hauria de...), però és una mica bèstia, ja que estàs donant permisos totals a qualsevol usuari.

Si poses "umask=0002" estaràs assignant els permisos 775 a la unitat, el qual sembla més raonable. El que no tinc clar és el primer dígit, si hi ha de ser o no. Podries provar primer amb "002" a veure si funciona.

---

### Post by Daerun on 2008-07-16
L'has encertada Papapep, només calen tres digits :D

Així doncs, definitivament, la línia que cal afegir al /etc/fstab perqué el Hardy munti el disc dur a l'inici és aquesta:


UUID=[la uuid del teu disc dur]     /media/[nom del teu disc dur]        ntfs    defaults,nls=utf8,umask=002     0      0



Per saber la UUID del disc dur, només cal anar al menú Llocs > Ordinador, s'obrirà el nautilus i cal clicar amb el botó dret sobre el disc dur en qüestió, apareixerà una finestra, i cal anar a la pestaña "Volume" per trobar el UUID.

Aqui mateix també es pot trobar el punt de muntatge del disc (/media/nom_que_sigui), i finalment IMPORTANT, umask=000 en cas de voler donar plens privilegis d'acces, o umask=002, en cas de voler donar només privilegis de lectura/execució.

---

### Post by oriolsbd on 2008-07-17
Hola, si vols tenir-ho més controlat, també pots fer que només un grup d'usuaris pugui escriure en aquest disc. Si fas:
UUID=[la uuid del teu disc dur] /media/[nom del teu disc dur] ntfs defaults,nls=utf8,umask=002,gid=xxx 0 0

On "xxx" és el número d'identificació d'd'un grup d'usuaris (que pot existir o que pots crear), els usuaris que estiguin en aquest grup tindran permisos també d'escriptura, i els que no estiguin al grup, tindran només permisos de lectura i execució. Una altra opció que en alguns casos pot ser útil és, apart d'afegir el "gid", posar "umask=007". En aquest cas, els pertanyents a aquest grup podran llegir, executar i escriure, però els usuaris que no pertanyin al grup no podran ni tan sols llegir la informació del disc.

Salut!

---

### Post by Daerun on 2008-07-19
Moltes gràcies a tots, tema resolt més que satisfactòriament :D

---

### Post by CarlesOriol on 2008-07-19
Per saber el UUID en comandes pots usar el programa vol_id.

Per exemple:

sudo vol_id /dev/sda1

---

### Post by lluisalguero on 2008-08-13
Jo es que des de fa uns dies cap aquí que no m'ho munta 2 particions tampoc a l'inici...i no he tocat res..
el meu etc/fstab diu això (entre altres coses)

```
# /dev/sda1
UUID=8208BEE408BED5FF /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=7038585538581C82 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
```

no sé si ho tindria que canviar i ficar-ho tal i com dieu més amunt

```
UUID=[la uuid del teu disc dur] /media/[nom del teu disc dur] ntfs defaults,nls=utf8,umask=002 0 0
```

i per a mes conya, hi han cops que m'ho munta a l'inici i han cops que no...

Crec que al final tindré que matxacar-ho tot, perque ja son diversos els problemes que tinc en la posta en marxa de l'Ubuntu...començo a estar una mica "fregit"

---

### Post by CarlesOriol on 2008-08-13
Pot ser per errors al disk ntfs o una sortida irregular de l'altre sistema que deixi el disc marcat.

Si vols pots fer dos canvis.

- Canviar el ntfs per ntfs-3g per tenir suport d'escriptura

Si estas segur que el disc no té errors afegir force als paràmetres.

# /dev/sda1
UUID=8208BEE408BED5FF /media/sda1     ntfs-3g    force,defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=7038585538581C82 /media/sda2     ntfs-3g    force,defaults,umask=007,gid=46 0       1

---

### Post by lluisalguero on 2008-08-13
> **CarlesOriol said:**
> Pot ser per errors al disk ntfs o una sortida irregular de l'altre sistema que deixi el disc marcat.

Si vols pots fer dos canvis.

- Canviar el ntfs per ntfs-3g per tenir suport d'escriptura

Si estas segur que el disc no té errors afegir force als paràmetres.

# /dev/sda1
UUID=8208BEE408BED5FF /media/sda1     ntfs-3g    force,defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=7038585538581C82 /media/sda2     ntfs-3g    force,defaults,umask=007,gid=46 0       1

Tinc el presentiment que era un error del disc ntfs, ja que he entrat al finestres (es el que fan servir els meus fills) i al tornar a entra a l'Ubuntu, ja m'apareixen les particions.

Gracies de totes formes

---

### Post by CarlesOriol on 2008-08-13
És el que et comentava. Quan el finestres es tanca inadecuadament o es suspen el disc queda en un estat que el linux no l'automunta. Sols cal reiniciar el finestres i sortir-ne correctament.

Ah.... ;-) i hi ha un truc que jo uso, per que això no passi. Eliminar aquell sistema de l'ordinador.

---

### Post by lluisalguero on 2008-08-14
> **CarlesOriol said:**
> És el que et comentava. Quan el finestres es tanca inadecuadament o es suspen el disc queda en un estat que el linux no l'automunta. Sols cal reiniciar el finestres i sortir-ne correctament.

Ah.... ;-) i hi ha un truc que jo uso, per que això no passi. Eliminar aquell sistema de l'ordinador.

Malauradament, necesito el finestres per a fer anar uns pocs programes dels que no he trobat cap alternativa al ubuntu...

---

### Post by CarlesOriol on 2008-08-14
> **lluisalguero said:**
> Malauradament, necesito el finestres per a fer anar uns pocs programes dels que no he trobat cap alternativa al ubuntu...

Deies que era pels teu fills, quins son aquest programes?. A veure si et podem ajudar a anar-ho "netejant".

---

### Post by lluisalguero on 2008-08-14
> **CarlesOriol said:**
> Deies que era pels teu fills, quins son aquest programes?. A veure si et podem ajudar a anar-ho "netejant".

Apart de que els meus fills i juguen, jo sóc "fotògraf" aficionat, i després de comparar The Gimp amb Photoshop, i d'altres de retoc fotogràfic..., ho sento no he trobat alternatives a "Photomatix" o a "PT Lens" o al "Noise Ninja" i així a algún d'altre...

Ja em fot, que cada cop haig de reiniciar i posar en marxa el finestres per a la "feina" fotogràfica..

---

### Post by Daerun on 2008-08-14
També pots fer servir virtualbox i instal·lar-hi un XP, així no haurás de reiniciar cada vegada :P

---

### Post by CarlesOriol on 2008-08-15
(mmm... Hauriem de fer un nou fil... )

Crec que amb una mica de sort tots els pots usar amb wine.

D'entrada tots ells estan a la llista de [http://appdb.winehq.org/](http://appdb.winehq.org/) sense cap problema important notificat.

Abans de res et recomano insta&#320;lar el wine 1.1.0 tal com diuen a [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Si et cal pots usar winetricks [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) per tal de configurar les parts del sistema que no han estat reescrites usant les llibreries originals.

En aquest punt pots provar dues coses:

1. Anar a la carpeta on tens la insta&#320;lació actual i exectuar el programa amb wine nomdelprograma.exe

2. Provar si et funciona de fer la insta&#320;lació d'aquest.

Au...

Digue'ns si et funciona.

---


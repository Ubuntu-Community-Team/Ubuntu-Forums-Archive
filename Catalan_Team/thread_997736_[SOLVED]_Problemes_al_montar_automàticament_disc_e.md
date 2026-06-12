---
title: "[SOLVED] Problemes al montar automàticament disc esclau"
date: 2008-11-30
forum: Catalan Team
---

### Post by mininomutante on 2008-11-30
Hola a tots,
Porto uns dies amb un problema i us ho plantejo per si em podeu ajudar.
Tinc un disc dur esclau amb l'etiqueta "Disco local 2".
Segons he llegit per aquest i altres fòrums haig d'editar l'arxiu fstab (així és com el tinc actualment) 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=bd85965a-ca90-41b1-9651-e0565a5e57fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=92f80734-9b15-44b9-87c0-ac1c9cd083b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb1
UUID=2234719C3471739F /media/disk ntfs-3g force,defaults,umask=007,gid=46 0 1
```

i afegir-hi alguna cosa semblant a:
```
# /dev/sda1
UUID=A06C41486C411A84 /media/Disco local 2 ntfs-3g force,defaults,umask=007,gid=46 0 1

```
Comentar-vos que la carpeta on em crea el dics dur és /media/Disco local 2, pot venir l'error del nom d'aquesta etiqueta? :confused: .
El dilema és que no ser fixar-ho perquè al arrancar ja estigui montat.

Gràcies i disculpeu les molèsties, soc novell en això de l'ubuntu :oops:

PD: la línia
```
# /dev/sdb1
UUID=2234719C3471739F /media/disk ntfs-3g force,defaults,umask=007,gid=46 0 1
```
També l'he posat jo per coses que he llegit per la xarxa però no sé segur si és del tot correcte :confused:, aquest és un disc dur master i sí me'l reconeix inicialment.

---

### Post by oriolsbd on 2008-12-01
Hola, en un PC que tinc on conviuen Windows i Ubuntu 8.10 he vist que les particions "ntfs" les té definides així:

```
UUID=xxxxxxxxx  /media/windows  ntfs  defaults,umask=007,gid=46  0 1
```

De tota manera, del que tu li indiques no crec que li agradi massa els espais que hi ha a "Disco local 2" a l'hora d'interpretar el fitxer fstab. Encara que aquest sigui el label del disc, realment ho pots muntar en el directori que vulguis. Jo crearia un directori en el qual el nom no tingui espais, i el muntaria allà.

Salut!

---

### Post by mininomutante on 2008-12-01
Hola oriolsbd,
Primer de tot gràcies per la teva resposta.
A mi també em semblava que els espais del "Disco local 2" no pintaven molt bé :(, encara que la instrucció que vaig posar al fstab no &#347;e si és del tot correcte. Intentaré llegir una mica respecte el que em posses de "ho pots muntar en el directori que vulguis" --> com et dic soc novell i vaig amb peus de plom i una mica amb por ;)

Crec que m'ha sortit un error provinent de tot això.
Quan intento entrar al disc (amb la partició de win) per "llocs-> Suport 477,3 GB (nom del disc master)" em surt l'error següent:

"No s'ha pogut obrir la ubicació «file:///media/disk»
No hi ha cap aplicació que s'hagi registrat per a gestionar aquest fitxer" 

En canvi quan hi intento entrar per l'escriptori tot va la mar de bé :confused: (igual em passa amb l'esclau pel menú em surt l'error però per l'escriptori cap problema :confused:)

Gràcies per la resposta ;)

---

### Post by quitus on 2008-12-01
Prova amb "disk manager" Es una aplicació que et permetrà fer tot això de manera gràfica.

salut

---

### Post by mininomutante on 2008-12-02
Moltes gràcies, quitus, m'ha anat molt ;), hem detecta a la primera els disc.
Ara només em queda els temes dels errors en el Menú "llocs"
> "No s'ha pogut obrir la ubicació «file:///media/disk»
No hi ha cap aplicació que s'hagi registrat per a gestionar aquest fitxer" 
Que feia esment en un post de una mica més amunt (que no sé si està relacionat amb tot això)

De debò, molts gràcies ;)

---

### Post by quitus on 2008-12-02
No estic del tot segur, però pot ser degut a un problema amb els permisos, prova amb nautilus com a superusuari per comprovar-ho.

salut.

---

### Post by mininomutante on 2008-12-16
Per si algú li apareix el mateix problema, explico com ho he pogut solucionar (almenys això crec :-D ):
He obert el discos per l'icona de "Ordinador", botó dret de cada disc a "propietats" --> "Obre amb" --> Sel·leccionar "Navegador de fitxers" i ja està.

---

### Post by jinglada on 2008-12-16
> **quitus said:**
> Prova amb "disk manager" Es una aplicació que et permetrà fer tot això de manera gràfica.

salut

Ufffff! que bé quitus! Jo tenia un problema semblant que vaig comentar en aquest fil [http://ubuntuforums.org/showthread.php?t=938190](http://ubuntuforums.org/showthread.php?t=938190) i finalment l'acabo d'obrir amb el "disk manager". Estava molt preocupat fins i tot m'estava mentalitzant de que potser perdria gran quantitat d'informació.

---


---
title: "No s'instal.la"
date: 2008-02-12
forum: Catalan Team
---

### Post by dmolner on 2008-02-12
Hola,

Com vaig dir en el post de presentació finalment vull deixar de banda l'XP i treballar només amb Linux.

M'he descarregat la versió 7.10 per x86 però tinc un problema.

Quan comença la instal.lació aquesta s'atura de sobte amb aquest missatge.

Udevd-event[a434]:run_program:'/sbin/modprobe'abnormal exit

El Pc es un AMD Athlon 64 3200+ amb 512Mb
Un disc dur SATA de 127Gb amb XP
Un disc dur IDE de 20Gb amb XP que es on vull posar Linux.

També he provat la versió 7.10 de 64Bits i el resultat es el mateix, penso que potser la única sol.lució serà desconnectar el disc SATA per fer la instal.lació.

---

### Post by papapep on 2008-02-12
Abans de fer res més jo provaria a fer la instal·lació amb la versió Alternate.

---

### Post by eduardsola on 2008-02-12
> **papapep said:**
> Abans de fer res més jo provaria a fer la instal·lació amb la versió Alternate.

Si et puc ajudar amb la descàrrega...

[ftp://ftp.caliu.cat/pub/distribucions/ubuntu/releases/7.10/ubuntu-7.10-alternate-i386.iso](ftp://ftp.caliu.cat/pub/distribucions/ubuntu/releases/7.10/ubuntu-7.10-alternate-i386.iso)

---

### Post by dmolner on 2008-02-12
Ja esta baixada.

Gràcies. eduarsola

---

### Post by dmolner on 2008-02-13
Hola, ja soc aqui altre cop.

No he aconseguit res, ni amb la versió Alternate i instalació text (es queda parada i no avança) ni desconectant el disc dur SATA.

Que més puc provar?

---

### Post by patrickfromspain on 2008-02-13
podries probar a posar les ordres d'arrancada noapic acpi=off irqpoll a l'hora d'arrancar el live cd.

salut!

---

### Post by dmolner on 2008-02-13
> **patrickfromspain said:**
> podries probar a posar les ordres d'arrancada noapic acpi=off irqpoll a l'hora d'arrancar el live cd.

salut!

Pots explicar-me com fer-ho?

---

### Post by patrickfromspain on 2008-02-13
doncs a l'arrancar, amb sembla que amb F6 (hi posa options) apretes i pots passar els parametres que t'he dit i pitjar enter per a que el kernel es carregui amb ells.

salut

---

### Post by eduardsola on 2008-02-13
Una cosa...

Quan poses el cd i reinicies el PC, després s'inicia amb el cd, no?

---

### Post by patrickfromspain on 2008-02-13
depen de com tinguis configurada la bios..

---

### Post by CarlesOriol on 2008-02-14
També pots trobar algunes bios (sobretot en portàtils) que sense entrar a la configuració amb alguna tecla al iniciar (normalmer f12 però pot ser qualsevol) et permeten elegir el dispositiu d'inicialització

---

### Post by dmolner on 2008-02-14
Hola,

El problema no es que no s'inicii el CD, el problema es que comença la instal.lació i s'interromp.

He provat el que hem van dir de posar al menú d'inici del CD i tampoc.
:(:confused:

---

### Post by papapep on 2008-02-14
Però en quin punt concret se't queda? Arribes a veure el menú per triar quina mena d'instal·lació vols fer?? O ja no arribes ni aquí? No et mostra CAP missatge? Ni un abans de quedar-se fregit?

---

### Post by Frealof on 2008-02-14
Hola dmolner.

Pot ser que el CD se t'hagi cremat malament?

Ho dic perquè a mi em passava això quan em vaig baixar la imatge de CD de la Knoppix... i els primers d'Ubuntu, fins que no me'n vaig adonar (per pura casualitat ;)). 

Si has canviat l'ordre de Boot de HDD a CD-ROM hauria d'anar, en el cas que t'arrenqui el menú d'instal·lació hi ha una opció que busca defectes al disc... Jo li faria una passada, a veure què. Si no es això... en poc més puc ajudar-te.

Salut!

---

### Post by dmolner on 2008-02-14
> **dmolner said:**
> Hola,
Quan comença la instal.lació aquesta s'atura de sobte amb aquest missatge.

Udevd-event[a434]:run_program:'/sbin/modprobe'abnormal exit

El Pc es un AMD Athlon 64 3200+ amb 512Mb
Un disc dur SATA de 127Gb amb XP
Un disc dur IDE de 20Gb amb XP que es on vull posar Linux.

També he provat la versió 7.10 de 64Bits i el resultat es el mateix, penso que potser la única sol.lució serà desconnectar el disc SATA per fer la instal.lació.

El missatge que dona es el d'aquí d'alt.

Ho he provat amb 3 CD's i ho he gravat 3 o 4 vegades, també he fet la comprovació del CD

---

### Post by papapep on 2008-02-14
I tu quina versió intentes instal·lar, la de 32 bits o la de 64? El missatge que esmentes quan te'l mostra, abans d'arribar al menú, o després??

---

### Post by dmolner on 2008-02-14
He provat les dues versions.
El missatge surt en les dues versions i surt despres del menu on es sel.lecciona el tipus d'instal.lación, comença però s'aborta.

Tambe he provat la alternate i el resultat es el mateix.

---

### Post by papapep on 2008-02-14
Val, perfecte. Ja ens comencem a ubicar.

Aleshores, agafa l'alternate i quan estiguis al menú on tries el tipus d'instal·lació prems F6 (Other options) i hi fiques el següent:

```
noapic acpi=off irqpoll
```

Darrera la línia que t'apareix:

---

### Post by dmolner on 2008-02-14
OK
Ja ho he fet i el resultat es que es queda penjat :mad:, indico l'ultim que surt en pantalla.

[xx.xxxxxx] sd 0:0:0:0: [sdb] Attached SCSI removable disk
[xx.xxxxxx] sd 0:0:0:0: Attached SCSI generic sg1 type 0

He provat el CD en un altre PC i s'inicia sense cap problema en pocs segons.
L'altre es un AMD64 amb un disc dur SATA, vaja que son molt iguals

---

### Post by ilku on 2008-02-15
Posa quina es la placa base.
Ho dic perquè jo m'havia trobat en versions anteriors d'ubuntu que el xip controlador del discs (normalment el northbridge) no era compatible amb ubuntu i es quedava penjat.
Si és això la cosa es complica.

Una salutació

---

### Post by dmolner on 2008-02-15
La placa es
ASUS K8N-E Deluxe

---

### Post by patrickfromspain on 2008-02-15
prova a desconectar tarjes pci que hi tinguessis connectades, prova amb un sol módul de ram, etc

La fallada ha d'estar en alguna cosa del maquinari. La placa no pinta malament, ja que jo tinc una A8V-E deluxe i funciona be

salut!

---

### Post by ilku on 2008-02-18
Prova amb una altre lector de CD/DVD, potser no funciona del tot bé. Com has dit que tenies un altre ordinador a mà que et funcionava bé intercanviar lectors.

---

### Post by dmolner on 2008-02-19
Dons no hi ha manera!!!

He provat un altre lector i tampoc
Les tajes només tinc les dels ports USB
Fins hi tot he provat la versió 6 d'Ubuntu

Si instal.lo el Kubuntu podré fer el mateix?

---


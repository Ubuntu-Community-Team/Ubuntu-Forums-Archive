---
title: "Hardy no em deixa posar grub"
date: 2008-04-12
forum: Catalan Team
---

### Post by ffp on 2008-04-12
Hola,

He instal·lat Hardy en un ordinador AMD XP 2400+  RAM 1,5GB i DD 40GB, que tinc per fer proves, abans tenia Debian.
El CD live no reconeixia la màquina, per la qual cosa l'he instal·lat amb el alternate, al arribar al moment en que ha de carregar el grub m'ha donat error, "no es pot instal·lar el carregador, el sistema no arrencara".
L'hi passat el super grub i res de res. Resulta que no havia instal·lat /boot/grub ni menu.list.
Ho he tornat a intentar i mateix resultat, com el alternate m'ho ha permès, l'hi posat LILO i ha funcionat correctament.
Però el LILO (primera vegada que el tinc), no te un menú per canviar kernels o entrar en línia d'ordres.
Un altra cosa que no entenc es que marca el disc com sda, i al ser ATA, hauria de ser hda ?
Que consti que funciona be, però m'emprenya lo del grub.

A algú se l'hi acut quelcom? :confused:

---

### Post by menut on 2008-04-12
Linux mostra els discos SATA, el llapis USB i altres com a SCSI, i, per tant, *sda*.

Tot i que això no és cert del tot, ja que SATA=ATA=IDE, i hauria de ser *hda*. Per tant, tens raó.

---

### Post by patrickfromspain on 2008-04-12
No senyors. Fa temps que es va cambiar la nomenclatura. Si no m'equivoco, van aprofitar la manera de tractar els discos SATA per a les unitats ATA/IDE. Això es una novetat, ja que si no m'equivoco es fa així des de la Feisty.

Ah! no es un tema d'ubuntu, sino de kernel.

Respecte a SATA=ATA=IDE, no, mai de la vida.

salut!

---

### Post by ffp on 2008-04-12
patrickfromspain,

L'altra ordinador, amb 7.10, tinc 2 discs SATA (sda i sdb) i 1 ATA (hda), o sigui que a Feisty encara es així.

Salut

---

### Post by menut on 2008-04-13
> **patrickfromspain said:**
> Respecte a SATA=ATA=IDE, no, mai de la vida.


IDE=ATA. Estem d'acord aquí ?

És igual que estigui en paral·lel(PATA) o en sèrie (SATA), són dispositius IDE els 2.

I, per tant, haurien d'apareixer com a /dev/hdX tots els IDE.


[http://es.wikipedia.org/wiki/Integrated_Drive_Electronics]("http://es.wikipedia.org/wiki/Integrated_Drive_Electronics")

---

### Post by patrickfromspain on 2008-04-13
Mea culpa senyors!

Es veritat que els SATA son Ide tambe, gracies per l'aclaració.

Respecte al tractament de linux... jo pensava que ja feia temps que la nomenclatura havia canviat, ja que pels forums en angles no es res de nou que els discos PATA apareguin com a sdX.

Per tant.. ja no comento res perque ja m'he perdut xD. El que em sembla recordar es que el kernel migraria a la branca de libata per a tots els dispositius, tant Pata com Sata, deixant d'utitilitzar la emulació Scsi i els drivers ide estàndard.

Salut!

---


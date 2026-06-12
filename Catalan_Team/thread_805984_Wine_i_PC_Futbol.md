---
title: "Wine i PC Futbol"
date: 2008-05-24
forum: Catalan Team
---

### Post by PequeMayol on 2008-05-24
Bones,

és el meu primer post, si alguna cosa no ha quedat clara digueu-m'ho.

Voldria poder utilitzar el **PC Futbol** (2000 o 2001 és igual quin). 
M'han dit que amb el **Wine** puc utilitzar programes de Windows.
El problema és que no tinc instal·lat **Wine** i tampoc el sé fer funcionar.

Algú em pot dir com instal·lar el **Wine** i posteriorment el **PC Futbol**?



Gràcies!

---

### Post by menut on 2008-05-24
Amb el Wine, que jo sàpiga, els jocs no funcionen.

Si vols jugar a jocs de windows dins de l'Ubuntu, i tens un ordinador potent, pots instal·lar el Virtualbox, i instal·lar-hi dins el Windows i el joc.

---

### Post by PequeMayol on 2008-05-24
Vist que amb el **Wine** no funciona....

Algú podria dir-me de quina manera podria utilitzar **PC Futbol**? 


De totes maneres gràcies **Menut**!

---

### Post by papapep on 2008-05-24
> Amb el Wine, que jo sàpiga, els jocs no funcionen.

Jo no acostumo a jugar (i menys jocs de [hasefroch]("http://es.wikipedia.org/wiki/Hasefroch")), però aquesta afirmació és, com a mínim, no exacta. Si mires [URL="http://appdb.winehq.org/"]al lloc web de Wine
[/URL] dels 10 programes que remarquen a la pàgina principal 6 són jocs. Imagina si comencem a mirar a la base de dades d'aplicacions que pot executar el wine, quants jocs deu haver.
Probablement sigui més correcte dir que depèn de cada cas en concret i que quant més modern sigui i més "directx" d'aquests faci servir, més complicat serà.

> Si vols jugar a jocs de windows dins de l'Ubuntu, i tens un ordinador potent, pots instal·lar el Virtualbox, i instal·lar-hi dins el Windows i el joc.

Això tampoc és exactament correcte ja que, a banda de concretar què és potent i què no, depen directament d'altres paràmetres com, per exemple, què intentes executar amb la màquina virtual. Sé de casos en que va més lleuger el programa (i molt) a la màquina virtual sota Ubuntu que en mode natiu en Hasefroch, i t'asseguro que no és cap programa poc pesat ni senzillet (un totxo fet en java i molt mal programat).

---

### Post by Joan Marc on 2008-05-24
> **menut said:**
> Amb el Wine, que jo sàpiga, els jocs no funcionen.
Com ha dit en papapep, si que es pot jugar a jocs de hasefroch, i despen dels jocs van o no van. Et posaré 2 exemples: Imperivm III si que va, en canvi el CounterStrike CZ no...

Salut!

---

### Post by pespin on 2008-05-24
> Algú em pot dir com instal·lar el Wine i posteriorment el PC Futbol?



1- Instal·lar wine:

Tens 2 opcions, fer-ho des de la terminal o des del Synpatic. Des de la terminal has d'escriure:

```
sudo aptitude install wine
```

I Per instal·lar-lo des del Synpatic has de buscar i instal·lar el paquet "wine".


2- Jugar/Instal·lar el PC Futbol:

Diria que tens 2 opcions, des de la terminal o des de l'entorn gràfic (aquesta última no n'estic segur):

Des de la terminal --> situat al directori on està l'executable que inicia/instal·la el joc (depent del que vulguis fer) i fes:
```

wine nom_del_executable.exe
```

Des del entorn gràfic --> Situat al directori on està l'executable amb el nautilus i fes clic dret a sobre l'executable. Allà hi hauria d'haver-hi alguna opció del tipus "Córrer amb Wine".

Et recomano la primera opció, ja que si dóna algun error el programa des de la terminal es pot veure i en alguns casos es pot solucionar :)

---

### Post by RainCT on 2008-05-24
> **Joan Marc said:**
> Et posaré 2 exemples: Imperivm III si que va, en canvi el CounterStrike CZ no...

Doncs a mi el Condition Zero em va perfectament (bé, potser vaig haver de buscar alguna .dll addicional, no ho recordo, però el cas és que funciona)...

---

### Post by xoldy on 2008-05-24
Xoldy

---

### Post by xoldy on 2008-05-24
Jo us puc parlar de la meva experiència amb el virtualbox, i la veritat es que el hasefroch va bastant més ràpid tractant-lo com una finestra que com a sistema operatiu. Respecte al tema jox penso que el millor es tenir una consola de videojox, poses cd, engegues consola, i a jugar.

Se que no aporta res aquesta resposta, però feia dies que no intervenia.

De tota manera penso que puc aportar, vista l'experiència, que tinc tan en hasefroch com en linux, que qualsevol prova que vulgui fer, la penso fer sobre sistema virtualitzat que no representi cap impacte sobre el meu sistema "mare" que és la Hardy.

Bona nit i salut per tothom

Xoldy

---

### Post by indiosincracia on 2008-05-25
Les configuracions amb Wine son bastant complicades, aquí tens una aplicació que facilita instal·lar jocs i alguns programes del ghindows al Wine d'una manera gràfica, aquí hi ha el llistat de jocs que permet sense problemes [http://www.playonlinux.com/scripts_v2/show_repository.php](http://www.playonlinux.com/scripts_v2/show_repository.php)
no veig el teu però pots provar, aquí tens com s'instal·la [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)
Vaig a esmorzar, deuu!

---

### Post by Joan Marc on 2008-05-25
> **RainCT said:**
> Doncs a mi el Condition Zero em va perfectament (bé, potser vaig haver de buscar alguna .dll addicional, no ho recordo, però el cas és que funciona)...

Jo ho vaig provar amb la Gutsy Gibbon i no anava, potser amb la Hardy va... ja ho provaré :)

---

### Post by LitusMayol on 2008-05-27
Bones!
Com ha dit el meu germà estem probant d'instal·lar el **PC Futbol**. Animalot de mi, he instal·lat el **Wine** i amb el **Wine** el**PC Futbol**. 

El problema és que tot sembla haver funcionat de meravella. En canvi, quan obro el joc la pantalla queda negra (quan hauria de sortir una introducció de video). No passa re, la única manera fins ara ha sigut "*Alt+Crtl+Supr*" que apareix el menú de sortida i prémer "*Surt*".

> **papapep said:**
> 
Probablement sigui més correcte dir que depèn de cada cas en concret i que quant més modern sigui i més "directx" d'aquests faci servir, més complicat serà.

Pel que fa a això... què vols dir? Que será més difícil, ja, hehe; però vull dir que si hi ha alguna altra manera de fer-ho? 

Hi ha algun altre "**Wine**" però que funcioni millor am el "*DirectX*"?



Merci!

La famila Mayol us n'estarà moooolt agraïda! ;)

---

### Post by pespin on 2008-05-28
> Hi ha algun altre "Wine" però que funcioni millor am el "DirectX"?
Existeix Cedega, una implementació de Wine especialitzada en jocs.Això sí, és de pago :)

Et recomano córrer el PC Futbol des de la terminal amb el wine i mirar els errors que deixi anar per saber si es pot arreglar fàcilment.

Referint-me un altre cop a la cita, el Wine en principi és compatible amb DirectX. Pots instal·lar els DirectX utilitzant Wine de la mateixa manera que ho fas a Windows :)

---

### Post by LitusMayol on 2008-05-28
Bones...

A veure això és el que em diu el Terminal:
```
litus@mayolets-desktop:~$ cd /home/litus/.wine/drive_c/Program\ Files/DINAMIC\ MULTIMEDIA/PC\ FÚTBOL\ 2000/
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$ wine pcf2000.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f22dac0,0x00000000), stub!
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$ 

```
Jo no n'entenc re... :S A més a la finestreta on s'obra apareix una mini-finestra que de títol té "*No hay memoria*" i a l'interior hi ha escrit: "*MemAllocFun*".


Alguna idea?


Merci! ;)

---

### Post by LitusMayol on 2008-05-28
Ep!

Acabo de llegir això [aquí]("http://ubuntuforums.org/showthread.php?t=497332"):
```
Don't install DirectX - Wine has its own DirectX libraries, installing Microsoft's DX will screw up those libraries and Wine in general. Just don't do it.
```

Aleshores... Jo he instal·lat el **DirectX** del **PC Futbol**. Ara probaré de desintal·lar el joc i tornar-lo a insatal·lar sense instal·lar el **DirectX**.

---

### Post by LitusMayol on 2008-05-28
> **LitusMayol said:**
> ```
litus@mayolets-desktop:~$ cd /home/litus/.wine/drive_c/Program\ Files/DINAMIC\ MULTIMEDIA/PC\ FÚTBOL\ 2000/
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$ wine pcf2000.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f22dac0,0x00000000), stub!
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$ 

```

Tan amb el**DirectX** del **Wine** com amb el **DirectX** del **PC Futbol**; dóna el mateix error...

S'havia de probar, no? hehe

---

### Post by shimoda on 2009-07-25
I algú ha intentat instal.lar una versió més antiga del PC Futbol com la 5, 6 o 7.0?

Jo de fet és que crec que no tinc ni el wine instal.lat... Si aconsegueixo alguna cosa ja ho comentaré per aquí... :P

---


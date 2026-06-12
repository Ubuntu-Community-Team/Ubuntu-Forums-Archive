---
title: "Problema en actualitzar versió [Era: Estrany fenomen d'instal.lació]"
date: 2008-08-17
forum: Catalan Team
---

### Post by Rahefe on 2008-08-17
Hola a tots,

Vaig escriure fa uns pocos dies perquè no sabia connectar l'Ubuntu a Internet... ho he aconseguit amb el cable de xarxa, però aquest matí crec que he ficat la pota i ara no puc accedir a l'ordinador.

Què ha passat?

M'ha preguntat si volia actualitzar a la distribució 8.064 i li he dit que sí.

Quan ja portava molta estona he detectat que es passava como 15 min a la fase de descàrrega d'actualitzacions sense fer res i sense que corregués el comptador de temps, així que he decidit reiniciar i després, en veure que no tornava a la normalitat, apagar.

Què passa ara?

Primer m'indica un missatge que Ubuntu es veurà a baixa resolució de pantalla (un problema que fins ara no m'havia trobat, però el cable de la pantalla sembla ben connectat)

No puc accedir a l'escriptori. Després d'entrar com a usuari es queda el fons de color però sense les icones.

Què podria fer per restaurar-ho?

Moltes gràcies,

Raquel

---

### Post by papapep on 2008-08-17
Pel que comentes sembla que l'actualització no s'hagi completat, amb el qual pots tenir paquets no actualitzats, d'altres que sí, vaja, un poti-poti.

El que jo faria és acabar l'actualització. Al terminal (o sigui, no cal que estiguis a l'entorn gràfic, que en el teu cas no és possible):

```
sudo aptitude update
```

un cop estigui:

```
sudo aptitude dist-upgrade
```

i quan hagi acabat tot (no facis res entremig) a veure si ja ho tens com abans.

---

### Post by Rahefe on 2008-08-17
Un cop teclejat 

sudo aptitude update

em diu 

[sudo]password for usuario:

Però no me deixa escriure res...

---

### Post by indiosincracia on 2008-08-17
el password s'oculta (no es veu) simplement escriu-lo correctament i apreta enter

---

### Post by Rahefe on 2008-08-17
Després d'introduir el password em dóna diversos "No se puede resolver 'es.archive.ubuntu.com"

I tot seguit:

E:dpkg was interrupted, you must manually run 'dpkg--configure -a' to correct the problem
E: No se pudo reconstruir el almacén de paquetes
usuario@usuario-desktop:~$

---

### Post by torracastanyes on 2008-08-17
Doncs això, escriu:

sudo dpkg --configure -a

Aquest problema ja l'hem tingut uns quants, sembla que és un error de l'actualització


(Compte amb els espais)

---

### Post by Rahefe on 2008-08-17
L'últim missatge que apareix és

Generating locales...
en_AU.UTF-8...

Ha de sortir alguna informació més o s'ha completat?

---

### Post by torracastanyes on 2008-08-17
No, no s'ha completat. A mí també em va passar i ho vaig solucionar, però no recordo com. Buscaré si ho trobo i t'ho dic.

---

### Post by torracastanyes on 2008-08-17
Prova d'escriure:

sudo apt-get install -f

A veure si amb això ho soluciones. Ja dirás el què.

---

### Post by Rahefe on 2008-08-17
Mmm... no passa res... potser perquè ho he posat a sota dels punts suspensius, però no em deixa posar-me a sobre amb el ratolí i esborrar-ho...

---

### Post by torracastanyes on 2008-08-17
Ho has d'escriure después d'això:

usuario@usuario-desktop:~$

Si encara està encallat, reinicia.

---

### Post by manelfus on 2008-08-17
Per solucinar-hi lo de LOCATES(son els paquets dels idiomes) has de engejar-hi desde l'anterior versio del kernel (la 19 o la 20) i fer el "dpkg -- configure -a" com tan dit mes a dalt.
A mi tambe va passarme i ho vaig solucionar aixi

[http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679)

[http://ubuntuforums.org/showthread.php?t=867059](http://ubuntuforums.org/showthread.php?t=867059)

que tingues sort salut!!!

---

### Post by Rahefe on 2008-08-17
Perdoneu que no sé on són els dos punts i el símbol següent (mai me'n recordo com es diu) amb la configuració del teclat de Terminal...

---

### Post by papapep on 2008-08-17
No Raquel, el que t'han volgut dir és que has d'escriure les ordres quan el terminal les està esperant, quant et mostra el teu nom d'usuari i d'ordinador. En el meu cas, em mostra això:

```
papapep@awacs:~$ 

```

No ho has d'escriure tu això, ho fa l'ordinador sol. Si no ho fa, reinicia i torna a començar.
Les ordres les has de posar a continuació del símbol del dólar que et mostra l'ordinador. M'explico?

---

### Post by Rahefe on 2008-08-17
Hola,

He tornat a provar-ho des del principi però no puc avançar quan veig escriure

sudo apt-get install -f

(No apareix el meu nom d'usuari i ordinador davant)

Probaria una alternativa si sabés què es el kernel i sobre tot on és (perdoneu si sóc usuària usuària, però m'he apuntat a Ubuntu no per coneixements sinó per ganes).

Una altra idea... es pot tornar al principi i no intentar acabar amb l'actualització?

Moltes gràcies

---

### Post by indiosincracia on 2008-08-17
kernel és el nucli de linux, quan inicies l'ordinador pocs segons després de la bios t'apareix la paraula "grub" immediatament prem la tecla "Esc" i aquí veuràs les versions del kernel que tens instal·lades...

---

### Post by torracastanyes on 2008-08-17
En els enllaços d'en Manel està molt ben explicat.
Només reinicia la màquina i apreta la tecla "Esc" uns quants cops abans que surti la pantalla d'ubuntu (just quan s'encén la llumeta del teclat).
Et sortirà una llista, amb la fletxa avall vés a la tercera linia i apreta "enter".


Perdó, t'he trepitjat

---

### Post by Rahefe on 2008-08-17
Bé, he provat a anar a Kernel, i, seguint les indicacions linkades per Manel, he arribat fins al Terminal i escrit manualment 

dpkg --configure -a

Em diu

dpkg: la operación solicitada precisa privilegios de superusuario

Què vol dir?

Gràcies

---

### Post by indiosincracia on 2008-08-17
sudo dpkg --configure -a

---

### Post by Rahefe on 2008-08-17
Vale, i un cop teclejat sudo... i apareguda la info de configuració, em torna a aparèixer usuario@usuario...

Quin seria el següent pas?

---

### Post by torracastanyes on 2008-08-17
Si has entrat la ordre sencera i torna a apareixer l'usuari, vol dir que ja està!

Reinicia la màquina i a veure si ja està tot a lloc

---

### Post by Rahefe on 2008-08-17
Per fi!

Moltes gràcies a tots!

Ara ja no se m'oblidarà la importància del kernel :>

---

### Post by torracastanyes on 2008-08-17
Has tingut una iniciació una mica sobtada, pero te n'has sortit molt bé. 

Felicitats i que ho disfrutis!

---

### Post by tanreb20 on 2008-09-15
Ei!!!!

No t'oblidis de marcar el post com a SOLUCIONAT!!!!

Per fer-ho vés a editar el post,  thread tools i marca la opcio mark as solved

---

### Post by Carolus67 on 2008-09-29
Jo tambe ho he pogut solucionar, gracies.

---


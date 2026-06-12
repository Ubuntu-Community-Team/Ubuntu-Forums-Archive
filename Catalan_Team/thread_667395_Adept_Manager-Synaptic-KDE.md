---
title: "Adept Manager-Synaptic-KDE"
date: 2008-01-14
forum: Catalan Team
---

### Post by prostata on 2008-01-14
Seguint el fil que parla sobre llançament del Kde4 que m'ha semblat extraordinari pel seu contingut i pel que en sabeu, "collons", he decidit establir com a predeterminat a l'inici de sessió amb l'escriptori KDE, s'ha de provar de tot.

Provant, provant he vist que quan vull arrencar tant synaptic com adept manager, cap dels dos arrenquen, el cursor dona la senyal de "estic treballant" però no termina d'arrencar....

Em podeu ajudar, si us plau....gràcies

---

### Post by pespin on 2008-01-14
Prova a executar-los des de la terminal a veure si diu alguna cosa:)

---

### Post by prostata on 2008-01-14
Si, abans m'he oblidat; per consola puc invocar synaptic, però no així Adept Manager

aquí un resum de Adept Manager

josep@josep-desktop:~$ sudo Adept Manager
sudo: Adept: command not found
josep@josep-desktop:~$

---

### Post by prostata on 2008-01-14
Disculpes, aquí resum de synaptic

josep@josep-desktop:~$ sudo synaptic
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by orestesmas on 2008-01-14
> **prostata said:**
> 
josep@josep-desktop:~$ sudo Adept Manager
sudo: Adept: command not found


Quan fas això estàs fent malament dues coses:

[LIST=1]
[*]Estàs invocant un programa que es diu "Adept" amb un paràmetre que es diu "Manager", i tu no vols fer això.
[*]Probablement el nom del programa no portarà majúscules.
[/LIST]

De fet, el programa es diu "adept_manager", i no és del KDE4 sinó que el fa kubuntu. Suposo que aquesta versió funcionarà també amb el KDE4 sense problemes, però tot depèn de com hagis instal·lat la KDE4 i de si has eliminat les llibreries del KDE3.

Resum: t'has de fixar més amb els missatges. El bash t'ho deia clarament: "Command not found", doncs no està instal·lat, no és al path o l'estàs invocant amb un nom erroni.

---

### Post by prostata on 2008-01-15
> **orestesmas said:**
> Quan fas això estàs fent malament dues coses:

[LIST=1]
[*]Estàs invocant un programa que es diu "Adept" amb un paràmetre que es diu "Manager", i tu no vols fer això.
[*]Probablement el nom del programa no portarà majúscules.
[/LIST]

De fet, el programa es diu "adept_manager", i no és del KDE4 sinó que el fa kubuntu. Suposo que aquesta versió funcionarà també amb el KDE4 sense problemes, però tot depèn de com hagis instal·lat la KDE4 i de si has eliminat les llibreries del KDE3.

Orestesman, gracies per les teves explicacions, ja que el segur és que hagi estat jo qui no s'ha explicat bé, Jo el que vaig instal-lar es kubuntu-desktop  via synaptic, res més i desprès en arrencar cambio la sessió i li dic que em posi escriptori KDE. Això és tot el que faig. No he instal-lat la KDE4, tant sols l'escriptori Kubuntu...

Resum: t'has de fixar més amb els missatges. El bash t'ho deia clarament: "Command not found", doncs no està instal·lat, no és al path o l'estàs invocant amb un nom erroni.

;-) també moltes gràcies pel resum, de veritat, però fins aquí ja havia arribat jo solet, de totes maneres gràcies per l'observació  ;-) de bon rotllo

---

### Post by orestesmas on 2008-01-16
No està fet amb mal rotllo (ja veus que a la meva foto sempre surto somrient :-) ). Llegint i escrivint és molt difícil adonar-se de si l'altre ha reparat en tal o qual detall. A segons qui, aquesta mena de comentaris el poden ajudar a aprendre si els aplica en altres situacions semblants.

---

### Post by prostata on 2008-01-17
> **orestesmas said:**
> No està fet amb mal rotllo (ja veus que a la meva foto sempre surto somrient :-) ). Llegint i escrivint és molt difícil adonar-se de si l'altre ha reparat en tal o qual detall. A segons qui, aquesta mena de comentaris el poden ajudar a aprendre si els aplica en altres situacions semblants.

Gràcies Orestesman....és que no voldria que es  mal-entengui el meu correu. Per cert espero que hagis llegit el meu privat, al respecte. Gràcies[B]

---


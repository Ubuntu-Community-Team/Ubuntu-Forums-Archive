---
title: "[SOLVED] barres"
date: 2008-06-17
forum: Catalan Team
---

### Post by grundt on 2008-06-17
Hola, estava treient programes amb el synaptic i no se que he tret
però ara no em surten les dues barres de l'escriptori, 

com puc tornar a posar les barres ,tenint en compte que no hi son??

---

### Post by papapep on 2008-06-17
El fil que tens dos llocs més avall, parla exactament del mateix problema.

---

### Post by grundt on 2008-06-17
Com puc accedir a la terminal?

a l'escriptori nomes tinc la carpeta

de documents,

ja m'he llegit el post de dues linees més avall,
la veritat es que no l'havia llegit i parla del mateix.

---

### Post by papapep on 2008-06-17
Pots executar-lo fent Alt+F2 i posant a la finestra que et sortirà:

```
gnome-terminal
```

si no et funcionés, pots anar a un tty fent Ctrl+Alt+F1 (per exemple, et serviria des d'F1 fins a F6).
Per tornar a l'entorn gràfic fes Ctrl+Alt+F7.

---

### Post by grundt on 2008-06-17
He accedit a la terminal a traves de la carpeta /usr/bin
he escrit i m'ha respòs:

/usr/sbin/dpkg-reconfigure: ubuntu-desktop no està instal·lat

---

### Post by grundt on 2008-06-17
He provat de posar gnome-panel i apartir d'aqui ho he pogut aconseguir!

Ara el que no surt és la paperera.:confused:

---

### Post by grundt on 2008-06-17
He provat de posar la paperera fent clic dret i afegint al cuadre però em diu:

El quadre ha trobat un problema en carregar "OAFIID:GNOME_Panel_TrashApplet".

---

### Post by papapep on 2008-06-17
> he escrit i m'ha respòs:

/usr/sbin/dpkg-reconfigure: ubuntu-desktop no està instal·lat 

Doncs igual et va bé fer:

```
sudo dpkg-reconfigure ubuntu-desktop
```

(sempre que no facis servir Kubuntu, cas en el qual el paquet es diria kubuntu-desktop)

Quan acabis amb aquest batibull que tens entre mans, podries aprofitar i presentar-te al fil de benvinguda, i fer una bona llegida al fil pels novells.

---

### Post by grundt on 2008-06-17
He provat de posar

grundt@grundt-desktop:~$ sudo dpkg-reconfigure ubuntu-desktop

i em respòn

/usr/sbin/dpkg-reconfigure: ubuntu-desktop no està instal·lat

ja em passaré pel fil, no vull complicar el foro

gràcies

---

### Post by papapep on 2008-06-17
> ja em passaré pel fil, no vull complicar el foro

No compliques pas res.

No entenc com pots tenir un escriptori (si dius que veus un escriptori on posar una paperera) i, en canvi, no tens instal·lat l'ubuntu-desktop (no tens pas instal·lat kubuntu o xubuntu, oi?)

En tot cas, per a instal·lar l'ubuntu-desktop de nou:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by grundt on 2008-06-17
Perfecte, arreglat!

Doncs no se com he desinstal·lat l'escriptori,

he estat desinstal·lant programes amb el synaptic,

el vlc, l'evolution, el serpentine...

Merci

---

### Post by papapep on 2008-06-17
Quan desinstal·les programes, has de mirar SEMPRE quines dependències queden afectades abans d'acceptar ja que, per exemple, juraria que quan intentes esborrar l'Evolution t'arrossega, entre moltes altres coses, l'ubuntu-desktop.

---


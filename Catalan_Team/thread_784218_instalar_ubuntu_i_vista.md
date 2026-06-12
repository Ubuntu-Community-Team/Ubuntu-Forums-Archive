---
title: "instalar ubuntu i vista"
date: 2008-05-06
forum: Catalan Team
---

### Post by trinkus on 2008-05-06
Ja se que em direu que repetixo pero es que a la xarxa no queda res clar (almenys pel que jo he trobat)
Tinc un Laptop nou de trinca de DELL (un inspiron 1525) que he hagut de comprar amb VXXXX instalat perque la versio Ubuntu era mes cara i amb menys prestacions (quina vergonya que fa!). La questio es que he posat el CD de la Hardy i em diu que te problemes per particionar (el gparted no em deixa reduir la particio del VXXXX). 
Per tant, tenint en compte que no vull esborrar el VXXXX (entre d'altes perque l'he hagut de pagar! camufladament i soc molt catala...) quina es la millor estrategia aseguir per instalar urgentment la Hardy?

1.- El Wubi funciona be i treu el mateix rendiment que una instal·lacio diferent?
2.- El GRUB permetra triar el sistema operatiu com tenia abans?
3.- Hi ha algun lloc on es doni informacio clara i concisa (a mes de fiable) sobre els procediments a seguir?

Gracies

---

### Post by menut on 2008-05-06
Hola, trinkus.

Probablement sigui tema de permisos.

Si el Gparted no pot particionar, fes-ho tu mateix des del Hasefroch:

Ho pots fer amb el "Partition Magic" o qualsevol particionador, si es lliure, millor ;)

Amb el programa crees una nova partició sense format, i reinicies l'ordinador amb el cd del Hardy.

Llavors el Gparted veura la nova partició i et deixarà crear a dins tot el necessari per a la instal·lació (swap, etx2/3, etc...)


1-NO dóna el mateix rendiment.
2-SÍ, el GRUB em detectà el Vista a la primera :)
3-Mira [aqui]("http://www.ubuntu-es.org/index.php?q=node/71223") i [aqui]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/").

---

### Post by trinkus on 2008-05-06
Gracies menut!

Al final amb un particionador anomenat ParagonPartitionMagic he pogut fer lloc al disc dur, no ho he provat amb el Hasefroch, pero deu funcionar, espere. Despres ha estat com tu dius, instalar la Hardy... i el GRUB funciona perfecte! Executa els dos (sense reparar res). Ara em toca passar el meu \home del portail vell i... endavant! Visca la Hardy! Ara ja podre veure els efectes del Compiz, l'AWN i tota la pesca que fins ara m'impedien treballar...

Gracies pel consell de la wubi... he estat a punt...

PD: Com es fa per posar que ja esta resolt???

---

### Post by kukat on 2008-05-06
abans estava a dalt a la dreta, en "Thread Tool", però ara ja no ho encontre:confused: On està?

---

### Post by menut on 2008-05-06
Amb el nou redisseny del fòrum, ha desaparegut. Esperem que ho posin prompte.

Ja n'hem parlat [aqui]("http://ubuntuforums.org/showthread.php?t=762416&highlight=nous+f%F2rums&page=3").

---


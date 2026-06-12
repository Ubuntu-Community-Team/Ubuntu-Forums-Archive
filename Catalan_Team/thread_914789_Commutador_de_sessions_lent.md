---
title: "Commutador de sessions lent"
date: 2008-09-09
forum: Catalan Team
---

### Post by LitusMayol on 2008-09-09
Bones familia!

A veure, primer de tot: no és un problema greu. Més aviat és una qüestió per tal de millorar l'eficiència. 

El commutador de sessions (no sé si es diu així però sóna bé i descriu el que fa, veure arxiu adjunt) em va lent. Quan dic que em va lent em refereixo a que si canvio d'usuari sense tancar la sessió actual el canvi és lent i farregós (el més típic es passar de la sessió *Peque* a *Litus* o la inversa). La sessió nova s'obre molt lentament i després funciona mooooolt lenta (m'ha recordat a quan utilitzava a la vegada el **Reproductor de Windows Media** i el **Photoshop**, com si fos un **Windows 98** amb moltes fonts al seu processador de texts, m'explico?). Per summum, quan tanco/canvio la sessió i torno a la inicialment oberta (que resta oberta, doncs és canvi de sessió no tancar i obrir una altra) aquesta es comporta de la mateixa manera: lenta, es col·lapsen els programes (allò de que es tornen grisos i en blanc i negre)...

Sabeu si hi ha alguna manera de fer que el canvi sigui més fluid i que la nova sessió oberta (i després l'anteriorment oberta) no vagin tan lentes?


Merci a tothom de nou!

[COLOR="Silver"]
(descric el comportament sense dades de terminal ni res perquè no sé com fer-ho)[/COLOR]

---

### Post by papapep on 2008-09-09
Home!! ja et trobava a faltar!!! :-P
([espero que no ens fallis dissabte vinent, eh]("http://ubuntuforums.org/showthread.php?t=912167")!!)

Jo pregunto:

 - quina màquina (especificacions) teniu?
 - quantes sessions simultànies teniu obertes i quines/quantes aplicacions a cadascuna?
 - en fer un "top" o "htop" a un terminal, què et diu d'ocupació de RAM i de processador?

---

### Post by LitusMayol on 2008-09-09
Ara mateix només tinc la meva sessió oberta. Posant *top* tinc aquest resultat:
```

top - 13:42:28 up  1:19,  3 users,  load average: 0.47, 0.51, 0.42
Tasks: 130 total,   2 running, 128 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.7%us,  3.3%sy,  0.0%ni, 82.7%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    904288k total,   888340k used,    15948k free,    33532k buffers
Swap:  1461872k total,      196k used,  1461676k free,   429344k cached
```


Però el tema és que fins hi tot tenint poca cosa oberta (ni **Firefox**s, ni **aMule**s, ni cosetes així..) va lent...  Però si em dones 1 minutet em poso a la sessió del meu germà.

---

### Post by PequeMayol on 2008-09-09
Ja hi som!

Ara a hi ha la sessió "*Litus*" oberta (però commutada) i la sessió actual ("*Peque*"). Si introdueixo *top* al terminal la sortida és:
```

top - 13:51:49 up  1:29,  3 users,  load average: 0.36, 0.64, 0.51
Tasks: 173 total,   5 running, 168 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.7%us,  3.0%sy,  0.0%ni, 81.9%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    904288k total,   890820k used,    13468k free,     6708k buffers
Swap:  1461872k total,    44428k used,  1417444k free,   197464k cached

```


Com sempre passa en aquests casos, ara mateix funciona de perles. Però tornaré a alternar deixant aquesta sessió oberta amb un **Firefox** (que té ara mateix 5 pestanyes). A veure si al retornar a la meva em passa el que descric abans.

---

### Post by LitusMayol on 2008-09-09
Perfecte!
Acabo de tenir un error com déu mana! (xD)

No és greu. Però enlloc de commutar la sessió... txan-txan! Ha començat a carregar les barres de GNOME (superior i inferior, però sense mostra les icones) i el ratolí. Però no ha arribar ni a carregar el fons d'escriptori ni els icones de les barres (ni els de l'escriptori). Aleshores ell solet m'ha portat al GDM (és diu així el gestor d'entrada a les sessions, oi?) i m'ha mostrat les sessions amb un "*Ja entrat*" sota la sessió *Peque* i la meva sessió tancada! Aleshores he escrit la contrasenya (no, no us la diré!) i ha entrat normal i corrent (això si, com si acabés d'engegar l'ordinador).


Alguna idea?

---


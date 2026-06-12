---
title: "tractament de dvd+rw"
date: 2008-02-09
forum: Catalan Team
---

### Post by climent on 2008-02-09
Necessito treballar amb un dvd+rw (esborrar, formatar, gravar, etc), i he d'esborrar uns arxius que ja hi són dintre, però em diu que necessito permisos de root. Com ho he de fer? I, com puc arrencar l'ordinador com a root?

---

### Post by lluisanunez on 2008-02-09
No, no et cal arrencar l'ordinador com a root, només el programa. Obre un terminal, i tecleja
```
sudo <nomdelprograma>
```

---

### Post by papapep on 2008-02-09
O des de l'entorn gràfic, i que no senti precedent :-D, amb **ALT+F2** i ficant:

```
gksudo nom_del_programa
```

per a executar-lo temporalment com a administrador.

---

### Post by elbuit on 2008-02-10
supose que et referiras a un DVD+RW formatat amb udf,fat, o ext2/3, per que si es iso no ho pots borrar directament, com quan borres un arxiu del disc dur.
En cas de ser el primer cas seria una questio de permisos, i tal com t'han dit abans sols cal escalar privilegis amb sudo o gksudo, per exemple gksudo nautilus.
En el segon cas, hauras d'emprar k3b o qualsevol altre programa de grava, però no podras borrar fisicament arxius.

---


---
title: "[SOLVED] Desinstal·lar kernel antic"
date: 2008-10-16
forum: Catalan Team
---

### Post by Daerun on 2008-10-16
Això és una cosa que es va comentar en un tema fa uns quants mesos... però no he sigut capaç de trobar-ho :confused:
Fa poc em va entrar la actualització de l'últim kernel, el 2.6.24.21. Com que sempre deixo el kernel anterior per una recomanació que vaig llegir per aqui, doncs el 19 es queda on és per si de cas, que funcionava bé, però també tinc el 16, que és el que vull eliminar; com ho faig?

---

### Post by papapep on 2008-10-16
Doncs desinstal·les el paquet amb la teva eina preferida: synaptic, aptitude, apt-get...

```
sudo aptitude purge linux-image-versió_del_paquet
```

pots fer abans un:

```
sudo aptitude search linux-image-|grep ^i
```

per veure els que tens instal·lats i decidir quin/s et vols carregar.

---

### Post by Daerun on 2008-10-17
Tan sencill que no se m'havia acudit :lol: Gràcies mestre papapep

---


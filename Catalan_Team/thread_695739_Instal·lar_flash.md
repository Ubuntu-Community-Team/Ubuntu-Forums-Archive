---
title: "Instal·lar flash"
date: 2008-02-13
forum: Catalan Team
---

### Post by oriolconstanti on 2008-02-13
Hola, sóc nou en l'ubuntu, me'l vaig instal·lar fa poc i tot just començo a veure com funciona. 
El cas és que a l'hora d'Instal·lar el flash player des d'algunes pàgines, segueixo les instruccions de la pestanya que apareix, però cada cop m'assenyala que no troba el flashplugin-nonfree: "can not find flashplugin-nonfree"


Com ho puc fer, i com puc instal·lar altres plugins ??

Mercès!

---

### Post by jan quark on 2008-02-13
in terminal run this
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by oriolconstanti on 2008-02-13
Ja ho faig i em va tot bé, però al final hi torna a posar: [I]E: No s'ha pogut trobar el paquet flashplugin-nonfree
[/I]

---

### Post by CarlesOriol on 2008-02-13
Obre el synaptic i a paràmetres Dipòsits (abans no deia repositoris) comprova que tinguis totes les marques a programari ubuntu i a actualitzacions com a mínim les dos primeres.

---


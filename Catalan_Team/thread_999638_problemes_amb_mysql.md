---
title: "problemes amb mysql"
date: 2008-12-02
forum: Catalan Team
---

### Post by jaumety on 2008-12-02
Hola bones, acabo d'instal·lar un servidor amb ubuntu server 8.04 amb el mysql 5.0.67 i l'ssh. Dins la meva xarxa tot sembla funcionar correctament però quan connecto des de l'exterior a través d'internet em va molt lent, he pensat que que el problema és al mysql, i m'agradaria probar amb una versió de mysql més antiga, que sabeu com es pot fer?. O si penseu que el problema no és aquest que podria probar?
Gràcies

---

### Post by papapep on 2008-12-02
Si el mysql et va bé en local, què et porta a concloure que té la culpa de la lentitud en remot?

A banda, no ens dónes cap dada objectiva, ni de la rapidesa en local ni de la lentitud en remot, ni de quines operacions fas per provar-ho.
Jo votaria per un simple problema de comunicacions d'on estiguis amb el client, respecte la pujada del teu servidor. Tingues present que en local, en el pitjor dels casos, tens 10 Mb, i en remot, excepte que paguis una passada al mes, només tens 300 Kb (amb sort). Ja ho tens present això?

---

### Post by jaumety on 2008-12-02
La única dada que puc donar que tampoc és obectiva és que amb la versió ubuntu 6.06 anava més ràpid, d'altre banda no se com comprovar que efectivament va més lent ja que el mytop no em funciona correctament a la versió 8.04, que saps d'alguna altre eina per verificar la conexió?

---


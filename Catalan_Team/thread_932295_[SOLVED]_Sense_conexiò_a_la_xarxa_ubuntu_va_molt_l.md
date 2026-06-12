---
title: "[SOLVED] Sense conexiò a la xarxa ubuntu va molt lent"
date: 2008-09-28
forum: Catalan Team
---

### Post by Quepotser on 2008-09-28
Bon dia a tothom: no sé si te gaire interès la meva pregunta, o si ja està contestada en algún altre lloc (que jo no he sabut trobar), però per què l'Ubuntu va tant lent quan, pel que sigui, no tens conexió a Internet. Hi ha alguna manera de que això no passi?. Per a mi és una cosa "important" ja que el meu suministrament elèctric prové de fonts alternatives i no em sobra ni un watt i l'aparell que fa possible que pugui tenir internet en xucla bastants, i la veritat, hi ha moltes voltes que per fer sogons quines coses, no necessito estar conectat.

Gràcies per endevant.

---

### Post by CarlesOriol on 2008-09-28
Això no és així. L'ubuntu no va més lent quan no està connectat a la xarxa.

Caldrà que ens donis més detalls del que passa al teu aparell per veure si et podem ajudar.

---

### Post by RainCT on 2008-09-28
A mi també em passava fa temps, i la veritat és que era bastant empipador. Lamentablement no recordo exactament com ho vaig poder solucionar, només que era algun problema amb el GNOME...

Digue'ns quina versió de l'Ubuntu fas servir i adjunt el teu /etc/hosts, a veure.

---

### Post by Quepotser on 2008-09-28
Hola.
CarlesOriol: la veritat és que poca més informació et puc donar del què li passa al meu ordinador. L'únic que puc dir és el que ja he dit al principi: Ubuntu (si més no en el meu cas) va súper lent quan no hi ha conexió a internet.

RainCT: la versió del meu Ubuntu és la 8.04 i el /etc/hosts:

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
82.198.114.58 ip6-localhost ip6-loopback

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by papapep on 2008-09-28
A banda de que puguis tenir altres problemes, et falten aquestes dues línies a /etc/hosts:

> 127.0.0.1 localhost
127.0.1.1 el_nom_del_teu_ordinador


I evidentment que el tema de la lentitud no té absolutament res a veure amb la connexió a internet.

---

### Post by Quepotser on 2008-09-28
Això sí que és rapidesa. Una pregunta: a quin lloc (línea), s'han d'introduïr aquestas líneas? A veure si ho arreclo (arreclem) d'una vegada. Merces.

---

### Post by papapep on 2008-09-28
No té importància la ubicació dins el fitxer, però pots ficar-les al principi, és on solen ser.

---

### Post by Quepotser on 2008-09-29
Bon dia.

Oli en un llum. La cosa ha anat de conya i ja tinc l'Ubuntu funcionant a tota canya sense haver d'estar conectat. Merci a tots. Ho marco com a sol·lucionat.

---


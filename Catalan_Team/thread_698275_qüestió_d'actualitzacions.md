---
title: "qüestió d'actualitzacions"
date: 2008-02-16
forum: Catalan Team
---

### Post by rogespierre on 2008-02-16
llegeixo a la wikipedia que cada sis mesos apareix una nova versió d'ubuntu, quan surti la propera (abril?) com ho actualitzaré? igual que els paquets que actualitzo de tan en tan quan m'avisa, o com?

---

### Post by jodufi on 2008-02-16
Quan arribi l'abril i aparegui la nova Ubuntu 8.04, en el "Gestor d'actualitzacions" t'apareixerà l'opció d'actualitzar a la nova versió. Simplement hi fas clic i se t'actualitzarà tot el sistema a la nova versió. Això també es pot fer des d'un terminal. 

Si vols que aquesta opció no et dongui problemes, és important no fer moltes «guarrades» al sistema (instal·lar paquets que no siguin del repositori i poc confiables, utilitzar l'automatix...).

Com que jo acostumo a tocatejar molt l'ordinador i instal·lar-hi molts programes, el que faig és instal·lar de nou l'Ubuntu i així aprofito per a fer-hi neteja :)

---

### Post by Daerun on 2008-02-16
Ostres, jo que tinc Automatrix y AWN, aleshores..... Què cal fer doncs, arribat el cas?  Hi ha alguna manera de "traspassar" la configuració i els programes instal·lats actualment a la nova versió?

---

### Post by papapep on 2008-02-16
L'automatix el treus del /etc/apt/sources.list i fas un:

```
sudo aptitude update
```

i després un:

```
sudo aptitude safe-upgrade
```

si no tens cap incongruència de paquets, estaràs com abans de posar-te'l.

Respecte l'AWN no sé si et pot portar problemes o no. Pel fet de ser de fora dels repositoris oficials no significa de manera directa que sigui nociu (l'automatix per ara si...).

---

### Post by eduardsola on 2008-02-16
I pel tema de la música i això, quan actualitzi a la nova versió, tot quedarà igual, les mateixes carpetes i tot, no?

---

### Post by papapep on 2008-02-16
Eduard: no sé ben bé a què et refereixes en concret amb "pel tema de la música i això", però pensa que en principi les actualitzacions només, literalment, actualitzen les versions dels executables dels paquets, no toquen ni els fitxers de configuració a no ser que tu li diguis que si que ho faci quan t'ho pregunta. O sigui, que no, que no ha de tocar res del que suposo que parles.

---

### Post by eduardsola on 2008-02-16
> **papapep said:**
> Eduard: no sé ben bé a què et refereixes en concret amb "pel tema de la música i això", però pensa que en principi les actualitzacions només, literalment, actualitzen les versions dels executables dels paquets, no toquen ni els fitxers de configuració a no ser que tu li diguis que si que ho faci quan t'ho pregunta. O sigui, que no, que no ha de tocar res del que suposo que parles.

Ah val x)

Sí, em referia als arxius .ogg

---

### Post by jodufi on 2008-02-16
També s'ha de dir que hi ha l'opció de no actualitzar a la 8.04 i continuar amb la 7.10 Encara hi hauran actualitzacions d'aquesta distribució fins a l'abril del 2009.

És a dir, si tot en funciona perfectament i no tens cap necessitat d'anar a l'última continua amb la 7.10. Tindràs tot un any per decidir quan vols actualitzar :)

---

### Post by SiscoGarcia on 2008-02-17
Això és cert jodufi, però mentrestant ja hauran sortit les versions 8.10 i 9.04 (si no hi ha contratemps); amb la qual cosa per estar a l'última (si és que es vol) caldrà fer... 3 actualitzacions!

---

### Post by lpargemi on 2008-02-17
De qualsevol manera hi ha actualitzacions que tenen suport a més llarg termini. Això em penso que vol dir que Canonical manté les actualitzacions durant més temps.
Suposo que aquestes son les ideals per a qui no té cap necessitat especial d'estar a l'última [com em passa a mi, que el canvi pel canvi, sobretot d'una cosa que ja em funciona, em fa una mica d'urticària].

La següent versió, 8.04, hauria de ser d'aquestes.

---

### Post by SiscoGarcia on 2008-02-17
Sí lpargemi, la 8.04 està previst que sigui el que en diuen LTS (long term support), que vol dir que tenen "suport" durant 3 anys les versions d'escriptori i 5 anys les versions servidor. En aquests moments encara s'acutalitza l'única versió LTS que s'ha fet d'ubuntu, la 6.06. I, evidentment, no cal tocar una cosa que funciona; el que passa és que alguns no sabem tenir les mans quietes, encara que no tinguem prou coneixements (ni coneixement, suposo):)

---

### Post by albert-I on 2008-02-18
Parlant d'actualitzacions. Amb el 8.04 tot passarà el Kde passarà al 4 o conviuran amb el 3.5? Algú sap alguna cosa?

---

### Post by CarlesOriol on 2008-02-18
El kde 4 de moment està en una fase bastant experimental encara que ja hagin sortit les primeres versions oficials.

El hardy seguirà amb la serie 3.5

---

### Post by albert-I on 2008-02-20
Em sembla.
Gràcies, he vist que si, es manté el 3.5.9
Ja el tinc
Com m'agrada això
[COLOR="DarkRed"]a maintenance release for the latest generation of the most advanced and powerful free desktop for GNU/Linux and other UNIXes.[/COLOR]

Però suposo que en un futur pròxim es deixarà el 3.5.9 i tots anirem amb el 4 pq com que hi ha allò del Qt4 i les altres coses noves.

---

### Post by CarlesOriol on 2008-02-21
Tots en kde!!!! Quin horror!!!!

Au... mira la darrera entrada del wiki parides que us he dedicat als kdeaires.

[https://wiki.ubuntu.com/CatalanTeam/Parides](https://wiki.ubuntu.com/CatalanTeam/Parides)

---


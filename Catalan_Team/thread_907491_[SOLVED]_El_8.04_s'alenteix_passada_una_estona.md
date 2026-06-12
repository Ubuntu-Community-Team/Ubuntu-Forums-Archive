---
title: "[SOLVED] El 8.04 s'alenteix passada una estona"
date: 2008-09-01
forum: Catalan Team
---

### Post by Quepotser on 2008-09-01
Hola a tothom.

Tinc un problema al qual no he sabut trobar sol.lució: quan fa una estona llarga que tinc l'ordinador en marxa (més de dues hores), poc a poc, es va alentint, fins que al final puc estar minuts abans no se m'obri una finestra; poso per cas Llocs > Carpeta d'inici. En casos extrems la màquina es queda parada del tot. No sabria dir si això m'ho ha fet sempre perquè habitualment no la tinc engegada tanta estona, però ùltimament he estat tirant de l'aMule i he tingut en marxa l'andromina moltes hores i he pogut adonar-me'n. Intentant averiguar que podia estar causant aquest fenòmen ho he provat amb diversos programes i amb tots em fa el mateix. 
Quan engego l'ordinador, el consum de memoria no supera gaire els 400 Mb, pero fent un **top**en una consola cada cert temps, i fent servir tota l'estona els mateixos programes (aMule i Firefox) es veu perfectament com va pujant la memòria utilitzada. Ara, avui, he activat la swap i de moment, aguanta. Jo he estat mirant per una colla de forums i remenant pel Google però no n'he pogut esbrinar la causa. Si algú en té alguna idea de per què passa això li agrairia molt que me'n faci cinc cèntims. Gràcies per endavant.

---

### Post by Quepotser on 2008-09-01
Perdò. M'oblidat de dir-vos que la memòria és de 1GB i que la swap en té assignada un altre tant.

---

### Post by papapep on 2008-09-01
A banda de fer un memtest per assegurar que no tens cap problema de RAM, també podria ser sobre-escalfament de la gràfica, processador o similar.
Seria interessant que comprovessis que els ventiladors et funcionen correctament i que la pasta que hi ha entre els dissipadors i els xips que refrigeren està bé.

També pots executar un "top" (tal qual, sense cometes, clar...) a un terminal i veure si hi ha algun procés que es menja la memòria o que ocupa tot el processador.

---

### Post by Quepotser on 2008-09-02
Bon dia papapep. Fet el memtest no sembla haver-hi cap problema. En quant als ventiladors sembla que tampoc vagin malament. No he mirat la pasta refrigerant. Fet el "top", quan arrenco al matí em dona un ús de la memòria de poc més de 400 MB; vint minuts després i sols amb el Firefox engegat em diu això que t'adjunto.

---

### Post by Quepotser on 2008-09-02
Bé, sembla ser que no s'ha adjuntat el resultat del top. Ho tornaré e provar. La veritat és que no sé si s'ha enganxat la cosa aquesta. Per si un cas, en aquest moment la memória ocupada es de 552 MB i continua pujant sense que hi hagi cap més programa en marxa.

---

### Post by Quepotser on 2008-09-03
Finalment he desmontat l'ordinador per revisar l'estat de la pasta refrigerant i m'ha semblat que estava en bon estat. A més a més, l'interior de la màquina era força net; jo m'esperava trobar-hi més sutge, però no n'hi havia. He anat provant coses diverses i he trobat que si bé hi ha programes que crec que consumeixen un excés de memòria (Firefox), el que fa que l'ordinador s'alenteixi i acabi parant-se és l'aMule. Tinc la versió SVN 2.2.0. Ho deixo aquí per si a algú li passa el mateix o en sap la causa o la sol·lució.

---

### Post by Quepotser on 2008-09-05
Finalment, després de molt llegir i provar coses sembla que he trobat la sol·lució al meu problema, si més no, ho sembla; fa deu hores i escaig que tinc l'ordinador en marxa amb l'amule funcionant, el Firefox treballant, veient pel·licules o escoltant música i continua anant bé.
L'únic que li he fet  ha sigut deixar-li la velocitat tant de pujada com de baixada al 80% de la capacitat nominal del meu ample de banda. A  efectes pràctics no he perdut velocitat i sí que he guanyat en temps total de conexió per què ja no s'ha tornat a penjar.
Aquí ho deixo per si a algú li va bé i pot estalviar-se un maldecap.

---

### Post by SiscoGarcia on 2008-09-07
> **Quepotser said:**
> Finalment, després de molt llegir i provar coses sembla que he trobat la sol·lució al meu problema, ...
Aquí ho deixo per si a algú li va bé i pot estalviar-se un maldecap.

Que tal si marques el fil com a resolt?

Ja saps "Thread Tools" + "Mark this thread as solved" ;)

---


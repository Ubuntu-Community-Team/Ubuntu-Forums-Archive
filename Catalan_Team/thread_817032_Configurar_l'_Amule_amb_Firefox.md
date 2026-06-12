---
title: "Configurar l' Amule amb Firefox"
date: 2008-06-03
forum: Catalan Team
---

### Post by JordiSF on 2008-06-03
-Hola, He intentat de configurar l' Amule amb Firefox per poder descarregar directament clicant a links i he seguit els següents passos:

   1. Obriu el Gestor de paquets Synaptic (Per fer-ho aneu a Sistema\Synaptic Package Manager)
   2. Un cop dins cliqueu Search i poseu ed2k per cercar els paquets de amule.
   3. Si no està ja instal.lat instal.leu el paquet amule-utils (Si no teniu amule instal.lat sel.leccioneu tb el paquet amule)
   4. Un cop instal.lat obriu Firefox i escriviu about:config a la barra d'adreces
   5. Cliqueu amb el botó dret i trieu Nou\Cadena. Entreu el text network.protocol-handler.app.ed2k i doneu-li el valor /usr/bin/ed2k
   6. Cliqueu novament amb el botó dret i trieu Nou\Booleà. Entreu el text network.protocol-handler.external.ed2k i doneu-li el valor true.

-Després de fer tot això quan clico un link em diu: "Aquest enllaç cal obrir-lo amb una aplicació" i llavors a **Trieu** vaig a l' **Amule** però no sé què triar.

Em podeu ajudar?

Gràcies i salut

---

### Post by pespin on 2008-06-03
Prova posant-hi "/usr/bin/ed2k"

---

### Post by JordiSF on 2008-06-04
> **pespin said:**
> Prova posant-hi "/usr/bin/ed2k"

Ho he repassat i això ja ho vaig posar tal i com poso al pas 5 a dalt a la pregunta. A veure si hi ha alguna altra sol.lució.

Gràcies

---

### Post by pixatintes on 2008-06-04
La ordre ed2k esta al paquet amule-utils, comprova que el tinguis instal·lat.

També pots fer servir aquest complement de firefox, [Firefox MLdonkey/eMule/aMule Protocol Handler]("http://www.informatik.uni-oldenburg.de/~dyna/mldonkey/"), jo el faig servir per l'mldonkey.

---

### Post by JordiSF on 2008-06-07
> **pixatintes said:**
> La ordre ed2k esta al paquet amule-utils, comprova que el tinguis instal·lat.

També pots fer servir aquest complement de firefox, [Firefox MLdonkey/eMule/aMule Protocol Handler]("http://www.informatik.uni-oldenburg.de/~dyna/mldonkey/"), jo el faig servir per l'mldonkey.

Si que tenia instal.lat el paquet amule-utils i tampoc, probaré el complement aquest a veure què tal.

Gràcies

---


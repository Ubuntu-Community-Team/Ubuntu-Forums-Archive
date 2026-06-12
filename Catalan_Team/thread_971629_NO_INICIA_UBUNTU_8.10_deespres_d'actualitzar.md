---
title: "NO INICIA UBUNTU 8.10 deespres d'actualitzar"
date: 2008-11-05
forum: Catalan Team
---

### Post by ferreret on 2008-11-05
Hola, tenia instal·lat el feisty i anit passada vaig instal·lar l'actualització cap al 8.10. La instalació va anar be, però un cop reiniciat,, i despres de demanar-me usuari i contrasenya, l'ubuntu es queda aturat sense fer res en la pantalla blau cel que apareix normalment segons abans d'iniciar-se el S.O., ni tan sols es sent la musiqueta d'entrada. En canvi, enmode GNOME a prova d'errors sí entra, però no sé què he de fer des d'allà.


  què puc fer per a arreglar-ho? hauré de formatar :( Preferiria no fer-hgo, perquè també tinc windows. Per favor ajudeu-me. Tinc descarregat el livecd, imagin que alguna cosa s'hauria de poder fer des d'allà

---

### Post by SiscoGarcia on 2008-11-05
Si l'actualització et va anar bé com dius, t'hauria de funcionar, diria jo.

Pel que dius suposo que no veus ni la pantalla inicial amb les diverses possibilitats d'arrencada (el menú del grub), és així?

Potser que introdueixis el CD autònom i miris d'editar el fitxer /boot/grub/menu.lst a veure què hi tens. Quan ho hagis fet, enganxa'ns el resultat ací.

Per editar pots fer servir la comanda "gedit /boot/grub/menu.lst" sense cometes des de consola (Aplicacions>Accessoris>Terminal).

---


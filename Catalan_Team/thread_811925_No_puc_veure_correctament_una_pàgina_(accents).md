---
title: "No puc veure correctament una pàgina (accents)"
date: 2008-05-29
forum: Catalan Team
---

### Post by sianeu on 2008-05-29
Es estrany per que es en l'única pàgina en que em passa. Tots els accents, tambè en les majúscules (en castellà ?) es veuen com interrogants.

[http://www.carreteros.org/normativa/ehe/ehe.htm]("http://www.carreteros.org/normativa/ehe/ehe.htm")

Uso el Hardy català d'aquí.
Us passa a vosaltres?, sabeu el problema?

Salut

---

### Post by sianeu on 2008-05-29
Ja està arreglat. El problema venia de la web de gmail: quan he obert la pàgina desde gmail (me l'han enviada) es veia malament, igual que una altre oberta desde el menú d'aquesta. Quan desprès m'he donat compta que les demès es veien totes bè, he netejat les cookis i tot solucionat. 

De tota manera es raro, oi?

Salut

---

### Post by oriolsbd on 2008-05-29
El problema podia ser que la pàgina està codificada en ISO i, per algun motiu que desconec, el gmail te la intentés obrir en UTF-8. Si et torna a passar, pots canviar la codificació en que veus la pàgina fent des del Firefox:

Visualitza -> Codificació de caràcters -> Occidental (ISO-8859-1)

Salut!

---

### Post by sianeu on 2008-06-02
Ha tornat a passar. Ara en una página d'un manual HTML.
Potser que s'hagi desconfigurat alguna cosa del firefox?

 La soluciò del oriolbsd funciona, però s'ha de fer a cada pàgina del index del manual, i es pesat.

El firefox, quan passa això utilitza una codificaciò Unicode UTF-8, però normalment utilitza Occidental ISO-8859-1.

Salut

---

### Post by oriolsbd on 2008-06-02
Hola, Sianeu.

Crec que això deu ser perquè tens activada la detecció automàtica i el Firefox es deu pensar que la pàgina està codificada en UTF-8. Pot ser que el tinguis posat com a predeterminat. Prova a fer el següent:

Ves a "Visualitza -> Codificació de Caràcters -> Personalitza". A mà dreta hi veuràs les codificacions que tens actives. Si no tens la codificació ISO com a predeterminada, mou-la a dalt. Crec que amb això t'hauria d'anar.

Si tot i així no et funciona, prova a desactivar la codificació automàtica: 

Primer, des de qualsevol pàgina, activa la codificació ISO tal i com indicava en un missatge anterior.
Després, desactiva la detecció automàtica: "Visualitza -> Codificació de Caràcters -> Detecció Automàtica -> Desactivada".

Salut!

---


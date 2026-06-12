---
title: "Caràcters extranys en part de missatges de correu"
date: 2008-02-11
forum: Catalan Team
---

### Post by ffp on 2008-02-11
Hola a tots,

Veureu, tinc un problema als e-mails al evolution, que m'envia elperiodico.com, als texts, el caràcters, accents etc. es veuen bè, però en els enllaços no, tal com copio a continuació:

[I]Si hi ha cap problema llegint aquest email, pot visualitzar-ho al següent enllaç butlleti 
		
Usuari: ffp

Dilluns, 11 febrer 2008
Butlletí generat a 18:00h. 	
	Opini&oacute;	Internacional	Pol&iacute;tica	Societat	Catalunya	Economia
	Tecnologia	Esports	Cultura/Espectacles	Gent	Televisi&oacute;/R&agrave;dio	Quin m&oacute;n

	PORTADA

ACUSATS D'ASSASSINAT I CONSPIRACIÓ
El Pent&agrave;gon demanar&agrave; la pena de mort per al presumpte cervell de l'11-S i 5 sospitosos m&eacute;s
És la primera vegada que la junta militar de Guantánamo presenta càrrecs pels atacs del 2001
[/I]

Les paraules en cursiva son part del missatge, i on haurien d'anar accents etc. surten paraules rares, però sempre son els enllaços. Els enllaços dirigeixen a un servidor a Anglaterra. [http://server-uk.irmworldwide.com/](http://server-uk.irmworldwide.com/)

He provat tots les codificacions de caràcters dels missatges sense cap resultat.

Algú te una idea, es que queda molt lleig.
Tinc Ubuntu Gutsy.
Reenviat a algú amb W$, es veu bè.

Gràcies.

---

### Post by menut on 2008-02-23
Llegint el correu electrònic via web, també tens el problema ?

Si llegint l'email a través del navegador persisteix aquest, llavors el problema no és de l'Evolution, sinó del servidor de El Periódico que no deu tractar bé els enllaços amb accents inclosos.

---

### Post by ffp on 2008-02-23
Gràcies per contestar,

Pel navegador no tinc problemes, i es llegeix be. També algun altre correu, d'altres emissors te el mateix problema, peró el del Periodico es una passada

---

### Post by menut on 2008-02-23
He estat mirant per primera vegada el meu correu amb l'**Evolution**, i tinc un problema semblant al teu: els apòstrofs enllaçats no es mostren bé.

Exemple:
[INDENT]El saló de sessions de l&39Ajuntament de Tortosa va ser ahir al vespre l'escenari d'una xerrada amb una cinquantena d'estudiants de Periodisme...[/INDENT]

Provant amb *Visualitza>Codificació dels caràcters*, he vist que entre "ISO-8859-1", "ISO-8859-15" i "UTF-8" no hi ha cap diferència; persisteix el problema.

He mirat el mateix correu amb el **Thunderbird** i es mostra correctament amb "ISO-8859-1", però amb "UTF-8" no mostra els accents NO enllaçats.:lolflag: :

[INDENT]El sal&#65533; de sessions de l'Ajuntament de Tortosa[/INDENT]

Una solució no gaire pràctica és passar-te al Thunderbird...però seguirem investigant !

---

### Post by rroca1 on 2008-02-24
No l'he fet servir mai, però bé deu tenir on configurar la codificació dels missatges 

:confused:

---


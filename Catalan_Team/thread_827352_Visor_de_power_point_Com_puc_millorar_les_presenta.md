---
title: "Visor de power point? Com puc millorar les presentacions"
date: 2008-06-12
forum: Catalan Team
---

### Post by dguardia on 2008-06-12
Faig servir Ubuntu en exclusiva i la única pega que he trobat és la visualització de presentacions que envia la gent per correu.

Les obro amb l'editor de presentacions de l'openoffice però tinc alguns problemes i plantejo el següent:

-Com ho faig per veure les presentacions directament sense obrir el programa de l'openoffice i pitjar F5? És a dir, com m'ho faig per veure-les directament si són format pps i no ppt i les vull veure directament??

-A vegades, en obrir presentacions de power point amb l'openoffice se'm "desquadren" algunes diapositives. A què es degut? Com ho puc evitar??

-Existeix algun visor de power points per a linux que permeti suplir aquests problemes?

Moltes gràcies a tothom!!

---

### Post by pespin on 2008-06-12
> -A vegades, en obrir presentacions de power point amb l'openoffice se'm "desquadren" algunes diapositives. A què es degut? Com ho puc evitar??

-Existeix algun visor de power points per a linux que permeti suplir aquests problemes?

Potser si que hi ha solucions alternatives, però està clar que la primera solució és utilitzar formats lliures en comptes de formats privatius de Microsoft.
El que no s'acabi de veure tot bé segurament ve donat pel fet que el programa de l'openoffice que obre els powerpoints està fet mitjançant enginyeria inversa perquè no tenen accés al codi font que dóna informació sobre l'estructura d'aquest tipus d'arxius.

---

### Post by orestesmas on 2008-06-14
A banda del que et diu Pespin, els "desquadres" de les diapositives poden tenir l'origen en les fonts: La pràctica totalitat de sistemes windows usen les fonts TrueType de Microsoft, que no són presents "de sèrie" en Ubuntu per problemes legals.

La solució a això és instal·lar tu mateix les fonts de Microsoft, o bé usar les "liberation fonts", que són unes fonts lliures amb una mètrica idèntica a les de Microsoft, per tal de facilitar la interoperabilitat.

Per usar les liberation fonts, instal·la't el paquet "ttf-liberation"

---

### Post by CarlesOriol on 2008-06-15
> **dguardia said:**
> 
-Com ho faig per veure les presentacions directament sense obrir el programa de l'openoffice i pitjar F5? És a dir, com m'ho faig per veure-les directament si són format pps i no ppt i les vull veure directament??


Fes clic amb el butó dret damunt l'arxiu pps > PROPIETATS > obre amb.
Afegeir > ordre personalitzada

**ooffice -impres **

Pots mirar la resta d'opcions vàlides fent:

**man ooffice**

---

### Post by brissels on 2008-06-16
A mi em funciona prou bé això:
ooffice -show %U

L'opció show obre la presentació directament en visualització... encara que li caldria  ser refinada, simplement t'estalvia de prèmer F5, ja que obre igualment en edició el document.

---


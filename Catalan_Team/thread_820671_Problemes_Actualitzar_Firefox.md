---
title: "Problemes Actualitzar Firefox"
date: 2008-06-06
forum: Catalan Team
---

### Post by Rubunter on 2008-06-06
Avui he sentit que ja esta disponible la versio RC1 del Firefox 3. Doncs bé, per tal d'actualitzar-lo he obert el programa com a root, ja que sino la opció per comprovar si hi ha actualitzacions no es pot clicar. 

Una vegada fet aixo he apretat el botó "comprovar actualitzacions" i no n'ha trobat cap. L'he tancat, l'he tornat a obrir com a usuari normal i resulta que m'ha eliminat tots els bookmarks i les contrassenyes guardades i tot plegat. I no nomes això, a més, si torno a guardar bookmarks, quan tanco i torno a obrir el programa no els recorda!
En canvi quan l'obro amb permisos de superusuari tots els bookmarks apareixen i tot sembla normal. Que creieu que he fet malament? i com podria solucionar ho?

---

### Post by lpargemi on 2008-06-07
Segurament al obrir com a root t'haurà canviat el propietari dels fitxers on guarda aquestes dades.

L'hauries de buscar a /home/XXXXX/.mozilla/firefox/XXXXX.default.
Hi ha un fitxer que es dirà bookmarks.html (o així) i que segurament hauràs de canviar de propietari perquè siguis tu 
Comprova primer si això que et dic és cert fent

> ls -l bookmarks.html 

Si el resultat és que el propietari és root aleshores

> sudo chown NomUsuari bookmarks.html

Si no, doncs serà una altra cosa.

lluís

---

### Post by Rubunter on 2008-06-07
Ei Lluís, gràcies per la resposta. Ahir després de trencar m hi el cap vaig actualitzar el firefox i ara tinc la RC2. Ara sí que veig els bookmarks, però el problema ara és que el programa te alzheimer!  Cada vegada que el tanco i torno a obrir, s'oblida de la pàgina d'inici que li havia indicat. 
Quan entro com a root sí que em guarda les preferències i tot funciona normal.
He buscat al google i hi ha gent amb el mateix problema amb versions anteriors de firefox, però no he trobat cap solució.

---

### Post by Rubunter on 2008-06-07
Tot solucionat. No sé quin era exactament el problema, però suposo que seria que el meu profile estava corrupte. Ho he solucionat creant-ne un de nou i important tots els bookmarks, historia de navegació, passwords etc.
Des del terminal:

```
firefox -ProfileManager
```

i des d'aquí he creat el nou i he eliminat el vell. Gràcies

---


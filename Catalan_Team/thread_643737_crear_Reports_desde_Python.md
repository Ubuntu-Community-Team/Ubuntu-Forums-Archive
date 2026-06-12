---
title: "crear Reports desde Python"
date: 2007-12-18
forum: Catalan Team
---

### Post by carlesbm on 2007-12-18
Hola gent:

    Us explico; he estat experimentant en la programació desde Linux per mitja del llenguatge Python i ara hem trobo en la necesitat què he de generar un seguit de informes (Reports) per tal de imprimir un seguit de dades, provinents de una base de dades, com pot ser PostgreSQL, he estat mitant diferents aplicacions per tal de generar aquests informes i no consegueixo de ver-ho massa clar. Hi aha que hem generen un arxiu PDF que en principi pot estar be si savem quina es la forma de imprimir despres aquest arxiu directament desde el programa, sense haver que obrir una altra aplicació.

   Si algú te alguna idea ho agraria molt doncs estic encallat en aquest punt.


  Moltes gracies ha tots.

:confused::confused:

---

### Post by papapep on 2007-12-18
Crec que el mateix openoffice et permetrà accedir i crear informes a partir de postgres. L'ordinador client que farà les consultes al servidor també serà Linux o serà algun "altre" sistema operatiu?
Tu el que vols és fer consultes i que resultin estèticament agradables, no? Per que suposo que ja has provat el pgadmin.

---

### Post by carlesbm on 2007-12-18
Hola 

    M'explicare millor que no ho he fet anteriorment:
    
    La meva idea es crear una aplicació per tal de gestionar una base de dades on tinc totes les comandes de l'empresa, i per mitja de aquesta comada puguer imprimir els fulls de entrega de material, llistats de material.... . Actualment tinc una aplicació molt basica creada amb Access, però ultimament hem dona problemes,quan vull implementar noves funcions, a l'aplicació.

   Ha l'empresa utilitzem Guidows, i al veure que amb Python es poden crear aplicacions multiplataforma, havia pensat, de refer tota l'aplicaió, però aquest cop desde Python.

   Referent al teu comentari de utilitzar OpenOffice si que es pot fer, però veig un petit inconvenient, que de segur que no ho es, si se sap com solucionar-ho. Per tal de poder accedir a un document de Ooo cal haver arrencat la suite  amb una serie de ordres en mode client, i desde el programa no ser pas com fer-ho.

---

### Post by papapep on 2007-12-18
Ara ens entenem ;-)

Crec que aquí hi ha un parell de coses que igual t'ajuden:

[http://swik.net/PostgreSQL?popular](http://swik.net/PostgreSQL?popular)

---

### Post by marcoil on 2007-12-19
> **carlesbm said:**
> Hola gent:
Hi aha que hem generen un arxiu PDF que en principi pot estar be si savem quina es la forma de imprimir despres aquest arxiu directament desde el programa, sense haver que obrir una altra aplicació.

   Si algú te alguna idea ho agraria molt doncs estic encallat en aquest punt.


Depèn un poc de quin framework o llibreria vulguis emprar per fer l'aplicació. Per exemple, GTK+ permet imprimir directament des de l'aplicació amb [GtkPrinting]("http://library.gnome.org/devel/gtk/unstable/Printing.html").

Sinó, la manera bèstia és enviar directament l'arxiu a un programa d'impressió, com el lpr o el gtk-lp.

Hi ha un parell (de pagès) de projectes per substituir l'Access, com el [Glom]("http://www.glom.org/wiki/index.php?title=Main_Page") o el [Davo]("http://dabodev.com/").

---


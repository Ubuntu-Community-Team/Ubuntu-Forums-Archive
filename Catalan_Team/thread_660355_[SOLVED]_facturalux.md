---
title: "[SOLVED] facturalux"
date: 2008-01-06
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-01-06
bones.
Estic cercant un programa per fer factures amb Ubuntu.
He instatal·lat "faturalux" i només engegar ja hem diu que "Cargando driver de la base de datos... Ok
Comprobando conexión a la base de datos... 
Error: Pulse en Atrás y compruebe su configuración". Sembla que no supera la conexió base de dades, i no tinc ni idea.
Algú coneix aquest programa?
O be, algú sap d'algun altre programa per facturar?
Gracies x endavant.

---

### Post by CarlesOriol on 2008-01-07
Insta&#320;la abaq de la web del fabricant [http://www.infosial.com/](http://www.infosial.com/) . És la versió actualitzada.

---

### Post by papapep on 2008-01-07
En tot cas, tan si fas servir la antiga Facturalux o el nou Abanq, tingues present que, com ja t'adelanta l'error que has vist, has de tenir un gestor de base de dades al darrera del programa per a gestionar-ne les dades.
En tot cas, fes un cop d'ull a la documentació que tenen al seu lloc web abans de fer res:

[http://abanq.org/documentacion/](http://abanq.org/documentacion/)

T'ajudarà a tenir una millor perspectiva sobre si és el que vols o no.

---

### Post by Miquel Ubuntero on 2008-01-12
Hola de nou.
Ja he instal·lat facturalux i, després de mirar-me el link recomenat per papapep, també m'he instal·lat una base de dades PostgreSQL. Ara be, sembla que configurar aquesta base de dades no és gens fàcil.
Serà que m'agraden les coses més fàcils :)
Algú coneix algun programa que no requereixi instal·lar a més aixó de les bases de dades?

---

### Post by CarlesOriol on 2008-01-13
Vinga que està "xupat".

Instalar el postgres en 2 passos:

**1.** Insta&#320;lar la base de dades i una utilitat de manteniment gràfica

```
sudo apt-get install postgresql pgadmin3
```

**2.** Crear un usuari administrador

```
sudo -u postgres createuser carles -P
```

i ja pots usar el pgadmin per jugar a bases de dades.

---

### Post by Miquel Ubuntero on 2008-01-13
SOLVED
tenies raó Carles, està xupao. Be, xupao amb les teves bones i senzilles explicacions; perquè quan vaig llegir el "readme.doc" en anglès de 4 fulls hem vaig cagar :)
En fi, ja xuta, moltes gracies ;)

---


---
title: "[SOLVED] Augmentar rendiment Amarok"
date: 2008-10-13
forum: Catalan Team
---

### Post by LitusMayol on 2008-10-13
Ep gent!

Voldria augmentar el rendiment de l'**Amarok**. Tot i córrer amb *GNOME*, degut als meus passats *KDE*istes adoro i venero el reproductor de música del llop [COLOR="Silver"](que per cert, us heu fixat que és pràcticament el mateix llop que una coneguda [marca de vodka]("http://www.subzone.at/Eristoff%20Master%20CMYK.jpg")?)[/COLOR]

Doncs això. M'encanta l'**Amarok**(i espero la 2a part, que ja va per la 2a Beta!) però té un inconvenient... Em va LENT. La navegació a través de les pestanyes laterals és lenteta (pot tardar 10 segons en carregar un canvi de pestanya) però el pitjor és la *Col·lecció*. Efectuar-hi cerques és mortal. Arriba a penjar-se (allò de que es torna a escala de grisos i deixa de funcionar). És una mala passada, perquè quan vull buscar un artista o una cançó en concret, pot tardar minuts en recuperar el seu aspecte i el seu funcionament (si és que ho arriba a fer). 

Primer de tot vaig provar a *taguejar* les cançons de la millor manera possible per assegurar un ordre (que no hi hagués "*LAX'N'BUSTO*", "*Lax n Busto*" i "*Lax'n'Busto*", per exemple). Però res. Ara he desconectat l'OSD. Però clar: només l'utilitza quan canvia de cançó per tan... bastant estúpid.

Suposo que el fet de tenir prop de 10.000 cançons ajuda a tenir problemes. Però això no hauria de ser un entrebanc en un reproductor de música, no? 

Algú sap com augmentar el seu rendiment, o com fer que la lectura a través de la *Col·lecció* sigui més ràpida?

Merci!

---

### Post by orestesmas on 2008-10-14
Home, a mi l'Amarok sempre m'ha anat bé però, és clar, jo no tinc 10.000 cançons a la col·lecció...

Això té pinta d'haver-te topat amb problemes de rendiment del sistema de base de dades subjacent, que és el SQLite. Simplement no deu estar pensat per aquestes tasques, i és un dels motius pels quals els desenvolupadors d'Amarok han decidit passar-se a MySQL, en una decisió que ha aixecat polèmica, però que ells justifiquen en l'enllaç que et poso més avall. Aquí tens un fraqgment on comenten els enormes guanys de rendiment que s'obtenen en passar de SQLite a MySQL:

> Now we had to choose the type. At first, SQLite seemed like a good choice. Using transactions, it's decently fast. It's pretty stable (those that complain about odd MySQL bugs should talk to markey, as he, being the SQLite maintainer in 1.4, can attest that SQLite's had its fair share). However, there were a few problems that in the end knocked it out of the running. The first problem is performance. Although for people with small collections it performs fairly well, people with large collections that switched to the MySQL or PostgreSQL backends in A1 would report enormous speed gains when operations performing complex or many queries were performed, such as adding many entries to the playlist, scanning files, or filtering/searching in the collection. Since we want to accommodate users with large collections just as well as those with smaller collections, and since digital music collections aren't getting smaller, the speed increase for our users with large collections was quite important.

De tota manera, no cal esperar-se a l'Amarok 2, perquè que pots usar MySQL (o Postgres) com a dorsal de dades ja en l'Amarok 1. Només cal que busquis per la xarxa "amarok mysql backend" i trobaràs una pila de referències. Per exemple, a [http://gentoo-wiki.com/Amarok](http://gentoo-wiki.com/Amarok) en tens una que explica com fer-ho per una Gentoo, però per Ubuntu és molt semblant.

Si fas el canvi probablement hauràs de reescanejar la col·lecció, però no crec que això suposi un problema especial. Però fes una còpia de les dades del SQLite per si de cas.

Per si vols saber-ne més, pots trobar l'article complet que explica la decisió del canvi a MySQL a:
[http://amarok.kde.org/blog/archives/812-MySQL-in-Amarok-2-The-Reality.html](http://amarok.kde.org/blog/archives/812-MySQL-in-Amarok-2-The-Reality.html)

---

### Post by LitusMayol on 2008-10-14
**orestesmas** ets un crack! 
Si senyor! Avui per tu, el més *KDEista* del fòrum!

He llegit l'article que m'has passat, genial. És l'explicació perfecta. Un dels motius és el meu: una col·lecció extensa. (de fet en algun moment diu que les biblioteques petites no notarien la diferència entre SQLite i MySQLite, mentre que les grans la notarien)

Doncs ara m'hi poso a veure si ho aconsegueixo (i de pas ja posaré el *[SOLVED]*, de moment no)


Merci!

---

### Post by LitusMayol on 2008-10-14
Ieeep!

A veure, *googlejant* he acabat anant a parar a [aquí]("http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html"). He seguit les passes però això és el que em diu l'**Amarok**:
> MySQL ha informat del següent error:
Access denied for user 'amarok'@'localhost' (using password: YES)
Podeu configurar MySQL a la secció Col·lecció al menú Arranjaments-> Configura l'Amarok


Algú sap què vol dir i com solucionar-ho? (suposo que aquest error és l'arrel de que ara no llegeixi la col·lecció fins hi tot després de redefinir-la i prémer diverses vegades "*Reescaneja la col·lecció*")


Merci!

---

### Post by _DarkEagle_ on 2008-10-14
> **LitusMayol said:**
> 

Algú sap què vol dir i com solucionar-ho? (suposo que aquest error és l'arrel de que ara no llegeixi la col·lecció fins hi tot després de redefinir-la i prémer diverses vegades "*Reescaneja la col·lecció*")


Merci!

L'únic que et diu aquest error és que no pot entrar com a usuari amarok a la base de dades de mysql, pot ser que no l'hagis creat ? si no et sents a gust amb el mysql en línia de comandes, pots instal·lar-te phpmyadmin (és un frontend web per a administrar usuaris/bases de dades de mysql).


Com sempre, apt-get install phpmyadmin (tens que tenir instalat tant php, com apache) després hi accedeixes mitjançant [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Ja veuràs que és bastant intuïtiu de fer anar, però per algun problema ja saps .. :)

Salut !

---

### Post by LitusMayol on 2008-10-14
Ep!

Això del *phpmyadmin*... :S He clickat al web que m'has donat (però he canviat *localhost* pel número de localhost que he de posar) i em diu això:
> Not Found

The requested URL /phpmyadmin was not found on this server.
Apache/2.2.8 (Ubuntu) Server at 127.0.0.1 Port 80

El tema és que teòricament m'he d'*enxufar*al port 3306, té alguna cosa a veure amb aquest "Port 80"? Si és això com ho canvio?

Si no és això... vaig perdudíssim i no &#347;e què fer!:lolflag:

Merci

---

### Post by _DarkEagle_ on 2008-10-14
> **LitusMayol said:**
> Ep!

Això del *phpmyadmin*... :S He clickat al web que m'has donat (però he canviat *localhost* pel número de localhost que he de posar) i em diu això:


El tema és que teòricament m'he d'*enxufar*al port 3306, té alguna cosa a veure amb aquest "Port 80"? Si és això com ho canvio?

Si no és això... vaig perdudíssim i no &#347;e què fer!:lolflag:

Merci

A veure .. el phpmyadmin és una web que tu "instal·les" en el teu ordenador (gràcies a tenir instal·lat un servidor web, en aquest cas apache). Un servidor web, escolta les peticions dels clients (la persona que vol mirar la web) pel port 80, en canvi .. el servidor de bases de dades mysql escolta pel port 3306.

Es dir, tu per a connectar-te al servidor de mysql faràs anar un client, aquest client, pot ser per linia de comandes, o també pot ser a traves d'un frontend web. El frontend (phpmyadmin) ja s'encarregarà de comunicar-se amb el servidor mysql per el port 3306, tu l'únic que has de fer es visitar la web que et farà d'intermediari, es a dir: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Aquest localhost, el pots canviar si el servidor web no esta instal·lat en la teva maquina, es dir .. si es una altra màquina de la teva xarxa podries posar per exemple: [http://192.168.0.X/phpmyadmin](http://192.168.0.X/phpmyadmin)

Aquí sembla com si no tinguessis instalat el phpmyadmin, has fet el apt-get install phpmyadmin ??

---

### Post by LitusMayol on 2008-10-14
OK.

Estava mal instal·lat (al *Synaptic* apareixia com a instal·lat, he fet un *purge* i l'he tornat a instal·lar). Ara ja puc accedir-hi. Però no sé ben bé què he de fer.

Diria que he de crear una nova base de dades... però diu que no tinc permisos (veure adjunt)


Què faig? :(

---

### Post by papapep on 2008-10-14
Mysql, com tots els gestors de bases de dades, tenen diferents usuaris que tenen certs drets sobre les altres taules i altres objectes de la base de dades. En Mysql "root" (però un root propi, no el del sistema), és el rei de la festa. Pot fer i desfer a voluntat. Per a recuperar la contrassenya de l'usuari root (si és que no la saps) i poder crear noves bases de dades pots buscar un qualsevol dels documents que en parla a inet (n'hi ha a milers). Un d'ells: [http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

Amarok, si ho fan de manera correcta, hauria de fer servir per a gestionar la base de dades de cançons un usuari que no fos "root", per evitar maldecaps. Probablement, no els he mirat, als enllaços que ja t'han passat es parla del tema.

---

### Post by _DarkEagle_ on 2008-10-14
El tema de permisos és normal, per que has entrat al phpmyadmin com a usuari "amarok" i no com a usuari "root" que és el que per defecte te tots els permisos. De totes maneres amb això es veu que l'usuari amarok el tens ven creat ... però i la base de dades amarok ? està creada ?

Des d'aquí és més fàcil explicar-t'ho a traves de Terminal, així és que, obre un terminal i escriu:

```
# mysql -p -u amarok
```

Això servirà per a accedir al servidor mysql com a usuari amarok.

Un cop a dins escriurem la comanda que ens llistarà les bases de dades que hi tenim definides:

```
show databases;
```

**És important el punt i coma final !**

Aquesta ultima comanda t'hauria de llistar les bases de dades que tens creades, n'hi hauria d'haver una anomenada amarok.

Si no hi és, l'haurem de crear ... a través de phpmyadmin (per exemple), entrant com a usuari root.

Salut !

---

### Post by LitusMayol on 2008-10-15
Ep!

**_DarkEagle_**, primer de tot merci. Després dir-te que tinc problemes:
```
litus@mayolets-desktop:~$ mysql -p -u amarok
Enter password: 
ERROR 1045 (28000): Access denied for user 'amarok'@'localhost' (using password: YES)
litus@mayolets-desktop:~$ 
```

Ara no em deixa entrar ni via web! :S


També he provat el *link* que en **papapep** dóa, però al primer pas ja tinc entrebancs...

```
litus@mayolets-desktop:~$  /etc/init.d/mysql stop
open: Permission denied
 * Stopping MySQL database server mysqld                                        cat: /var/run/mysqld/mysqld.pid: Permission denied
open: Permission denied
                                                                         [fail]
litus@mayolets-desktop:~$ 

```


:S AJUDAA! heheh

Merci! ;)

---

### Post by _DarkEagle_ on 2008-10-15
Per parar/engegar un servidor necessites fer-ho com a root.

Es a dir, has de fer:

```
sudo /etc/init.d/mysql stop
```

Salut !

---

### Post by LitusMayol on 2008-10-15
Perfecte.

Després d'afegir el *sudo* he seguit [el manual d'en **papapep**]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html"). 


Un cop fet això he fet el que em deies tu, **_DarkEagle_**:

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| amarok             | 
| mysql              | 
+--------------------+
3 rows in set (0.01 sec)

mysql> 
```



Fet. I ara què faig?


(Merci, merci!)

---

### Post by _DarkEagle_ on 2008-10-15
Si has pogut entrar com a usuari amarok dintre de mysql i la taula amarok esta creada ... teòricament ja t'hauria de funcionar tot.

Encara tens problemes amb el amarok ? si tens encara problemes .. potser que miréssim de fer això mes interactiu i ens podem trobar en un xat o pel msn ... un cop solucionat el problema podem fer un post amb la solució aquí, al fòrum.

Salut !

---

### Post by LitusMayol on 2008-10-15
Ieeep!

Doncs a l'**Amarok** no hi noto cap canvi. Segueix sense escanejar la col·lecció. 

(@**_DarkEagle_**: em conecto a l'IRC, si apareixes per allí digue'm alguna cosa )

---

### Post by LitusMayol on 2008-10-15
Bones!
Gràcies a en **_DarkEagle_** la cosa ja rutlla. (Merci, merci, mercii!!!)

Via IRC ho hem (vaja.. ho HA) solucionat. Simplement hem esborrat l'usuari de MySQL i la base de dades de l'**Amarok** i hem començat de 0. Pas a pas...

En fi!

Merci!



**EDITO:**
Links relacionats que m'han ajudat a resoldre el post:

[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)
[http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php)
[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

---


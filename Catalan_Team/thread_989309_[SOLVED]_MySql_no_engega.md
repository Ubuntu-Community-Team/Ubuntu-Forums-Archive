---
title: "[SOLVED] MySql no engega?"
date: 2008-11-21
forum: Catalan Team
---

### Post by xoldy on 2008-11-21
Hola a tots, bona tarda, vaig una mica perdut. tinc posat el mysql per "jugar" amb el joomla, i ara al iniciar el firefox amb el localhost, em dona el següent missatge:

Database Error: Unable to connect to the database:Could not connect to MySQL

per poder saber quin error dona, al terminal intento entrar a mysql i em dona això:

```
xoldy@xoldy-ubuntu:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

algun suggeriment? No domino massa el tema del mysql.

Moltes gràcies

---

### Post by papapep on 2008-11-21
Mysql NO és un programa normal que executis sense més, és un servei, un servidor.

Aquestes coses normalment s'arrenquen amb una ordre de l'estil:

```
sudo /etc/init.d/mysql start
```

ja que a /etc/init.d/ és on solen ser els scripts d'arrencada i aturada dels dimonis.
T'aconsello buscar, i llegir, algun text d'iniciació a mysql a internet, que n'hi ha a patades, abans de ficar-t'hi, sinó et tornaràs boig.
Tampoc estaria malament mirar el tema del paradigma client-servidor i què són i per a què serveixen els dimonis (daemons).

---

### Post by xoldy on 2008-11-21
Em penso que ja he trobat el perquè no engega el servei, em falta espai a la partició perquè em dóna aquest error:
```
xoldy@xoldy-ubuntu:~$ sudo /etc/init.d/mysql start
 * /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!
xoldy@xoldy-ubuntu:~$ 

```

Miraré de fer un particionat més racional, perquè em penso que no funciona.

Moltes gràcies papapep, la comanda m'ha anat molt bé perquè tot i que estic llegint el document que tens penjat per entendre el terminal, falta costum de treballar-hi.

Torno a reinstal·lar tot, però deixant dues particions només la / i la /home, perquè vaig fragmentar massa el disc del portàtil i ara no puc ni instal·lar el gparted per esmenar les particions (tot i que no se si ho hauria permés). tanco el post.

---


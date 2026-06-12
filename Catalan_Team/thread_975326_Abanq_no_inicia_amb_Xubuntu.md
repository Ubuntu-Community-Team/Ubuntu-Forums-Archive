---
title: "Abanq no inicia amb Xubuntu"
date: 2008-11-08
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-11-08
Bones.
He instal·lat Abanq al Xubuntu 8.04 amb Xfce 4.
No puc iniciar abanq. Pot ser es normal? Es un problema no tindre gnome o kde?
El mateix procediment d'instal·lació hem va be amb Ubuntu 8.04 amb Gnome. 
Gracies qui pugui orientar-me.
Salut!

---

### Post by papapep on 2008-11-08
Miquel, no dones cap pista sobre què et pot passar, ni què intentes, ni quins possibles missatges has vist, si has executat a un terminal què mostra...etc. No podem veure el teu monitor de tan lluny... :-)

---

### Post by Miquel Ubuntero on 2008-11-08
Perdò, tens rao, poques pistes.
Be, la ideal del terminal es bona, ho he fet i he vist que demanaba unes llibreries. Les he instal·lat i ara ja s'inicia.
Però, el següent error: "No es pot connectar a la base de dades, data base "miquel" does not exist".
Gracies.

---

### Post by CarlesOriol on 2008-11-08
Has insta&#320;lat el postgres??? i en aquest la base de dades de nom "miquel"???

Has comprovat que el port del postgres sigui el 5432???

---

### Post by Miquel Ubuntero on 2008-11-11
Hola Carles.
Sí he instal·lat postgres i també he creat un usuari "miquel". El port 5432.
Referent a la base de dades, en intentar conexió hem demana crar-la, li dic que sí i me la crea, però despres diu no poder conectar-se.
Moltes gracies pel teu interés. Puc fer res més?

---

### Post by papapep on 2008-11-11
Jo m'asseguraria de que l'usuari té els permisos suficients per a tot el que ha de fer.
Ja has verificat que el postgres tingui el servei funcionant? amb un

```
netstat -nl |grep 5432
```

veuràs si el tens funcionant al port que cal.

Amb el [pgadmin]("http://packages.ubuntu.com/intrepid/pgadmin3") podràs veure els usuaris i els seus permisos, i modificar el que calgui, sense haver de barallar-te gaire amb el terminal. No he entès si el servidor i el client són la mateixa màquina o són dues diferents.

En tot cas, el sistema d'autenticació del postgres es defineix a /etc/postgresql/**NÚM_DE_VERSIÓ**/main/pg_hba.conf. Evidentment, has de substituïr **NÚM_DE_VERSIÓ** per la versió que tinguis instal·lada...

I, el més important: ens has de donar els missatges exactes que et mostra l'ordinador. Si no ho fem així podem estar perdent informació important per a resoldre el cas.

---

### Post by papapep on 2008-11-11
També és possible que a /var/log/messages tinguis algun missatge important:

```
sudo tail -n 30 /var/log/messages|grep posgtgres
```

et mostrarà les línies dins les últimes 30 del fitxer, i filtrarà les  que continguin la cadena de text "postgres", a veure què hi ha.

---

### Post by Miquel Ubuntero on 2008-11-12
Hola Papapep.
Aquí tens l'informació que hem demanes:

miquel@miquel-laptop:~$ netstat -nl |grep 5432
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     13426    /var/run/postgresql/.s.PGSQL.5432
miquel@miquel-laptop:~$ sudo tail -n 30 /var/log/messages|grep posgtgres
[sudo] password for miquel: 
miquel@miquel-laptop:~$  sudo tail -n 30 /var/log/messages|grep posgtgres
miquel@miquel-laptop:~$ 

Tal com veus, crec que la segona instrucció no diu res?

Referent al arxiu pg_hba.conf

aquí tens el contingut, que no entenc:


# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local   all         all                               ident sameuser
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
# IPv6 local connections:
host    all         all         ::1/128               md5

Salutacions cordials, Miquel.

---


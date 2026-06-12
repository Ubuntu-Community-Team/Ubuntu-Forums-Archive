---
title: "abanq copia seguretat"
date: 2008-04-05
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-04-05
Bones.
He provat amb abanq copia seguretat.
Per iniciar abanq, la base de dades es diu "miquel" i usuari "miquel", fàcil!
Però no hem surt lo del back-up.
Us enganxo el que hem diu el Terminal:

miqueladroer@miquel-desktop:~$ pg_dump miquel -U miquel > backup.sqlp
g_dump: [archiver (db)] connection to database "miquel" failed: FATAL:  Ident authentication failed for user "miquel"
miqueladroer@miquel-desktop:~$ 

Cap idea?
Gracies.

---

### Post by papapep on 2008-04-05
Fes servir l'usuari administrador de Postgresql, de nom "postgres".

---

### Post by CarlesOriol on 2008-04-05
#! /bin/sh

export PGPASSWORD=latevapassword

pg_dump -i -h server -p 5432 -U miquel -F c -b -v -f "/home/miquel/bitacoles.backup" labasededades

---

### Post by papapep on 2008-04-05
Uh! Fa falta tanta galindaina per fer un pg_dump per l'abanq??? Un simple pg_dump amb l'usuari correcte no funcionaria??

---

### Post by CarlesOriol on 2008-04-05
Si ho vols posar en un cron (per programar les copies). Jo ho faig així. 

La resta de paràmetres... no recordo per que son :-) (un com de man i es pot veure) els vaig preparar fa temps i es com jo volco les meves bases de postgres.

---

### Post by papapep on 2008-04-05
Per cert, fas servir sh en vers de bash com a intérpret d'ordres a l'script per alguna cosa en concret, o per simple hàbit?

---

### Post by CarlesOriol on 2008-04-06
pufff....

Fa temps ho tenia tot en bash fins que amb la edgy els xicots de canònical van canviar el bash pel dash (l'sh sols és un enllaç a un dels dos) ja que requereix una dècima part de recursos. I això em va trinxar tots els ifs amb arrays i un munt de coses.
(Recordes quan els paquets debs que no eren d'ubuntu petaven tots)


Recordo haver llegit que recomanaven aquest #!... així que com a bon xai del ramat ho vaig seguir.

Resumint: que els scripts que van aguantar el canvi els vaig passar a sh i els altres vaig forçar-los amb bash.

Si creus que hi ha altres possibilitats obrim un altre fil, si no emmerdarem aquest de la copia de seguretat.

---

### Post by Miquel Ubuntero on 2008-04-07
Gracies a tots dos.
Avuit tinc lio. Demà ho provo i ja us explicaré.
Salut!

---


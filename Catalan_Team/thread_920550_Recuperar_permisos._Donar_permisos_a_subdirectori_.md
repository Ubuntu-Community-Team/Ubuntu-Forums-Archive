---
title: "Recuperar permisos. Donar permisos a subdirectori amb accents"
date: 2008-09-15
forum: Catalan Team
---

### Post by srsiempre on 2008-09-15
Hola.

Vull copia unes carpetes del cd rom al disc dur, i diu que no tinc permisos.
Això em passa des de que vaig fer una actualització del ubuntu.

Els meus passos han fracassat:

A la terminal
[INDENT]1) sudo su
2) cd /media/sdc4
3) chmod 776 Mi música
[/INDENT]
Resposta:
[FONT=Courier New]chmod: no s’ha pogut accedir a «Mi»: No such file or directory
chmod: no s’ha pogut accedir a «música»: No such file or directory[/FONT]

[INDENT]Abans, tot haver instal·lat el ubuntu per primera vegada, podia arrossegar des de el cd rom al disc dur sense problemes,** que suggeriu que faci per canviar això?**
[/INDENT]
Veure imatge:
 [http://img254.imageshack.us/my.php?image=lsmimusicavz7.png](http://img254.imageshack.us/my.php?image=lsmimusicavz7.png)


Gràcies

---

### Post by papapep on 2008-09-15
Els espais als noms de directoris no són bons amics de l'usuari. És una altra mala herència dels sistemes fat i similars. 
Quan fas:

```
chmod 776 Mi música
```

no t'està dient que tingui problemes amb l'accent, té problemes en que no entèn que Mi i música formen part del mateix nom. 

Prova a fer:

```
chmod 776 Mi\ música
```

aquí li estàs dient que entre una paraula i una altra HI HA un espai (només cal fer-ne un, si en deixes dos també fallarà).

Respecte el perquè ara no et va el que abans t'anava, doncs això ja és un tema bastant més pelut...

---

### Post by kukat on 2008-09-15
a mi em pasava això!
tens que posar les cometes, les de la tecla de l'interrogant "?"

chmod 776 'Mi música'

així em funciona a mi!!! si hi ha un espai tens que posar les cometes per a que forme part d'un tot!! si no es pensa que es "Mi", i "música", per separat...o aixó sembla:)

Salut!

---

### Post by srsiempre on 2008-09-15
Si amb les[SIZE=7] '[/SIZE] ho he pogut canviar.

:guitar:

---

### Post by lpargemi on 2008-09-15
Hola

A part de les cometes un altre truc, que vaig trobar en un post de l'oriolbsd al post d'aqui baix, és escriure 

chmod 776 Mi[Tab] 

i quan apretes el tabulador el programa t'escriu el que falta del nom del fitxer.

[http://ubuntuforums.org/showthread.php?t=856150]("http://ubuntuforums.org/showthread.php?t=856150")

Salut

Lluís

---


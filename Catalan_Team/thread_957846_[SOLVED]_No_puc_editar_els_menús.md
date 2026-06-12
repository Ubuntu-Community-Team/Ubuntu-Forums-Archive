---
title: "[SOLVED] No puc editar els menús"
date: 2008-10-24
forum: Catalan Team
---

### Post by sakuraya on 2008-10-24
Bona nit a tothom.

Tinc un petit problema amb els menús i no els puc editar. Quan clico a sobre de qualsevol d'ells a la barra superior, amb el botó secundari del ratolí, em surt la opció de "Edita els menús", però es queda com si res. Algú sap perquè?

Moltes gràcies.

---

### Post by papapep on 2008-10-24
No, però has provat a Sistema > Preferències > Menú principal?

---

### Post by LitusMayol on 2008-10-25
Prova el que et diu en **papapep** (que sempre té la raó hehehehe) i sinó prova d'escriure al terminal:
```
alacarte
```

sort! ;)

---

### Post by sakuraya on 2008-10-25
Hola de nou, i moltes gràcies.

He provat el què diu en Papapep, però passa exactament el mateix, és a dir, absolutament res. 
També he provat el que diu en LitusMayol, i em surt el següent, que no sé què vol dir:

mari@mari:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ca_AD
mari@mari:~$ 

Suposo que ja n'he fet alguna...

---

### Post by LitusMayol on 2008-10-25
> **sakuraya said:**
> 
mari@mari:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ca_AD
mari@mari:~$ 



Mmm... Ostres. Jo no en sé massa... però diria que l'últim error que dóna és que no entén l'idioma local (català d'andorra), pot ser?

Tan se val, pots provar de eliminar-lo completament i reinstal·lar-lo:
```
sudo apt-get purge alacarte
sudo apt-get install alacarte
```


[COLOR="SlateGray"]
(No n'estic segur però em sembla que és el mateix que fer: )
```
sudo apt-get purge alacarte && sudo apt-get install alacarte
```

[/COLOR]

A veure si hi ha sort! ;)

---

### Post by CarlesOriol on 2008-10-25
Crec que no has finalitzat la insta&#320;lació de l'idioma catala andorrà (ca_AD).

Ves a Sistema > Administració > Suport d'idioma i marca totes les opcions de català.
(si segueix igual prova la canfiguració del català en d'altres estats com frança, italia, i algun altre que no recordo)

---

### Post by sakuraya on 2008-10-27
OK OK OK, perfecte, ja funciona. La solució en aquest cas, després de provar totes les opcions, ha estat Sistema > Administració > Suport d'idioma, tot instal·lant totes les opcions del català, tal i com explica en Carles Oriol.
Moltíssimes gràcies.

---


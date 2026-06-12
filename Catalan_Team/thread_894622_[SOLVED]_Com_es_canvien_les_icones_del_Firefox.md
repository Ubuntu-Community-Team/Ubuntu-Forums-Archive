---
title: "[SOLVED] Com es canvien les icones del Firefox"
date: 2008-08-19
forum: Catalan Team
---

### Post by LitusMayol on 2008-08-19
Hola que tal!?

Aquí el *pelma preguntón*!

Mireu he trobat unes icones fantàstiques (al menys des del meu punt de vista) per al **Firefox**. Les hi he trobat com a avatar a un tal **Happy_Man** i ell m'ha donat [aquesta adreça]("http://www.gnome-look.org/content/show.php/Firefox+Icons?content=47617") del **Gnome-Look**. 

Voldria canviar les icones del meu **Firefox** per aquestes. Però no me'n surto... Si vaig a "*Edita > Preferències*" no hi trobo res que em permeti canviar la icona.


Si que he pogut canviar la icona del llançador que tinc a la barra superior. Però no l'altra.


Algú em pot ajudar?



Merci!

---

### Post by oriolsbd on 2008-08-19
Hola, Carles.

A quina et refereixes amb "l'altra"? La del menú "Aplicacions", la de la barra superior de Gnome, o alguna que es mostra a la mateixa finestra del Firefox?

Salut!

---

### Post by patrickfromspain on 2008-08-19
per canviar l'altra icona, hauries de canviar totes les icones del firefox del tema que facis servir, per aquesta. Que es una mica follon, no?

Una altra manera, es crear-te tu mateix un tema d'icones, que només contingui aquesta icona i que agafi les icones que faltin del teu tema actual. Aquesta darrera opció, a poco que sapiguis com funcionen els temes de gnome, es bastant senzilla. 

salut!

---

### Post by LitusMayol on 2008-08-20
Bones!

> A quina et refereixes amb "l'altra"? La del menú "Aplicacions", la de la barra superior de Gnome, o alguna que es mostra a la mateixa finestra del Firefox?
Doncs a les dues: la del menú "*Aplicacions > Internet*" i la que m'apareix al centre de la finestra abans del nom de la plana web.

> per canviar l'altra icona, hauries de canviar totes les icones del firefox del tema que facis servir, per aquesta. Que es una mica *follón*, no?

Si la veritat que si que és un bon cacao.

> 
Una altra manera, es crear-te tu mateix un tema d'icones, que només contingui aquesta icona i que agafi les icones que faltin del teu tema actual. Aquesta darrera opció, a poco que sapiguis com funcionen els temes de gnome, es bastant senzilla.


Mmmm! Això no se m'havia ocorregut! Grandíssim **patrickfromspain**. Després ho probo i us dic què.

---

### Post by oriolsbd on 2008-08-20
Per canviar la d'"Aplicacions > Internet", ho pots fer des del menú "Sistema > Preferències > Menú Principal". Vas al menú "Internet" (en el panell a mà esquerra), i et sortiran a mà dreta les aplicacions que hi ha. Si fas clic amb el botó dret del ratolí sobre el Firefox i esculls "Propietats", t'obrirà un panell. Fas clic sobre la icona, podràs escollir la que vulguis.

Quant a l'altra icona, crec que hauràs de fer el que diu en Patrickfromspain.

Salut!

---

### Post by LitusMayol on 2008-08-20
Fantàstic **oriolsbd**!

Perfecte, ja només em queda canviar el de la finestreta, que ho probaré més tard (sóc a la feina! :S hehe).

Merci als dos!

---

### Post by LitusMayol on 2008-08-20
Ep!

Tinc un problema... quan clicko a "*Sistema > Preferències > Menú principal*" no passa re! :S No aconsegueixo obrir el menú!

---

### Post by oriolsbd on 2008-08-20
Des d'un terminal, executa la comanda "alacarte", que és l'equivalent. A veure si et dóna algun missatge d'error. Ho podries haver vist des de "Sistema > Preferències > Menú Principal". Ai, no! Si no et funciona!  :-)

Salut!

---

### Post by lluisanunez on 2008-08-20
La icona per defecte del Firefox és la que hi ha a 
/usr/share/firefox/chrome/icons/default/

---

### Post by LitusMayol on 2008-08-20
Ep!

Això és el que em diu el terminal:
```
litus@mayolets-desktop:~$ alacarte
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
litus@mayolets-desktop:~$ 

```

**lluisanunez** aquí és fins on he arribat:
```
litus@mayolets-desktop:/usr/share$ cd /usr/share/firefox/
litus@mayolets-desktop:/usr/share/firefox$ ls
defaults
litus@mayolets-desktop:/usr/share/firefox$ cd /usr/share/firefox/defaults
litus@mayolets-desktop:/usr/share/firefox/defaults$ ls
pref
litus@mayolets-desktop:/usr/share/firefox/defaults$ cd /usr/share/firefox/defaults/pref
litus@mayolets-desktop:/usr/share/firefox/defaults/pref$ ls
apturl.js
litus@mayolets-desktop:/usr/share/firefox/defaults/pref$ 


```

No he trobat pas la carpeta on dius que haurien de ser les icones per tal de canviar-les... 


Sabeu què he de fer?

Merci als dos!

---

### Post by pespin on 2008-08-20
```
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ca_AD
```

Pel que diu aquí no et detecta la llengua. prova amb LANG=ca_ES i si tampoc funciona prova LANG=C:

```

$ LANG=ca_ES; alacarte
```

---

### Post by oriolsbd on 2008-08-20
Al locale li falta el ".utf8". Prova de fer:
```
$ LANG=ca_AD.utf8;alacarte
```

Pots veure tots els locale disponibles amb:
```
$ locale -a
```

Salut!

---

### Post by lluisanunez on 2008-08-20
Jo provaria de tornar a insta&#320;lar l'Alacarte.

Les icones de Firefox pot ser que les trobis a:
/usr/share/firefox/chrome/icons/default
i també aquí:
/usr/share/firefox/icons

Jo he canviat amb èxit les del Seamonkey i el IceApe que eren horroroses, ara el FF té una integració amb el tema de Gnome que no sé si te les deixarà canviar.

---

### Post by LitusMayol on 2008-08-21
Bones senyors!

He triat l'opció de l'**oriolsbd**, i la veritat a funcionat! (tot i que no ha arreglat el tema que pugui obrir el *Menú Principal* des de "*Sistema > Preferències*"; simplement al teclejar el 1r codi s'ha obert i en català).Per tan ja he pogut canviar la icona de "*Aplicacions > Internet*". 


Pel que fa  a la icona de la finestra del **Firefox** no hi he pogut arribar.  (**lluisanunez** les carpetes que em descrius no les tinc jo! :S):
```
litus@mayolets-desktop:/usr/share$ cd /usr/share/firefox/
litus@mayolets-desktop:/usr/share/firefox$ ls
defaults
litus@mayolets-desktop:/usr/share/firefox$ cd /usr/share/firefox/defaults/
litus@mayolets-desktop:/usr/share/firefox/defaults$ ls
pref
litus@mayolets-desktop:/usr/share/firefox/defaults$ cd /usr/share/firefox/defaults/pref/
litus@mayolets-desktop:/usr/share/firefox/defaults/pref$ ls
apturl.js
litus@mayolets-desktop:/usr/share/firefox/defaults/pref$ 

```

---

### Post by oriolsbd on 2008-08-21
Què et respon si fas:
```
locale
```

Salut!

---

### Post by LitusMayol on 2008-08-22
*locale*? Això que fa. busca els idiomes...?

Aquí ho tens!
```
litus@mayolets-desktop:~$ locale
LANG=ca_AD
LC_CTYPE="ca_AD"
LC_NUMERIC="ca_AD"
LC_TIME="ca_AD"
LC_COLLATE="ca_AD"
LC_MONETARY="ca_AD"
LC_MESSAGES="ca_AD"
LC_PAPER="ca_AD"
LC_NAME="ca_AD"
LC_ADDRESS="ca_AD"
LC_TELEPHONE="ca_AD"
LC_MEASUREMENT="ca_AD"
LC_IDENTIFICATION="ca_AD"
LC_ALL=
litus@mayolets-desktop:~$ 


```

---

### Post by oriolsbd on 2008-08-23
Et diu la "internacionalització" que tens assignada. Són diferents variables que utilitza el sistema per a saber com t'ha de mostrar les dades. Per exemple, la variable "LANG" defineix que l'idioma en que es mostren els menús, missatges, etc. és el català. La variable "LC_TIME" defineix que la data i hora s'ha de mostrar en el "format català", el "LC_MONETARY" defineix que els tipus numèrics de moneda s'han de mostrar amb el "format català", etc. Realment, es podria tenir un sistema amb l'idioma català, però mostrant la data en format americà, i mostrant les monedes en el format d'anglaterra. No sé si té molt sentit, però es podria fer.

En principi, per canviar aquestes variables crec que hauria de ser a través del menú "Sistema > Administració > Suport d'Idioma", però ho he provat, i no em canvia el valor de les variables. A veure si algú més ho sap fer.

Si no, hi ha una manera de fer-ho, que és assignant directament aquest valor de variables quan s'arranca el sistema. Si edites el fitxer ~/.profile i hi afegeixes aquestes línies al final, en rearrancar el sistema amb el teu usuari hauria de ternir bé les variables i hauria de funcionar el menú:

```

LANG=ca_AD.utf8
LC_CTYPE="ca_AD.utf8"
LC_NUMERIC="ca_AD.utf8"
LC_TIME="ca_AD.utf8"
LC_COLLATE="ca_AD.utf8"
LC_MONETARY="ca_AD.utf8"
LC_MESSAGES="ca_AD.utf8"
LC_PAPER="ca_AD.utf8"
LC_NAME="ca_AD.utf8"
LC_ADDRESS="ca_AD.utf8"
LC_TELEPHONE="ca_AD.utf8"
LC_MEASUREMENT="ca_AD.utf8"
LC_IDENTIFICATION="ca_AD.utf8"
LC_ALL=

```

De tota manera, crec que és una manera una mica "lletja" de fer-ho. A veure si algú altre sap fer-ho d'una manera "neta".

Salut!

---

### Post by LitusMayol on 2008-08-24
Ha funcionat! ;)

Merci mestre!

---

### Post by lluisanunez on 2008-08-25
Si poses una icona a /usr/share/pixmaps, que tingui el mateix nom que el programa i extensió png, automàgicament el menú l'agafa per a aquest programa (pot ser que hagis de fer logout i login perquè tingui efecte)

---

### Post by SiscoGarcia on 2008-08-25
> **lluisanunez said:**
> Si poses una icona a /usr/share/pixmaps, que tingui el mateix nom que el programa i extensió png, auto[COLOR="Red"]màgic[/COLOR]ament el menú l'agafa per a aquest programa (pot ser que hagis de fer logout i login perquè tingui efecte)


Sí que sembla màgic ;)

---

### Post by LitusMayol on 2008-08-26
Gràcies pel consell *màgic*! 

Funciona! ;)
Merci a tots!



([SOLVED] com una casa!!!)

---


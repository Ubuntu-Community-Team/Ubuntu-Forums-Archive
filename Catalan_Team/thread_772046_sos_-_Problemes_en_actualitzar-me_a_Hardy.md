---
title: "sos - Problemes en actualitzar-me a Hardy"
date: 2008-04-28
forum: Catalan Team
---

### Post by SiscoGarcia on 2008-04-28
L'he cagada molt. M'explico: Anit vaig començar a actualitzar-me i, igual que diu el Joan Marc al fil "[Durant l'actualització]("http://ubuntuforums.org/showthread.php?t=770758")", arribat un punt (faltaven 4 minuts per acabar l'actualització) em demana què vull fer respecte el? (adjunto la seua captura). Total que arribat aquest punt vaig demanar que em mostrés la diferència entre les versions "side by side". Aquí va venir el problema perquè em vaig esperar com uns 3/4 d'hora i no va fer res.

Llavors vaig començar a patir i vaig tancar la màquina ("craso error"), amb la qual cosa m'ha petat l'ubuntu.

problema afegit: no em funciona la lectora de CD (dissabte ja em fallava).

En arrencar em permet entrar en "recovery mode" i llavors si entro com a root puc treballar amb consola.

Se'm va acudir demanar un altre cop d'actualitzar-me (sudo apt-get upgrade) i em va dir que dpkg havia estat interromput i que podia solventar-ho fent "dpkg --configure -a". Ho vaig fer i va començar a instal·lar coses fins que arribat un punt va aturar-se i em va dir que hi havia hagut massa errors.

Curiosament el grub ara em permet triar entre diversos kernels que tenia comentats al menú del grub, però en cap d'ells puc entrar al sistema, només em surt la pantalla per "validar-me" i després d'introduir la contrasenya no fa res.

Aquesta és la història, alguna idea????:mad:

El que més em preocupa és que no tenia còpia de la clau gpg i em caldria per signar les de la [festa de signatures]("https://wiki.ubuntu.com/CatalanTeam/FestaDeFirmes/20080426").

---

### Post by SiscoGarcia on 2008-04-28
Hola, sortosament he tornat a entrar per consola com a root i he seguit el que ja m'havia dit "dpkg --configure -a" i aquest cop ha acabat d'actualitzar-se. No entenc res :confused: pero ja m'esta be,... de moment.

---

### Post by CarlesOriol on 2008-04-28
Ja tinc el usb embastat... però he posat els ubuntu-restricted-extras i així no el puc distribuir publicament.

Ja miraré com fer-t'ho arribar per que no tinguis problemes el proper cop.

---

### Post by Joan Marc on 2008-04-28
Perquè et mostrés les diferències, havies de clicar endavant a més de triar l'opció, ho vas fer o et vas pensar que clicant endavant continuaria l'actualització (ho dic perquè jo em vaig estar com una hora prenent la decisió de clicar endavant o no xDxDxD)

Espero que ho solucionis!
Salut!

---

### Post by SiscoGarcia on 2008-04-28
> **CarlesOriol said:**
> Ja tinc el usb embastat... però he posat els ubuntu-restricted-extras i així no el puc distribuir publicament.

Ja miraré com fer-t'ho arribar per que no tinguis problemes el proper cop.

Moltissimes gracies.

Pel que veig tinc un problema amb el teclat, no hi ha accents i aixi. Ara mirare de resoldre-ho.

EDITO> Podem fer servir la mateixa via que amb les enganxines metal*liques, si et sembla.

---

### Post by SiscoGarcia on 2008-04-28
> **Joan Marc said:**
> Perquè et mostrés les diferències, havies de clicar endavant a més de triar l'opció, ho vas fer o et vas pensar que clicant endavant continuaria l'actualització (ho dic perquè jo em vaig estar com una hora prenent la decisió de clicar endavant o no xDxDxD)

Espero que ho solucionis!
Salut!

No sé si no ha quedat clar o què però sí que ho vaig fer, llavors es va posar la pantalla fosca (gris fosc) i ja no va fer res. Gràcies de tota manera.

Per cert, també he resolt el problema amb el teclat, havia modificat la configuració i s'havia quedat amb el teclat estàndard de 105 tecles; he canviat la disposició a la del model de l'ordinador i he triat d'opcions de disposició la de "Spain"+"Spain Catalan variant with middle-dot L"; amb la qual cosa ja puc escriure de manera que tothom ho pugui entendre :)

---


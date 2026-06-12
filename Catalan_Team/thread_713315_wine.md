---
title: "wine"
date: 2008-03-02
forum: Catalan Team
---

### Post by rogespierre on 2008-03-02
em recomaneu un bon manual de Wine? la veritat sq vaig bastant perdut, no he estat capaç d'executar res, si vaig directament al .exe i l'obro "amb wine" no passa res, i la config. del wine no l'entenc...

és per executar el macromedia fireworks... hi ha d'haver algun problema?

---

### Post by Kururu on 2008-03-02
a la configuracio de wine revisa a la pestanya applications, a baix, que tinguis seleccionat el SO correcte. Per certm el que no se t'obra el setup? De totes maneres donali una oportinat a Gimp

---

### Post by rogespierre on 2008-03-02
ei! el Gimp el vaig trastejant, però quan vull fer coses concretes no tinc temps a perdre....

b, a aplicacions afegeixo el fireworks.exe i a sota... windows xp? q es el windows q tinc... llavors q? lexecuto tal qual des de la carpeta en questio?

---

### Post by SiscoGarcia on 2008-03-02
rogespierre, em sembla que a tu també se t'ha espatllat el teclat, com diu en papapep en [un altre fil]("http://ubuntuforums.org/showthread.php?t=712046"):

> **papapep said:**
> kururu, tens algun problema amb el teclat, que et posa "k" enlloc de "qu" i no et posa apòstrofs,accents, ni res de res.. :-)

---

### Post by lluisalguero on 2008-03-03
jo tampoc he estat capaç de fer anar cap programa amb el wine, en vaig instalar un parell, pero no s'inicien...i tampoc em deixa desisntalarlos...quan abans em va deixar instalar-los !!!

---

### Post by Kururu on 2008-03-03
mm home jo crec que la millor opció per tenir el photoshop estable i fàcil d'instalar és emulant windows xp amb VirtualBox. És molt senzill i va molt fluid amb molta poca RAM. Després crees una carpeta compartida i comparteixes les imatges.

---

### Post by bratac on 2008-05-06
Em vull instal·lar un programa .exe i el wine no em deixa, li dic «obre amb wine» i no fa res. Com puc fer-ho per a instal·lar-lo. Ho he provat configurant el w2000 i l'xp. A part del wine s'ha d'instal·lar alguna altra cosa?

fins ara,

---

### Post by pespin on 2008-05-06
Per a córrer prgorames amb el wine recomano utilitzar la terminal situant-se a la carepta on para l'executable i fent:

```
wine fitxer_executable.exe
```

D'aquesta manera el wine va deixant informació relativa al programa que us pot servir per a veure l'error que fa que no s'engegui.

Us recomano també que us passeu per la web de wine, on hi tenen una base de dades amb informació sobre les diferents aplicacions que ha fet servir la gent amb el wine i els resultats obtinguts.

---

### Post by bratac on 2008-05-06
Gràcies, pespin, 

ara em dóna aquest error:

bratac@portatil:~/Escriptori$ wine fastm6.exe           
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing

com ho puc solucionar?

---

### Post by pespin on 2008-05-06
Pots trobar informació sobre l'aplicació fastmail amb el wine aqui:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2993]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2993")


> err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable

L'únic que et puc dir és que sembla ser que et falta la llibreria dinàmica (dll)  winedos.dll

Prova a baixar-la d'internet i col·locar-la a la carepta system32 del wine. Ara no t'ho puc dir amb certesa perqupe no tinc el wine instal·lat, pero diria que està a '/home/elTeuUsuari/.wine/drive_c/system32' o quelcom semblant).

---

### Post by lluisalguero on 2008-05-06
Tinc un problema semblant, però a mi em diu això

```
install the Windows version of Mono to run .NET executables

```

He fet cap a: [http://www.go-mono.com/mono-downloads/download.html](http://www.go-mono.com/mono-downloads/download.html), però no sé ben bé quina versió haig de fer anar :confused::confused:

---

### Post by LitusMayol on 2008-05-07
Bones gent!

Jo tinc un problema semblant. Tinc el ***Wine*** instal·lat. Jo sóc guitarrero!(:guitar: yeah!) 

Jo el ***Wine*** el vull per poder fer ús del ***GuitarPro***. He probat el ***TuxGuitar*** per reproduir va de conya, però per editar i composar (si, composo...) el ***TuxGuitar*** perd (imagineu no té opció de "copiar compassos" -i en música es repeteixen els esquemes sovint-). 

Sé que el ***GuitarPro*** es pot instal·lar amb el ***Wine***. Però no me'n surto, algú em pot passar algun manual?


Merci! ;)

---

### Post by bratac on 2008-05-07
Bones,

ja he trobat la solució al meu problema, justament en aquest web:

[http://wiki.winehq.org/PreloaderPageZeroProblem]("http://wiki.winehq.org/PreloaderPageZeroProblem")

Mireu al fòrum del web per tal de veure si podeu solucionar els vostres problemes.

---

### Post by LitusMayol on 2008-05-09
Jo no hi trobo la solució...

---

### Post by kukat on 2008-05-09
Aci hi ha un tutorial: [http://fitoria.blogspot.com/2007/08/tutorial-instalar-guitar-pro-en-linux.html](http://fitoria.blogspot.com/2007/08/tutorial-instalar-guitar-pro-en-linux.html), 

no havia pensat mai d'instal.lar-lo, però en aplegar a casa em tire de cap jo també!!:guitar:

i altre tutorial: [http://www.taringa.net/posts/linux/1210988/Instalar-Guitar-Pro-con-Wine-en-Linux-Ubuntu.html](http://www.taringa.net/posts/linux/1210988/Instalar-Guitar-Pro-con-Wine-en-Linux-Ubuntu.html)

edito: supose que amb el hardy heron funcionarà igual...esperem! A la web del Wine el Guitar Pro té Silver i Bronce (o siga, que es pot!:P)

---


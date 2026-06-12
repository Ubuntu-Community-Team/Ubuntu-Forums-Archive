---
title: "[SOLVED] Instal·lar fonts a l'OpenOffice"
date: 2008-10-07
forum: Catalan Team
---

### Post by premianenca on 2008-10-07
Bones!

Veureu he de fer un document que ha de tenir un tipus de lletra específic, la qüestió és que no sé com instal·lar-la al OpenOffice, he buscat a la guia d'ajuda, però res...

Algú em pot donar un cop de mà?

---

### Post by papapep on 2008-10-07
Instal·la el paquet **msttcorefonts**:

```
sudo aptitude install msttcorefonts
```

Això t'instal·larà al sistema, no només per l'OOffice, sinó per qualsevol programa que faci servir fonts, la majoria de fonts "estàndard" al món fosc de la vida :-)

i també, per si un dia vols instal·lar altres fonts, mira't [això]("https://wiki.ubuntu.com/CatalanTeam/Recursos/PMFUbuntuCat#Afegir%20tipus%20de%20lletra%20al%20vostre%20sistema"):

---

### Post by indiosincracia on 2008-10-07
Hola,
opció 2:
hi ha moltes pàgines que ofereixen fonts gratuites, descarregues el "ttf" i el copies a  "/usr/share/fonts/truetype"
Salut.

---

### Post by premianenca on 2008-10-07
Gràcies!

M'ho he instal·lat tal i com m'expliques en la primera manera que ho has posat, però he vist que no hi és la que necessito. He provat el que poses més abaix, però no trobo les carpetes i si les busco a través del buscador no surten i mostrant les carpetes ocultes i res...Ara ja m'he perdut...

---

### Post by papapep on 2008-10-07
I si comences pel principi i expliques quina font "tan rara" et cal? :-)

Respecte el directori desaparegut, vols dir que si fas:

```
ls -la /usr/share/fonts
```

o que si poses a la barra del navegador de fitxers (Nautilus) **/usr/share/fonts**, no et surt res??

---

### Post by premianenca on 2008-10-07
Primer, la font en qüestió és diu "Gunplay".

He fet el que em dius i em diu que el directori no existeix.

Aix, cada dia em faig més embolics amb l'Ubuntu...:(

---

### Post by papapep on 2008-10-07
Quina versió d'Ubuntu tens instal·lada?

Per cert, si us plau, acostuma't a enganxar-nos la ordre que has teclejat i el resultat exactes. Sinó ens pots enganyar sense voler. I no vull dir que ho reprodueixis aquí, sinó que tallis i enganxis aquí el que realment has fet al terminal.

---

### Post by premianenca on 2008-10-07
La versió que tinc és la 8.04.

A partir d'ara, procuraré copiar-vos-ho, encara estic una mica peix amb el funcionament del fòrum, sap greu...

Em surt això:

```
marta@marta-laptop:~$ ls-la /usr/share/fonts
bash: ls-la: command not found
marta@marta-laptop:~$ 


```

---

### Post by papapep on 2008-10-07
:-D ja sabia jo....

Això és la ordre que t'he dit:

```
ls -la /usr/share/fonts
```

i aquesta és la que tu has executat:

```
ls-la /usr/share/fonts
```

ara et toca trobar la diferència ;-)

---

### Post by indiosincracia on 2008-10-07
Doncs acabo de fer el proces que t'he explicat i funciona correctament.
vinga paciència ;-)

---

### Post by papapep on 2008-10-07
Per cert, aquí: [http://www.1001fonts.com/font_details.html?font_id=164](http://www.1001fonts.com/font_details.html?font_id=164)

podria ser que trobessis el que busques.

---

### Post by premianenca on 2008-10-07
Val! Ara ho he fet bé! Realment he d'anar a l'oculista a revisar-me la vista...

Bé, he introduït això i després el que em diu [aquí]("https://wiki.ubuntu.com/CatalanTeam/Recursos/PMFUbuntuCat#Afegir%20tipus%20de%20lletra%20al%20vostre%20sistema")però hem demana la contrassenya i no em deixa introduir-la, estic fent alguna cosa malament perquè no pugui fer-ho? :(

---

### Post by papapep on 2008-10-07
Recordes lo de posar la ordre i la resposta??

---

### Post by RainCT on 2008-10-07
> **premianenca said:**
> [...] Em demana la contrassenya i no em deixa introduir-la [...]

Sí que et deixa introduir-la, el que passa és que el que escrius és invisible per evitar que si tens algú al darrere pugui veure quina llargada té.

---

### Post by premianenca on 2008-10-07
Val, ara ja m'ha funcionat. Com no veia la contrassenya, tancava la finestra de la Terminal.

Ara ho ah fet bé, però no veig la font. A la terminal m'ha sortit això:

```
marta@marta-laptop:~$ ls -la /usr/share/fonts
total 28
drwxr-xr-x   5 root root  4096 2008-04-22 19:54 .
drwxr-xr-x 321 root root 12288 2008-09-22 14:49 ..
drwxr-xr-x  15 root root  4096 2008-10-07 16:41 truetype
drwxr-xr-x   3 root root  4096 2008-04-22 19:50 type1
drwxr-xr-x   8 root root  4096 2008-04-22 19:54 X11
marta@marta-laptop:~$ sudo fc-cache -f -v
[sudo] password for marta: 
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 13 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/marta/.fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/marta/.fontconfig: cleaning cache directory
fc-cache: succeeded

```

---

### Post by indiosincracia on 2008-10-07
perquè encara no està copiat.

copia l'arxiu .ttf a l'escriptori.
obra terminal:

sudo cp /home/a/Desktop/b.ttf /usr/share/fonts/truetype

substitueix la "a" pel nom de la teva carpeta d'usuari.
substitueix la "b" pel nom de l'arxiu .ttf

Preguntarà pel teu codi, introdueix-lo correctament encara que no es vegi, i Enter.
Tanca l'Oppen Office i engega'l de nou.
Fi.

---

### Post by RainCT on 2008-10-07
> **indiosincracia said:**
> sudo cp /home/a/Desktop/b.ttf /usr/share/fonts/truetype

substitueix la "a" pel nom de la teva carpeta d'usuari.
substitueix la "b" pel nom de l'arxiu .ttf

O copia la següent comanda sense modificar-la:
```
sudo cp ~/Desktop/*.ttf /usr/share/fonts/truetype
```


Crec que abans de tornar a obrir l'OpenOffice cal que tornis a fer el:
```
sudo fc-cache -f -v
```

---

### Post by premianenca on 2008-10-08
Viam, ahir em vaig passar una hora intentant-ho fer i res, no funciona, em surt això:

```
marta@marta-laptop:~$ ls -la /usr/share/fonts
total 28
drwxr-xr-x   5 root root  4096 2008-04-22 19:54 .
drwxr-xr-x 321 root root 12288 2008-09-22 14:49 ..
drwxr-xr-x  15 root root  4096 2008-10-07 16:41 truetype
drwxr-xr-x   3 root root  4096 2008-04-22 19:50 type1
drwxr-xr-x   8 root root  4096 2008-04-22 19:54 X11
marta@marta-laptop:~$ sudo fc-cache -f -v
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 13 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/marta/.fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/marta/.fontconfig: cleaning cache directory
fc-cache: succeeded
marta@marta-laptop:~$ sudo cp /home/marta/Desktop/GUNPLAY_.ttf /usr/share/fonts/truetype
cp: ha fallat stat() sobre «/home/marta/Desktop/GUNPLAY_.ttf»: No such file or directory
marta@marta-laptop:~$ 

```

He pensat que ho escribia malament o que no tenia l'arxiu a l'escriptori, però ho he escrit bé i l'arixu està allà. No sé si és que m'he equivocat en algun pas o és cosa de l'ordinador, però estic bloquejada i no sé com fer-ho, ja...:(

---

### Post by indiosincracia on 2008-10-08
Doncs prova l'ordre que et posa en RainCT.

---

### Post by premianenca on 2008-10-08
He posat el que m'ha dit en RainCT i em dona el mateix error que abans "*No such file or directory*"...

No ho entenc :(

---

### Post by papapep on 2008-10-08
El que no sabem és si el fitxer realment és al teu directori /home/marta/Desktop/ i es diu realment GUNPLAY_.ttf. L'Ubuntu t'està dient que alguna cosa falla :-)

Fes un:

```
ls -la /home/marta/Desktop
```

a veure què hi ha.

---

### Post by premianenca on 2008-10-08
Em segueix dient exactament el mateix:

```
marta@marta-laptop:~$ ls -la /home/marta/Desktop
ls: no s’ha pogut accedir a /home/marta/Desktop: No such file or directory
marta@marta-laptop:~$ 

```

---

### Post by premianenca on 2008-10-08
Val! Ja sé que passa! La carpeta Desktop l'he de posar en català! Vaig a veure si se m'instal·la la font!

PS: Si, ja se m'ha instal·lat. :)

Gràcies a tots per ajudar-me!

---

### Post by indiosincracia on 2008-10-08
no puc amagar la meva sorpresa, però les llengües no canvien el nom dels directoris?!? o sí...

---

### Post by RainCT on 2008-10-09
> **indiosincracia said:**
> no puc amagar la meva sorpresa, però les llengües no canvien el nom dels directoris?!? o sí...

El de l'escriptori sí, està internacionalitzat en l'Ubuntu.

---

### Post by oriolsbd on 2008-10-09
I també el de Música, Imatges, etc. :-)

Salut!

---


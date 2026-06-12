---
title: "Programa per muntatge fotografic ?"
date: 2008-06-13
forum: Catalan Team
---

### Post by sianeu on 2008-06-13
Necessito un programa per fer un muntatge fotogràfic amb so. Ha de tenir linea de temps, per que necessito que les fotos canviïn en moments concrets de la música.

Quins programes tenim per això?

Salut

---

### Post by papapep on 2008-06-13
> Friend in need is a friend in deed.

Hi Vinisha,

This is the catalan speakers forum. If you have anything constructive to say, you're invited to participate, as long as you do it in catalan, of course. Otherwise, please be kind and don't post nonsense.

---

### Post by oriolsbd on 2008-06-13
Hola, Sianeu.

Fa un temps vaig estar buscant algun programa per a fer-ho. Vaig trobar el qdvdauthor i el Mandvd. Amb tots dos em vaig trobar petits problemes, i no els vaig poder fer funcionar, però els podries provar. El qdvdauthor està als repositoris d'ubuntu. El Mandvd no està als repositoris, però si busques pel google trobaràs un fitxer .deb per instal·lar-te'l fàcilment.

Salut!

---

### Post by RainCT on 2008-06-13
@papapep: SPAM Bot :).

---

### Post by bapoumba on 2008-06-13
> **RainCT said:**
> @papapep: SPAM Bot :).

+1, I'm doing the house cleaning ;)

---

### Post by orestesmas on 2008-06-14
El digikam et permet crear un vídeo MPEG a partir d'una sèrie de fotografies, però no deu ser això el que busques, perquè la durada de cada foto és constant.

Penso que el que t'anirà millor és kdenlive, que també et permet crear clips a partir d'un conjunt de fotos, però per fer el que tu vols hauràs de crear, per cadascuna de les fotos que tens, un clip de certa durada, i aleshores muntar-ho tot en la línia de temps, ajustant la durada de cada foto a les necessitats de la música.

El resultat és exportable a una gran varietat de formats.

---

### Post by CarlesOriol on 2008-06-15
Uops...anava a recomanar el **mandvd** i el **manslide** però veig que han desaparegut.

Algú sap on trobar-los? o què ha passat?

---

### Post by sianeu on 2008-06-15
He provat uns quants programes, i el kdenlive es el que millor ha funcionat i te el que demano. Això si, es una mica lent de treballar. Però es fàcil, quan saps com funciona. Adjunto una petit manual en castellà que he trobat per la xarxa, molt bò per aprendre el més bàsic del programa.

Salut

---

### Post by sianeu on 2008-06-16
Aquest kdenlive va bastant bé, tot i que em fa algunes coses rares (probablement per poca traça en el seu us). En una d'aquestes m'he quedat amb la finestra d'entrada del programa desconfigurada: ara no es presenta com al principi amb totes les eines a la mateixa finestra, ara tinc una finestra per la linea de temps, un altre pel monitor de visualització, un altre pel cos del programa...... una mica com el Gimp. Però en aquest cas no es gaire pràctic, i no se cóm tornar a la configuració inicial. Quant més ho remeno pitjor em queda.

Si algú que el faci servir pot dir-me cóm puc tornar a recollir tot el programa en una sola finestra, li agrairé.

Salut

---

### Post by orestesmas on 2008-06-16
Ara mateix no el tinc a mà i no sé si això que et passa és degut a haver escollit alguna opció que no havies d'haver escollit, o a una desconfiguració accidental del programa. En qualsevol cas, aquesta mena de coses sempre acostumen a arreglar-se esborrant el fitxer de configuració del programa, que en el cas del kdenlive és a "/home/el_teu_usuari/.kde/share/apps/kdenlive/kdenliveui.rc"

---

### Post by sianeu on 2008-06-16
Moltes gracies orestesmas, ja havia provat de tot sense cap èxit. El fitxer estava a ./kde/share/config però finalment l'he trobat.

De tota manera "manda huevos" que diuen........ Això de Linux te cops amagats. I el torrecollons del buscador per què no el trova si te "kdenlive" en el nom (i li he dit que busqui en fitxers ocults)? En qualsevol cas aquesta questió la deixo per l'altre post que tinc obert i aquest fil el deixem per si surten nous programes per provar.


Salut

---

### Post by orestesmas on 2008-06-16
Quin buscador? El més efectiu en aquests casos és el "locate". Obre un terminal i poses:

```
locate kdenlive
```
i veuràs.

Si uses konqueror també el pots usar en forma de kioslave: Simplement poses
```
locate:kdenlive
```
com a URL. Així de simple.

---

### Post by sianeu on 2008-06-18
Jo feia servir el gràfic: Llocs/Cerca fitxers....

Gracies pel "locate", la diferencia es brutal.

Salut

---

### Post by papapep on 2008-06-18
Recorda de tant en tant, o després de fer alguna modificació/actualització important, a fer:

```
sudo updatedb
```

per actualitzar l'índex que fa servir el locate per buscar.

---


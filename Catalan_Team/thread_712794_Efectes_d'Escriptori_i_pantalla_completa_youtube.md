---
title: "Efectes d'Escriptori i pantalla completa youtube"
date: 2008-03-02
forum: Catalan Team
---

### Post by Kururu on 2008-03-02
El meu problema és el següent:
Quan tinc activats els efectes d'escriptori, les reproduccions de videos es veuen pampallugan i no puc posar pantalla completa al youtube. En canvi, si els desactivo, els videos es veuen perfectament i si que puc posar pantalla completa al youtube.
Gràcies i a reveure

---

### Post by menut on 2008-03-02
Hauries de buscar, per internet, casos relacionats amb l'acceleració 3D de la teua tarjeta gràfica.

Si és ATI o NVidida, hi ha quantitat de solucions. Si en canvi, és una integrada Intel (com la meua) és més complicat.

---

### Post by papapep on 2008-03-02
Kururu, ens hauries de dir quina targeta gràfica tens i quin controlador fas servir per la mateixa.

---

### Post by Kururu on 2008-03-02
la meva tarjeta grafica es una radeon x1550 super vaig instalar els drivers amb envy fa poc aixi que suposo k deuen ser els mes nous xD

---

### Post by orestesmas on 2008-03-02
Menut, per què dius això de les intel? Potser no dónen tantes prestacions com les ATI o NVidia, però hi ha drivers lliures i l'acceleració 3D funciona perfectament.

Penso que el problema de Kururu pot venir més aviat del mètode/driver que usa el reproductor de vídeo per presentar el vídeo per pantalla. Pot ser XShm, Xv, OpenGL, FB... Alguns d'aquests mètodes poden interactuar malament amb les X si aquestes estan fent servir acceleració gràfica. Prova de canviar el mètode. Per exemple el reproductor Xine i els basats en ell (kaffeine, etc.) permeten canviar el driver de sortida (veure captura adjunta)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=61388&stc=1&d=1204480679[/IMG]

---

### Post by Kururu on 2008-03-02
Sembla k anem millorant!!! xD
Bé orestesmas gràcies xd però encara no s'ha solucionat del tot. Utilitzant el driver xshm am el kaffeine puc veure els videos en pantalla molt petita sense k pampalluguin. Ara bé si els poso en pantalla completa, la imatge es veu am molts pocs fps i baixa la qualitat. Tampoc he solucionat el problema amb la pantalla completa del youtube que quan l'obro se m'obre una finestra que es diu npviewer.bin

---

### Post by patrickfromspain on 2008-03-02
Fent servir els efectes d'escriptori, quin seria el millor driver de sortida? En el meu cas tinc una nvidia.

salut!

---

### Post by orestesmas on 2008-03-02
A part de tot això, estàs segur que tens activada l'acceleració gràfica??

Vejam: Obre un terminal i tecleja-hi:

```
glxinfo
```

i digues-nos què et surt. En particular, mira't si al principi de la parrafada hi tens una línia que digui:

```
direct rendering: Yes
```

---

### Post by Kururu on 2008-03-03
sisi aixo segur si no no em deixaria activar els efectes descriptori. tot em va molt be numes tinc aket problema.

---

### Post by SiscoGarcia on 2008-03-03
Kururu, tens el teclat espatllat. No et separa paraules, ni et posa accents ni apòstrofs ni qu, només k. Vigila;)

---

### Post by Kururu on 2008-03-05
alguna solució més? xD el problema persisteix =(

---

### Post by Kururu on 2008-03-12
no trobo cap solució, puju el tema, gràcies

---

### Post by CarlesOriol on 2008-03-13
T'hi pots fotre flowers.

És un dels problemes que crec que estara arreglat a la propera versió del controlador. 
Jo personalment esperaré que aquesta versió s'insta&#320;li amb l'envy.

---


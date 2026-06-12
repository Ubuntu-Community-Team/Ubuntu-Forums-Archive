---
title: "[SOLVED] connectors GStreamer"
date: 2008-04-04
forum: Catalan Team
---

### Post by diablessamariken on 2008-04-04
HOla hola

ahir vaig actualitzar la meva biblioteca musical amb el Rhythmbox i avui ja no funciona... 

En intentar reproduir les cançons em dóna un error que diu el següent:

"No s'han trobat els connectors del GStreamer per a descodificar fitxers <<MP3>>"

ja em diràs perquè de sobte no els troba... ai ves..
Algú en té una idea?

Gràcies!

Salut, tabals i foc!

---

### Post by CarlesOriol on 2008-04-04
Insta&#320;la els ubuntu-restricted-extras amb el synaptic o:

sudo apt-get install ubuntu-restricted-extras

---

### Post by diablessamariken on 2008-04-04
ui... no me n'ensurto...

He baixat els paquets del synaptic i els he instal·lat (diria que correctament). M'ha dit que totes les actualitzacions s'havien realitzat correctament (o una cosa semblant), però per si de cas he anat al terminal i he posat la comanda que m'has dit. 

I tot i això, res de res.

Ara em diu: 
S'ha produït un error de reproducció.
Internal GStreamer error: state change failed.  Please file a bug at [http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer](http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer).


Què més puc fer? 


Gràcies!

---

### Post by CarlesOriol on 2008-04-04
Prova de reproduir el mp3 amb el totem que també usa el gstreamer per veure si l'error és de l rythmbox o del gstreamer.

Si executes tant el totem com el gstreamer des de el terminal ens mostrarà més informació de l'error.

---

### Post by diablessamariken on 2008-04-05
no ho entenc... ara de sobte ja funciona! i no he fet res més des de l'últim post que vaig escriure! qui els entengui que els compri els ordrinadors... 

Gràcies de nou!

Salut, tabals i foc!

Astrid

---


---
title: "[SOLVED] Com puc desar aquests arxius..??"
date: 2008-03-16
forum: Catalan Team
---

### Post by prostata on 2008-03-16
Si visiteu aquesta adreça [http://ciclops.org/th_clips.php?page=1](http://ciclops.org/th_clips.php?page=1) i cliqueu sobre alguna de les mostres podreu veure un reproducció, estic molt interesat en desar el arxius per poder treballar posteriorment amb ells...¿com puc fer-lo??

gràcies

---

### Post by papapep on 2008-03-16
Això no té res a veure amb l'Ubuntu. No te'ls pots baixar per com han programat el lloc web.

---

### Post by prostata on 2008-03-16
> **papapep said:**
> Això no té res a veure amb l'Ubuntu. No te'ls pots baixa per com han programat el lloc web.


Gràcies.... ;-)

---

### Post by menut on 2008-03-16
Qui ho ha dit que no te les pots baixar?

Són vídeos en format Quicktime (.mov), en MPG i algunes animacions Flash(.swf).

Aquí et deixo mostres:

[http://s3.amazonaws.com/ciclops_ir_2007/3803_9002_4.mov]("http://s3.amazonaws.com/ciclops_ir_2007/3803_9002_4.mov")
[http://s3.amazonaws.com/ciclops_ir_2007/3806_8804_3.mpg]("http://s3.amazonaws.com/ciclops_ir_2007/3806_8804_3.mpg")


És molt fàcil, l'únic que has de fer després de fer clic i que comenci el video és mirar el Codi font de la pàgina web, i buscar la URL del vídeo.

Després amb el Terminal, fas un

> wget [http://direcciodelvideo.com/video.mov](http://direcciodelvideo.com/video.mov)

I te'l descarregaràs al teu directori /home.

---

### Post by prostata on 2008-03-16
;-) mira que és ben sentzitlla la solució...gràcies, de vegades un espera una solució complicada i en lloc de començar per lo fàcil ho fa a l'inreves, i aixi'em lluiex-ho, gràcies ;-)

però em pasas el següent en aquesta adreça i d'altres similars,  [http://ciclops.org/view.php?id=514](http://ciclops.org/view.php?id=514)

quan s'obra la finestreta faig el que em dius amb el botò dret però no emsurt l'opció veure el còdi font de la pàgina sino que m'obra directament el totem i des de aquest no em permet dessar, ¿qué puc fer??  gràcies

---

### Post by menut on 2008-03-16
T'explico:

El vídeo ocupa un espai, diguem-li tota l'amplada de la finestra.

El que has de fer per a poder veure el Codi font és fer clic amb el botó dret en un dels cantons. Si busques per les cantonades, veuràs que et deixa clicar amb el botó dret i tindràs les opcions del Firefox.
Ho he provat, i al costat del botó de "Submit", funciona !

ATENCIÓ: Si la URL del vídeo és ```
/carpeta/carpeta2/video.mov
```

Hauràs de ficar el domini per a poder descarregar-lo, de manera que quede:

[http://domini.com/carpeta/carpeta2/video.mov](http://domini.com/carpeta/carpeta2/video.mov)

---

### Post by prostata on 2008-03-16
Gràcies ja ho tinc claret... o rosaset  ;-)

---


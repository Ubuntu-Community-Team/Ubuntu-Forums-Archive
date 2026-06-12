---
title: "Aplicació per capturar vídeo analògic"
date: 2007-12-28
forum: Catalan Team
---

### Post by orestesmas on 2007-12-28
Tinc un petit problema, a veure si algú en sap alguna cosa. La meva situació és la següent:

Tinc una targeta capturadora de TV analògica amb entrades de RF, vídeo compost i S-vídeo. Basada en el xipset Bt878 i que GNU/Linux reconeix perfectament. Puc sintonitzar els canals i veure la TV a través d'aplicacions com TVtime, xawtv, kdetv, etc. També puc veure el senyal de vídeo compost procedent d'una càmera o vídeo analògic.

Però la captura del vídeo+àudio ja és una altra cosa. He provat diverses aplicacions però cap d'elles m'ofereix resultats satisfactoris: algunes no capturen l'àudio (potser perquè s'entesten en usar l'emulació OSS enlloc de l'ALSA?, potser perquè l'àudio va a part?), altres no em commuten bé a l'entrada de vídeo compost, altres...

Cal dir que al PC on tinc la targeta no té kubuntu, sinó una debian etch AMD64. Fins i tot consideraria canviar a kubuntu si això solventés el problema.

Suposo que amb mplayer/mencoder me'n sortiré, però em fa pal ajustar les opcions de la línia d'ordres i em resisteixo a creure que no hi hagi cap programa amb una IGU decent. Per vídeo digital hi ha moltes aplicacions, però el vídeo analògic deu posar més problemes (sincronisme àudio-vídeo?).

Vaja, que si algú coneix alguna aplicació que li funcioni (encara que sigui gnome, ja veieu el meu estat de desesperació), li agrairé la informació.

---

### Post by pespin on 2007-12-29
Si tens problemes pel fet que utilitzi OSS en comptes de ALSA pots probar a instal·lar el paquet "alsa-oss" i després córrer el programa fent:

```
aoss nom_del_programa
```

Aquest paquet em sembla que carrega el OSS com a mòdul d'Alsa i et permet mesclar els sons amb d'altres programes. :)

És el que uilitzo jo quan haig d'usar el TeamsSpeak a Linux i funciona prou bé. (Diria que la qualitat del so disminueix una mica).

---


---
title: "Se m'encalla l'audio i el video amb l'Intrepid"
date: 2008-12-01
forum: Catalan Team
---

### Post by mcako on 2008-12-01
Hola, 
Fa dues setmanes vaig fer una instal·lació neta de l'Intrepid però pel que he vist no m'acaba de rutllar del tot bé.
El que em passa és que al reproduir tant música com vídeo l'audio es queda encallat en certs moments, durant uns 2 segons àprox. Ens els vídeos ja he comprovat que no és culpa de Flash (com m'havia passat altres vegades) ja que em passa tant en vídeos de Youtube com amb el Totem com en el VLC.
També s'encalla exageradament quan reprodueixo vídeos en pantalla completa, però en canvi no passa quan tinc la finestra del reproductor en una mida raonablement petita.
Lo de l'audio no sé si pot ser problema dels drivers de la targeta de so, és la que venia incorporada a la placa base.
Podria ser problema de códecs, però ja vaig instal·lar els que venien amb el VLC, així que no sé gaire que fer.

---

### Post by quitus on 2008-12-02
això mateix em passa a mi quan intento reproduir videos molt i molt pesats, estil .mkv de més de 5 Gb

Quin es el rendiment del microprocessador en la reproducció? I ja de pas, quin ordinador tens?

salut

---

### Post by mcako on 2008-12-02
Pel que he vist era problema de códecs, ara ja em funciona bé, encara que em segueixen fallant els vídeos de Youtube, tinc la versió 10 de l'adobleflash-plugin, així que no sé perquè s'encalla d'aquesta manera.  

No crec que sigui aquest el teu problema, però per si de cas poso els còdecs que he instal·lat:
```

sudo apt-get install w32codecs faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0

```

El meu ordinador és un AMD Athlon de 64bits 3000+ amb 1'5 Gb de Ram i una GeForce 256 de l'any 2000, no sé si la targeta gràfica té molt a veure però bueno.

---


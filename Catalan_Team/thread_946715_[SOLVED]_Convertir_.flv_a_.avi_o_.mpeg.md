---
title: "[SOLVED] Convertir .flv a .avi o .mpeg"
date: 2008-10-13
forum: Catalan Team
---

### Post by LitusMayol on 2008-10-13
Hola!


Us explico, he copiat un video *.flv *([PD: Te Quiero]("http://www.megavideo.com/?s=seriesyonkis&v=3UDLZ4WI&confirmed=1")) del */tmp/*, (ja s'havia carregat tot) i l'he copiat a l'escriptori. El **Totem** no me'l deixa veure... fa com si no estigués sencer. També he baixat el mateix video amb el **DownloadHelper** i no hi ha manera.

Ara, a part de intentar solucionar el tema de veure'l amb en *.flv*, he pensat que potser si el passo a *.avi* o bé *.mpeg* el podré veure. He instal·lat el *ffmpeg* i em dona dos errors diferents.


Si el provo de passar a *.avi*:
```
litus@mayolets-desktop:~/Escriptori$ ffmpeg -i PD:TeQuiero.flv PD:TeQuiero.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
PD:TeQuiero.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
litus@mayolets-desktop:~/Escriptori$ 
```


Si el provo de passar a *.mpeg*:
```
litus@mayolets-desktop:~/Escriptori$ ffmpeg -i a.flv PD:TeQuiero.mpeg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, swf, from 'a.flv':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: mjpeg, 25.00 fps(r)
Could not open 'PD:TeQuiero.mpeg'
litus@mayolets-desktop:~/Escriptori$ 
```

Alguna idea al respecte?

Merci

---

### Post by lo gambusí on 2008-10-13
Si només vols reproduïr-lo, VLC t'ho farà.

---

### Post by orestesmas on 2008-10-14
Has provat amb mencoder? hi ha infinites maneres de fer-ho, amb paràmetres diversos...

```
mencoder entrada.flv -ovc lavc -oac pcm -lavcopts vcodec=mpeg4 -o sortida.avi
```

Notaràs que no comprimeixo l'àudio (PCM) perquè a vegades se'm dessincronitza respecte el vídeo i encara no n'he trobat la causa. Si vols investigar tu...

---

### Post by LitusMayol on 2008-10-14
No. No ho havia provat.

Però tampoc rutlla. Crec que el problema el té l'arxiu en *.flv*:
```
litus@mayolets-desktop:~$ cd /home/litus/Escriptori/ & mencoder tq.flv -ovc lavc -oac pcm -lavcopts vcodec=mpeg4 -o tq.avi
[1] 7633
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'tq.flv'
Failed to open tq.flv.
Cannot open file/device.

Exiting...
[1]+  Done                    cd /home/litus/Escriptori/
litus@mayolets-desktop:~$ 


```

---

### Post by MiquelBLL on 2008-10-14
Per convertir cualsevol fitxer a cualsevol altre faig servir la web aquesta : **[http://media-convert.com/conversion/](http://media-convert.com/conversion/)** et dona moltes opcions i a mi em va molt be, be que la recomano.

---

### Post by lesergi on 2008-10-14
Hola!

Potser que els dos punts (":") del fitxer resultant siga el problema. Prova a caviar-los per, per exemple, un punt.

Per cert, si el FLV és del YouTube, sempre pots usar Elltube, un programeta que he desenvolupat que descarrega i converteix el fitxer al format dessitjat.

[http://kde-apps.org/content/show.php?content=89693](http://kde-apps.org/content/show.php?content=89693)
[http://sf.net/projects/elltube](http://sf.net/projects/elltube)

Salut!

---

### Post by SiscoGarcia on 2008-10-14
EnhoraMOLTbona lesergi :guitar:

Acabo de provar el teu programa amb aquest [vídeo]("http://www.youtube.com/watch?v=tILPYMuVBU0") que us recomano per saludable en aquests temps de suposada "crisi" i ha funcionat de meravella. Gràcies.

---

### Post by LitusMayol on 2008-10-15
Sr. **lesergi**.

Em trec el barret. Fantàstic. Simplement genial!


Pel que fa al video que jo volia convertia era de *MegaVideo* però ahir el vaig intentar veure i no està sencer: per això dóna error.

Merci a tots!

---

### Post by lo gambusí on 2008-10-15
siscogarcia: [aquí]("http://www.youtube.com/watch?v=FVKweZ2fs8g") tens el vídeo subtitulat al català :)

---

### Post by orestesmas on 2008-10-15
Home, tiu, que no et dóna un problema de conversió, sinó de que no troba el fitxer!!

I és que tu vols córrer massa, company: Has volgut posar dues ordres a la mateixa línia, però les has separades amb "&" enlloc de "&&". Si només li poses un "&" estàs indicant que la primera ordre l'executi en segon pla, i aleshores l'executa i surt, però la següent ordre agafa el context original, i s'executa des del /home, no des del /home/Escriptori

Prova-ho: fixa't en la diferència entre:

```
cd Escriptori & ls -l
```

i

```
cd Escriptori && ls -l
```

---

### Post by SiscoGarcia on 2008-10-15
> **lo gambusí said:**
> siscogarcia: [aquí]("http://www.youtube.com/watch?v=FVKweZ2fs8g") tens el vídeo subtitulat al català :)

Merci, gambusí, això sí que és fer país ;)

---

### Post by lesergi on 2008-10-15
> **orestesmas said:**
> Home, tiu, que no et dóna un problema de conversió, sinó de que no troba el fitxer!!

I és que tu vols córrer massa, company: Has volgut posar dues ordres a la mateixa línia, però les has separades amb "&" enlloc de "&&". Si només li poses un "&" estàs indicant que la primera ordre l'executi en segon pla, i aleshores l'executa i surt, però la següent ordre agafa el context original, i s'executa des del /home, no des del /home/Escriptori

Prova-ho: fixa't en la diferència entre:

```
cd Escriptori & ls -l
```

i

```
cd Escriptori && ls -l
```

Exacte, però això li ha passat amb el Mencoder. Al primer missatge amb el FFMPEG, mirant-ho bé com diu és perquè està incomplet el fitxer, no apareix ni tan sols la durada del fitxer.

Au!

---

### Post by LitusMayol on 2008-10-15
Gran Orestes. Gran.


En fi... Quin cacao que he montat per un error d'escriptura... Em sap greu! 

MErci **orestesmas**!:lolflag:

---


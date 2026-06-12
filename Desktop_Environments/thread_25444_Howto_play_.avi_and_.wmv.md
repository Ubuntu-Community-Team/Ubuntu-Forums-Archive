---
title: "Howto play .avi and .wmv"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Maikel on 2005-04-10
I get following error-message while trying to play **some** avi and wmv via totem:

```

There were no decoders found to handle the stream in file "file:///home/maikel/daten/Videos/Tauchvideos/FantasyReef_SimilanIslands.wmv", you might need to install the corresponding plugins
```

Some do play and others just play the sound but no screen.

I installed w32codecs, gstreamer0.8-plugins, libdvdcss2 and some others...

I also could not install the mplayer due depencies (sorry, in German):
```
Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
mplayer-386: Hängt ab: libfontconfig1 (>= 2.3.0) aber 2.2.3-4ubuntu7 soll installiert werden
Hängt ab: libvorbis0a (>= 1.1.0) aber 1.0.1-1 soll installiert werden
E: Kaputte Pakete
```


Anyone?

---

### Post by bihe on 2005-04-10
[QUOTE=Maikel]I get following error-message while trying to play **some** avi and wmv via totem:...
Anyone?[/QUOTE]
hi there.
i had the same problem with totem. the solution was to remove totem-gstreamer and use totem-xine instead (universe). more formats less problems with xine.

---

### Post by Maikel on 2005-04-10
Thanks, that works so far...

---


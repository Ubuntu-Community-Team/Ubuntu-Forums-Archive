---
title: "Rhythmbox won't play anything anymore"
date: 2009-01-27
forum: General Help
---

### Post by TheLions on 2009-01-27
As the tile says i can't play anything, when i press play it just jumps to next song and to next one and so till end of playlist!

Totem can play the same files so i suppose gstreamer works.

running rhythmbox from terminal gives this output:
```
marko@Zvjer:~$ rhythmbox
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0x201cae0)" of type `GString'

(rhythmbox:4838): GStreamer-CRITICAL **: 
Trying to dispose element test, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(rhythmbox:4838): Rhythmbox-WARNING **: Unhandled error: Nepoznata greška u preslušavanju

(rhythmbox:4838): Rhythmbox-WARNING **: Unhandled error: Nepoznata greška u preslušavanju

(rhythmbox:4838): Rhythmbox-WARNING **: Unhandled error: Nepoznata greška u preslušavanju

(rhythmbox:4838): Rhythmbox-WARNING **: Unhandled error: Nepoznata greška u preslušavanju

``` 
where "Nepoznata greška u preslušavanju" means "Unknown play error"

How to fix rhythmbox?

---

### Post by TheLions on 2009-01-28
bumptiously bump!

---

### Post by TheLions on 2009-01-30
anybody?:(

---

### Post by TheLions on 2009-02-04
*bump*

---

### Post by TheLions on 2009-02-09
ok i installed banshee and tried play a music file and i get this error:

```
...(Nereid:8263): GStreamer-CRITICAL **: 
Trying to dispose element playbin, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

[Error 17:01:05.104] GStreamer resource error: Failed
[Error 17:01:05.106] GStreamer core error: StateChange
[Error 17:01:05.109] GStreamer resource error: Failed
[Error 17:01:05.112] GStreamer core error: StateChange
[Error 17:01:05.117] GStreamer stream error: Failed
[Error 17:01:05.980] GStreamer resource error: Failed

```

meaning something is wrong with Gstreamer but. How to fix it?

---

### Post by kostkon on 2009-02-09
Hmmm, indeed it seems that there is a problem with *GStreamer*. You could try reinstalling all the *GStreamer* related packages.

But before doing this, you could run *gstreamer-properties* and check what *plugin* and *device* is selected for audio input and output.

Please post here what is selected and what other options there are. Or you could just try every option there is. To run *gstreamer-properties*, just press *ALT+F2* and give
```
gstreamer-properties
```

---

### Post by TheLions on 2009-02-09
thanks for the replay!

i found a problem, it is Pulse audio. I messed around with settings in gstreamer-properties and i noticed that testing with pulseaudio dosen't work!

---


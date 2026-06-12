---
title: "getting gstreamer to use alsasink"
date: 2005-05-24
forum: Desktop Environments
---

### Post by Redsun on 2005-05-24
I've encountered this problem cited throughout internet, but I failed to find a solution.

When I try to tell gstreamer to use alsa selecting alsasink with gstreamer-properties and then press the test button it tells me an error message which in english would be

Failed to construct test pipeline for "ALSA"

The pipeline exists:

```
$ gst-inspect-0.8 alsasink
Factory Details:
  Long name:    Alsa Sink
  Class:        Sink/Audio
  Description:  Output to a sound card via ALSA
  Author(s):    Thomas Nyberg <thomas@codefactory.se>, Andy Wingo <apwingo@eos.ncsu.edu>, Benjamin Otte <in7y118@public.uni-hamburg.de>
  Rank:         primary (256)

Plugin Details:
  Name:         alsa
  Description:  ALSA plugin library
  Filename:     /usr/lib/gstreamer-0.8/libgstalsa.so
  Version:      0.8.8
  License:      LGPL
  Package:      GStreamer Plugins (Debian)
  Origin URL:   http://packages.qa.debian.org/gst-plugins0.8

GObject
 +----GstObject
       +----GstElement
             +----GstAlsa
                   +----GstAlsaMixer
                         +----GstAlsaSink

Pad Templates:
  SINK template: 'sink'
    Availability: Always
    Capabilities:
      audio/x-alaw
                   rate: [ 8000, etc etc etc etc etc
``` 

Instead if I try gst-launch-0.8:
```
$ gst-launch-0.8 alsasink
ESECUZIONE della pipeline...
ERRORE: dall'elemento /pipeline0/alsasink0: Errore interno di GStreamer: problema di pad. Notificare un bug.
Informazioni di debug aggiuntive:
gstpad.c(3340): gst_pad_pull: /pipeline0/alsasink0:
pull on pad alsasink0:sink but it was unlinked
Eseuzione terminata dopo 1 iterazioni (somma 466000 ns, media 466000 ns, min 466000 ns, max 466000 ns).
``` 

Sorry for the italian, practically it says there's an internal error in GStreamer, that it's a pad problem and it tells me to file a bug. Don't have a clue to what an unlinked pad is (or what's a pad, for what it matters :) )

With amarok (which makes gstreamer select a pipeline of its choice through the preferences) obviously only the oss pipeline works. Still using artsdsink with gstreamer or even the arts engine directly leads to the app crashing.

I want to use alsa, as I've experienced (and I've read I'm not the only one) some minor glitches in mp3 playback (and by the way didn't get gaim sound to work), and would like to see if alsa solves all. Arts daemon doesn't matter for me, as long as I manage to get alsa going.

Any idea? I must confess I've learnt the existence of pipelines this very day, so I won't take offence if the solution is reaaaaaally simple and my problem is reaaaaaaaally stupid. :)

---

### Post by whiskybar on 2005-05-30
Maybe your sound card does not support hardware mixing? See 
[http://wiki.debian.net/?ALSA](http://wiki.debian.net/?ALSA), *Sharing a card among multiple processes* to find out you may want to use *dmix* with ALSA.

The quickest way of solving the problem for me was ```
cp /usr/share/doc/libasound2/examples/asound.conf_dmix ~/.asoundrc
```
HTH,  whiskybar

P.S. I just have found yet a better solution, check out .asoundrc at [http://resolute.ucsd.edu/diwaker/articles/howtos/howto-alsa-dmix.htm](http://resolute.ucsd.edu/diwaker/articles/howtos/howto-alsa-dmix.htm)

---


---
title: "Any Fraps alternatives?"
date: 2012-01-06
forum: Gaming &amp; Leisure
---

### Post by JusticeZero on 2012-01-06
I'd sort've like to be able to video some gameplay, but I don't feel like dropping a bunch of cash and praying that fraps runs in wine.
Taksi is open source, but it appears to be Windows only, and the last update was several years ago.
Not sure if there are any other options.

---

### Post by Azdour on 2012-01-06
Hi,

I've never used this but there is glc:

[http://www.dedoimedo.com/computers/glc.html](http://www.dedoimedo.com/computers/glc.html)
[http://www.ubuntuupdates.org/packages/show/198188](http://www.ubuntuupdates.org/packages/show/198188)

There's also a thread here in the Ubuntu Forum:

[http://ubuntuforums.org/showthread.php?t=587935](http://ubuntuforums.org/showthread.php?t=587935)

I would be interested to know if its any good.

---

### Post by HolgerB on 2012-01-06
Beside glc I have had good experiences with the X11 recording abilities of ffmpeg.
Some peoples with beefier systems even catch up to 720p with it. Check out youtube recordings like this:
[http://www.youtube.com/watch?v=M55sRS-XBm8](http://www.youtube.com/watch?v=M55sRS-XBm8)

---

### Post by doorknob60 on 2012-01-07
GLC is the most similar to Fraps, as it goes through OpenGL like Fraps does, and can only record 3D OpenGL stuff (same as Fraps). Ffmpeg and other alternatives like recordmydesktop are more like Hypercam (though possibly better), they can record anything in X11, but performance may not be as good. GLC can be kind of a pain to use, but once you learn how to use it, it's usually not bad. I wrote a guide on Arch wiki, and most of it applies in Ubuntu as well, except for the isntallation part. To install, just follow the instructions here: [https://github.com/nullkey/glc/wiki/Install](https://github.com/nullkey/glc/wiki/Install)

The wiki on their github is also pretty good, but this is the way I've had the most success, so here's mine: [https://wiki.archlinux.org/index.php/GLC](https://wiki.archlinux.org/index.php/GLC)

Also note that it doesn't seem to be able to record audio if you use Pulseaudio. Either record the audio separately with Audacity or ffmpeg or something, or remove Pulseaudio.

---


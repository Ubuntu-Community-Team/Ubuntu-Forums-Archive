---
title: "help me"
date: 2008-03-04
forum: Dell  Ubuntu Support
---

### Post by krishnakrishna on 2008-03-04
i had received the open source cd UBUNTU 7.10..
Iam eager to play music and video files in this platform..
But it's asking some plugins to install
I searched all over to my extent in internet
But i cant get a right plugin that supports my PC(Intel Pentium4 -2.8ghz)
Please any one of them heip me!!!!!!!

---

### Post by em3raldxiii on 2008-03-04
Most codecs are relatively simple to get going.  For example, if you double-click on certain video files, Totem (the player that usually opens on a default install) will inform you that it needs a codec (or two), then it will offer you some to install.  In that case, you can simply check the little checkbox and then apply.  After that the video should play fine.

Now, you can also open Synaptic Package Manager (system>administration>synaptic package manager) and do a search for CODEC.  You will get lots of stuff and can usually find a codec to install without much trouble.

Finally, you can install the w32codecs package which should support most of the files you are trying to play (you may have to enable universe or multiverse repositories first):

```
sudo aptitude install w32codecs
```

There is also a guide on the main ubuntu documents site ... I don't have the link off hand ...

Hope this helps!!

---

### Post by itix on 2008-03-04
For video you need the Gstreamer libraries and plugins. Go to *system => Administration => Syanptic package manager.*

There should be a bunch of different gstreamers.

You'd want to install: 
[I]gstreamer0.10-ffmpeg, 
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse[/I].

They let you handle mp3s and movies in a bunch of different ways like burning, ripping, playing and such.

---

### Post by sisco311 on 2008-03-04
You can install ubuntu-restricted-extras from Synaptic or Add Remove Programs.[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---


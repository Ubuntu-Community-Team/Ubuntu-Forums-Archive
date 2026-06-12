---
title: "Cant Install Automatix2 Error 404 on Net"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by dontgetshocked on 2008-02-19
All I get when I try to download the file  is a big 404 error from whatever site I try, any suggestions? Have they stopped allowing downloads or is it just me?

---

### Post by aysiu on 2008-02-19
The only suggestion I have is not to use Automatix.

What do you think you need it for?

---

### Post by Toontwnca on 2008-02-20
The Automatix team is working on version 3 for Pioneer Linux.
It's kind of sad in a way; as I have tried Pioneer and I will not go
back to it. 
In all fairness it was ok when they used the Ubuntu repositories,
but after they started using their own repository system it sucks. imho.

But as aysiu says; why do you need it. Everything is so easy to install
now.

---

### Post by dontgetshocked on 2008-02-20
It said I needed an unrestricted format and needed to add a repository and also FFmpeg unprotected, etc...
So I wanted to try and resolve this.
This is the instructions i received;
$ sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Now to install the package that will allow you to playback encrypted DVDs (i.e. movie DVDs you rent or buy):

$ sudo apt-get install libdvdcss2

Acquire an Unlocked, Fully Enabled Version of FFmpeg:

Grabbing FFmpeg from Mediabuntu is critical (see steps above) if you want to encode videos to H.264/AAC (ipod/quicktime), DivX/Xvid/MP3, OGG Theora, etc. Note: FFmpeg is available in the standard Ubuntu repository but it’s very much hobbled and you’ll be disappointed when certain video editing apps and transcoding programs don’t work as expected.

$ sudo apt-get install ffmpeg

---

### Post by Toontwnca on 2008-02-20
Follow this guide here: maybe you already have?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You need to have extra repositories enabled however: easy to do in Synaptic.

---


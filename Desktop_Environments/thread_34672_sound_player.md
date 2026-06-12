---
title: "sound player"
date: 2005-05-15
forum: Desktop Environments
---

### Post by Oblivious Hazard on 2005-05-15
how can I download the plugin for the "default sound player" so it can support mp3s

---

### Post by abhaysahai on 2005-05-15
Hi,
gstreamer-mad is your friend.

Abhay

---

### Post by Oblivious Hazard on 2005-05-15
?

---

### Post by Maestro23 on 2005-05-16
[QUOTE=abhaysahai]Hi,
gstreamer-mad is your friend.

Abhay[/QUOTE]

Go into Synaptic or any other package manager and search for "gstreamer". gstreamer-mad is:

This GStreamer plugin enables the decoding of MPEG audio streams.  It
currently supports the all three audio layers of the MPEG 1 standard
(Layer I, Layer II, and Layer III, the latter often colloquially known
as MP3.)

Make sure you have all the repositories via the Ubuntu guide in your /etc/apt/sources.list

---

### Post by defkewl on 2005-05-16
$ apt-get install xmms

---

### Post by Oblivious Hazard on 2005-05-16
xmms works great :)

I'm new so i dont know what Synaptic is or how to get to it  :|

---

### Post by Sam on 2005-05-16
Synaptic is the package manager. You install almost everything from here. Open it form the System menu, Administration, Synaptic Package Manager. Or from a terminal with
```
$ sudo synaptic
```
Please read the [synaptic part](http://ubuntuguide.org/#synaptic) of the [Ubuntu guide](http://ubuntuguide.org/).

---


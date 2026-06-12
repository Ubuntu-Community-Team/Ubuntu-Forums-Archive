---
title: "wine upgrade"
date: 2006-01-20
forum: Desktop Environments
---

### Post by emerick7 on 2006-01-20
I've been trying to download the new wine version today but haven't had any luck. After it's almost finished downloading, I get this error:
> W: Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.6-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.6-winehq-1_i386.deb)
  Error reading from server. Remote end closed connection

I already have wine installed, but I don't know what I should do to fix this. I'm not that experienced with this sort of issue. I'd appreciate the help.

---

### Post by morphodone on 2006-01-20
you might try this link...

[here]("http://www.winehq.com/site/download-deb")

---

### Post by GabrielWolff on 2006-01-21
The installation through the console worked for me. It's easy, and explained well at the site morphodone linked to.

Gabriel

---

### Post by Zalbor on 2006-01-21
I always have the same problem, it seems that the repository shuts the connection down if the download hasn't finished by a cetain time.

If you're using Synaptic, you can simply click "Apply" again when that happens. The file will continue downloading from where it left off, and once it's done it will install.

---

### Post by emerick7 on 2006-01-21
The wine upgrade worked after following morphodone's link. Thanks for the help... ty.

---


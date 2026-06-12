---
title: "libmp3lame.so.0"
date: 2009-02-18
forum: General Help
---

### Post by Cheemag on 2009-02-18
All I need to get Audacity working with .MP3s is this file:

libmp3lame.so.0

I have been unable to find it. Where can I download it?

---

### Post by 3rdalbum on 2009-02-18
The file should be located in /usr/lib, but it is provided by a package that doesn't come with Ubuntu by default. I believe installing the "lame" package should do the trick.

---

### Post by Cheemag on 2009-02-18
> **3rdalbum said:**
> The file should be located in /usr/lib, but it is provided by a package that doesn't come with Ubuntu by default. I believe installing the "lame" package should do the trick.

I know it goes in /usr/lib - all I need is the file!!

It won't let me install the lame package - something to do with a locked file.

Where can I download the file from, anyone know?

---

### Post by lsuhendra on 2009-02-19
Try this

[http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/](http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/)

It works for me.
I use Interpid Ibex but choose the Ubuntu 7.10 option

---

### Post by mcduck on 2009-02-19
> **Cheemag said:**
> I know it goes in /usr/lib - all I need is the file!!

It won't let me install the lame package - something to do with a locked file.

Where can I download the file from, anyone know?

that sounds simply like having two package managers open at the same time.. Close them all and then try again.

---


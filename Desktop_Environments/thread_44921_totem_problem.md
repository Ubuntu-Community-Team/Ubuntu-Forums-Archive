---
title: "totem problem"
date: 2005-06-28
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-06-28
when i try to run totem i get this error "resource busy or not available" but it hasnt been opened...the only thing i did was i went to synaptic and installed a bunch of gstreamer...packages....i dunno of totem ever worked but right now thats what it says, i rebooted my pc and it still says that...i tried to reinstall totem-gsreamer and it still says the same thing...how do i fix this?

---

### Post by psychicdragon on 2005-06-28
I've never been able to play anything with totem-gstreamer. I would recommend replacing it with totem-xine.

---

### Post by frodon on 2005-06-28
[QUOTE=psychicdragon]I've never been able to play anything with totem-gstreamer. I would recommend replacing it with totem-xine.[/QUOTE]
 like you, installing totem-xine sovle all my problems, assuming you have install all the libraries (w32codecs, libdvdcss2, ...)

---

### Post by DarkManX4lf on 2005-06-29
thanks using totem-xine does not crash totem anymore. but im not sure i can play all video types.

---

### Post by psychicdragon on 2005-06-29
Make sure that you have all these codecs installed:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

If you still can't play something try it in vlc

---

### Post by DarkManX4lf on 2005-06-30
sudo apt-get install w32codecs



that doesnt work


and yea i have the sources.list modified like the starteguide says.

---

### Post by frodon on 2005-06-30
if apt-get don't work, you have to use the sources, you can find it on internet.
Don't hesitate to post problems using the sources.

---


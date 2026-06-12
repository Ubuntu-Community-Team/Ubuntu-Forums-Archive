---
title: "Totem Mozilla Plugin Not Working"
date: 2005-10-13
forum: Desktop Environments
---

### Post by steil on 2005-10-13
Whenever the totem mozilla plugin gets called, I get an error: Cannot find file: fd://0. If I download the movie file instead of running it embedded in the browser it will play fine in Totem. Any ideas?

---

### Post by stoffepojken on 2005-10-13
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) <---- Have you done this?

---

### Post by Wolki on 2005-10-13
Interstingly, I have the same problem.... When I save the files to my hdd, they play (in totem-gstreamer), when I open them with the plugin they don't. Will try to look into this.

---

### Post by mangar on 2005-10-13
mozilla-mplayer works much better,
but I had to completly remove firefox in order to make it work

i've tested the plugin here:
[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)

and it works almost without fault.

---

### Post by steil on 2005-10-13
is there a way to get mozilla-mplayer working properly with firefox? It always wants to play things with totem....

---

### Post by thechitowncubs on 2005-10-13
[QUOTE=steil]is there a way to get mozilla-mplayer working properly with firefox? It always wants to play things with totem....[/QUOTE]
alright
This was my method worked good, just move them back to where they were to get it back to its original form
```

cd /usr/lib/mozilla-firefox/plugins
sudo mkdir totem
sudo mv libtotem* totem

sudo apt-get install mozilla-mplayer
```

---

### Post by joelito on 2005-10-14
Another choice:

Is to enable the universe/multiverse repositories and install totem-xine from there. And maybe removing the totem mozilla plugin before installing the mplayer one

---

### Post by speedsix on 2006-03-02
I have the same problem, totem gstreamer works fine with everything, totem firefox plugin never works.

---

### Post by xtoph on 2006-03-04
yeah, about that.  how would i uninstall "Totem Mozilla Plugin 1.2.0"?  cant find it in synaptic

---


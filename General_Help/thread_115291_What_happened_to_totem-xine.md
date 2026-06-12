---
title: "What happened to totem-xine?"
date: 2006-01-10
forum: General Help
---

### Post by stv on 2006-01-10
I installed Ubuntu on my desktop & liked it enough to put it on my laptop as well. Through a helpful post I found on the wiki 

Roughly speaking the tasks were these:

Uninstall totem-gstreamer
install totem-xine
add libdvdcss2
enable DMA

All that worked fine on my desktop but now, three weeks later

  sudo apt-get install totem-xine 

gives:

Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libtotem-plparser0 libtotem-plparser-dev

yet libtotem-plparser0 is installed. 

What gives? Not only are these packages missing, but the helpful wiki page that pointed me toward enabling DMA for jumpy video 

  [http://wiki.ubunutu.com/DMA](http://wiki.ubunutu.com/DMA)

seems to have disappeared (this fine page still captures most of what I've had to do)

  [http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

---

### Post by nkhansen on 2006-01-10
As for the missing totem-xine, have you enabled the universe repository? As far as I can see on packages.ubuntu.com, totem-xine is still in universe.

---

### Post by stv on 2006-01-10
arghhhh ... I thought I checked that ... shame on me.

Thanks for the sanity check

---

### Post by nkhansen on 2006-01-10
[QUOTE=stv]arghhhh ... I thought I checked that ... shame on me.

Thanks for the sanity check[/QUOTE]

You're welcome ;)

---

### Post by Limulus on 2006-01-10
[QUOTE=stv]the helpful wiki page that pointed me toward enabling DMA for jumpy video 

  [http://wiki.ubunutu.com/DMA](http://wiki.ubunutu.com/DMA)

seems to have disappeared[/QUOTE]

Try it with http**s**:

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---


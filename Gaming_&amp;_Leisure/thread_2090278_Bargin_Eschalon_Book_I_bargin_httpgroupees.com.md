---
title: "Bargin Eschalon Book I bargin http://groupees.com/"
date: 2012-12-01
forum: Gaming &amp; Leisure
---

### Post by tuppe666 on 2012-12-01
Another pay what you want with a Linux games just got it up and running looks beautiful...cannot get the sound to work on my 64-bit system .I am currently running 1.06 of Eschalon on 12.10. The usual padsp fix does not work :(. I get the error

> padsp ./Eschalon\ Book\ I 
ERROR: ld.so: object '/usr/lib32/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/pulseaudio/libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored

---

### Post by oldrocker99 on 2012-12-02
Hmmmm...I read your post and bought the game (I liked the demo I played ~4 years ago).

My result:
oldrocker99@oldrocker99-Aspire-5516:~/Downloads/Eschalon Book I Registered$ padsp ./eschalon_book_1 
Segmentation fault (core dumped)

and this is on a 32-bit 12.10 system.


Hmmmmm...

Later...
I enabled the xorg-edgers PPA and did an upgrade, which included Linux 3.7.04, and now the game runs (with sound if I run padsp ./eschalon_book_1). I presume the upgrade did something, although I don't really know what, except that there's no seg fault.

---

### Post by tuppe666 on 2012-12-02
> **oldrocker99 said:**
> Hmmmm...I read your post and bought the game (I liked the demo I played ~4 years ago).

My result:
oldrocker99@oldrocker99-Aspire-5516:~/Downloads/Eschalon Book I Registered$ padsp ./eschalon_book_1 
Segmentation fault (core dumped)

and this is on a 32-bit 12.10 system.


Hmmmmm...

LOL thank you for taking the plunge. I had it up and running straight away. I'm surprised at the lack of news around this. It looks a pretty decent game.

---

### Post by tuppe666 on 2012-12-02
Not sure how I should continue as the problem does not seem to Eschalon Book I. It seems to be with padsp on my system.

Real error is > ld.so: object '/usr/lib/x86_64-linux-gnu/pulseaudio/libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.


---


---
title: "Cannot install GuiTuner"
date: 2008-12-23
forum: General Help
---

### Post by Masquerade on 2008-12-23
Hey everyone.
Im having issues installing [GuiTuner]("http://digilander.libero.it/guituner/index.html").

I download the .deb package
[(guituner_0.02.deb, (436kb), source code and binary code for Debian 2.2 with Gnome 1.2, with FFTW.)]("http://digilander.libero.it/guituner/downloads.html").

and open it. What it tells me is: Error: Dependency is not satisfiable: libglib1.2

Somehow, i dont find a similar called package for intrepid, further, i have
libglib2.0
libglib1.2-dbg - The GLib library of C routines (debug)
libglib1.2-dev - The GLib library of C routines (development)
libglib1.2ldbl - Die GLib-Bibliothek mit C-Routinen
installed

Can someone help me with this?
Thanks a lot yet!
benny

---

### Post by Cenoforums on 2009-01-25
same here, I've trying to install a guitar tuner for ubuntu for about half an hour. I wanted to play guitar, not handle shady dependencies O_o

---

### Post by matze_ on 2009-01-25
Try gtkguitune from the universe repository. Works for me.

---

### Post by Masquerade on 2009-08-16
great, thanks a lot

---

### Post by bjerngaard on 2009-12-26
GuiTuner has not been maintained for quite a while. Seems it depends on some outdated libraries ([gdk-imlib1]("http://packages.debian.org/search?keywords=gdk-imlib1") and possibly others) that were part of Debian until 'Lenny' version. [libimlib2]("http://packages.debian.org/search?keywords=libimlib2") seems to have replaced gdk-imlib1.

Too bad as GuiTuner seems simpler than GtkGuitune (and I was hoping its use of FFT would make it better than GtkGuitune which uses Schmitt-triggering).

---

### Post by bjerngaard on 2009-12-27
Just a bit more information for people looking for a guitar (or other chromatic / instrument) tuner:

Try 'fmit' and 'lingot' that are both available in the 'universe' repository.

fmit works better for me but it is easy to try both.

End of the day I'll probably end up using a Symbian application on my Nokia phone. In case you got a Symbian phone, check [Chromatic Tuner for Symbian/S60 devices]("http://hqh.unlink.org/s60/index.php?p=download"). [Here]("http://www.brighthub.com/mobile/symbian-platform/reviews/30748.aspx") is a review of it. It's free and the source seems to be available.

---


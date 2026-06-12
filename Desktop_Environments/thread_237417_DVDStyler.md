---
title: "DVDStyler"
date: 2006-08-16
forum: Desktop Environments
---

### Post by petri on 2006-08-16
dvdstyler: error while loading shared libraries: libwxsvg.so.0: cannot open shared object file: No such file or directory

I did have DVDStyler installed before and running. After moving the /home to it's own partition I can't get DVDStyler to run. Where I can found this libwxsvg.so.0?

Yes, I've searched and the answer wasn't quite good enough. Nowadays you can install .deb packages whitout CLI in Dapper.

---

### Post by DoctorMO on 2006-08-16
hmm, I've had quite a few bad experencies with DVD Styler and I gave up I must admit.

have you tried the following:

sudo updatedb
locate libwxsvg

this should tell you if there are any files with that name. if there is a lib with a similar name like libwxsvg.so but not libwxsvg.so.0 you might get away with linking. (man ln)

---

### Post by petri on 2006-08-16
Thanks

but there was not a file: libwxsvg

My DVDStyler did work flawlessly untill I moved the /home catalogue to it's own partition. 

Now I have uninstalled and reinstalled  DVStyler, rebooted but can't get it run again.

---

### Post by meth on 2006-09-04
You have to install [http://wxsvg.sourceforge.net/](http://wxsvg.sourceforge.net/) before install dvdstyler

---

### Post by petri on 2006-09-05
Thanks but it didn't work. 

GDebi Package Installer:
```
trying to write over "/usr/lib/libwxsvg.so.0.0.0" which also is included in package libwxsvg0
dpkg-deb: underprocess paste killed by signal (Broken pipe)
```

This happens everytime I try to install it. I have downloaded the package from several locations and everyone ends the same.

When I usen the -f alternative in terminal -- same fault again but now I had the update icon signaling a broken package, which , of course couldn't be fixed by Synaptic. :-k

---

### Post by petri on 2006-09-05
The solution for me was to uninstall this package in Synaptic: ```
libwxsvg0
``` and install wxsvg **from repositories** (with Synaptic), not the new one from [http://wxsvg.sourceforge.net/](http://wxsvg.sourceforge.net/)

DVDstyler is working now but I haven't checked if any other program is missbehaving but in that case I'll return to this thread. :-D

P.S. They are in repos IF you add two lines like [here]("http://dvdstyler.sourceforge.net/wiki/Installation")

---


---
title: "get message &quot;Gtk-WARNING **&quot; in terminal when trying to run a program"
date: 2009-01-31
forum: General Help
---

### Post by phantomjoker on 2009-01-31
Hi there, I was looking for some Dj'ing software and found DBmix (DBmixer). It seemed to install ok, but when i typed in 

```
dbmixer
```

in the terminal i got the following message
> 
Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory
DBMixer ERROR: could not create shared memory for system data.
 _**Hint: Make sure that dbfsd has been started.**_
 errno: : No such file or directory
DBMixer: could not detach memory segment.: Invalid argument

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkObject'

Gtk-CRITICAL **: file gtksignal.c: line 724 (gtk_signal_connect): assertion `object != NULL' failed.


So as the highlighted hint suggested, i ran dbfsd (what was a package that i noticed installing with dbmix. But then i got the message

> init_audio: cannot open device "/dev/dsp": Device or resource busy
Could not open main audio device.: Illegal seek

Any ideas? (i would use another software if anyone had any suggestion, but all i know of is djplay which just freezes on my sustem!)

---

### Post by phantomjoker on 2009-02-01
bump

---


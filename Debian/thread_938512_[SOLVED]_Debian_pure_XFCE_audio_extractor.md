---
title: "[SOLVED] Debian pure XFCE audio extractor"
date: 2008-10-05
forum: Debian
---

### Post by timzak on 2008-10-05
Can someone recommend an audio extractor for a pure xfce environment?  It is my understanding that Serpentine has gnome dependencies.  I have a low spec Debian xfce system that I'd like to occasionally use to extract .ogg files from my audio cds.  I need it to have a GUI, preferably something simple like Serpentine, but without gnome dependencies.

Any suggestions?  Or am I mistaken about Serpentine's dependencies?

Thank you.

---

### Post by p_quarles on 2008-10-05
For minimal dependencies, you might look at Asunder or ruby-ripper. They are both Gtk+ apps, so will provide a well-integrated GUI, but neither is in the Debian repositories. There may be packages for them out there, but otherwise you'll have to get the source.

You can always see the dependencies of a package by running:
```
apt-cache depends package_name
```

---

### Post by timzak on 2008-10-05
Asunder looks nice!  Could I get instructions on how to install?  I'm new to installing from source.

I also notice ripperx in the repos.  That's not as pretty, but do you have experience on how well it works?

Thanks.

---

### Post by timzak on 2008-11-11
I ended up sticking with ripperX as it is the only one available in Etch's repos, and Etch's version of gdebi does not work with Asunder.

---


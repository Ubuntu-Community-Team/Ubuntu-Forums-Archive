---
title: "gnome-do but no docky?!?"
date: 2009-02-04
forum: General Help
---

### Post by kadafi69 on 2009-02-04
so i installed gnome-do to much anticipation only to find no 'docky' option in the preferences. how do i get it working?

---

### Post by Skerit on 2009-02-04
What version did you install, the one from the ubuntu repo? If I remember correctly, that did not have Docky yet.

Try adding GnomeD-o's own repository to the /etc/apt/sources.list file:

deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main

And reinstall it.

---

### Post by kadafi69 on 2009-02-04
Thanks. I added those repo's but im gettin a public key error now.

---

### Post by kadafi69 on 2009-02-04
well it installed anyway and works. thanks

---

### Post by Dooley on 2009-02-04
Do you notice when you press win-space for docky the search image comes up in really low resolution?

---

### Post by Tibuda on 2009-02-04
> **Dooley said:**
> Do you notice when you press win-space for docky the search image comes up in really low resolution?

Make sure you are using an icon theme with "scalable" icons for your applications.

---

### Post by Dooley on 2009-02-05
I'm using the human icon theme, is that scalable?

---

### Post by Dooley on 2009-02-05
I tried a few different icon sets, no luck. Seems to always stay the same image.

---

### Post by Dooley on 2009-02-05
Ah solved it in fact, you seem to have to open docky's preferences before it adjusts the icons it uses.

Thanks.

---


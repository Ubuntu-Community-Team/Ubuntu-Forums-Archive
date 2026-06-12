---
title: "Tried to install gtk2.0"
date: 2010-01-26
forum: Desktop Environments
---

### Post by greyash99 on 2010-01-26
Hello. I was trying to install gtk2.0 so I could try and learn the api. I installed the dependencies, and after installing cairo, almost all text is turned into boxes. Screenshot shows my problem. Anyone know what's wrong?

---

### Post by greyash99 on 2010-01-28
Anyone?

---

### Post by mcduck on 2010-01-28
How did you try installing it? And what exactly didi you install?

If you are using Gnome, XFCE or LXDE as your desktop you already have GTK2.0 installed by default. That's what Gnome uses to draw all your applications.

---

### Post by greyash99 on 2010-01-28
I built it from source, and it was the development package. Got it from [http://www.gtk.org/download-linux.html](http://www.gtk.org/download-linux.html), but what I think broke it was Cairo libcairo2-dev from the Ubuntu repositories.

---

### Post by mcduck on 2010-01-28
then I suppose the problem is the package you cmpiled yourself. Try unsinstalling the stuff you compiled yourself and instead installing the GTK2 development packages from Ubuntu's repositories.

---

### Post by greyash99 on 2010-01-28
How would I do that?

---

### Post by mcduck on 2010-01-29
The source code probably came with instructions, if not the only way is to track down every file it installed and remove them manually. (by the way, I recommend using checkinstall in the future when compiling stuff, it makes a .deb package from the source and installs that through the package management, making it really easy to uninstall).

After you gothte hard part sorted out, installing GTK2 development packages should be as simple as running "sudo apt-get install libgtk2.0-dev".

---

### Post by greyash99 on 2010-01-30
Thanks, I'll give that a shot.

---


---
title: "xCHM does not display anything"
date: 2005-08-06
forum: Desktop Environments
---

### Post by Killy on 2005-08-06
Hi.

I installed xCHM on my box with: 
```
sudo apt-get install xchm
```
Everything went fine but xCHM does not display help files. If I try to open a file like [this](http://www.starsoftmultimedia.com/download.php?file=/manual/SmartOLE/SmartOLE.chm) (117.0 kb), xCHM starts with a white screen and nothing more.

Any Ideas what might be wrong?

Thanks
Killy

Edit: Okay, it seems that xCHM is somewhat limited in the supported kinds of .chm files ([see here](http://xchm.sourceforge.net/technotes.html)).

Does anyone know how I can display *.chm files created in Windows with Ubuntu?

---

### Post by lol on 2005-08-07
strange, I was able to open the file without any problem...

Anyway, you may want to try gnochm instead. There is no package though, so you will have to build it.

[http://www.gnomefiles.org/app.php?soft_id=257](http://www.gnomefiles.org/app.php?soft_id=257)

---

### Post by Killy on 2005-08-07
Thanks for your answer. I tried gnochm but it says...
```
You do not have all of the required Python modules to run gnochm.
Check the gnochm README file for tips on how to fix this.
What follows is the error description highlighting the problematic module.

No module named chm
```
...when I try to start it.

In the readme the following requirements are listed:
```
  - PyCHM (or python-chm)  (>= 0.8.2)
  - Python                 (my version = 2.2.1)
                           Also, python must have gettext and locale modules
  - pygtk2                 (my version = 1.99.12)
  - pygtk2-libglade        (my version = 1.99.12)
  - gnome-python2          (my version = 1.99.11)
  - gnome-python2-gtkhtml2 (my version = 1.99.11)
  - gnome-python2-gconf    (my version = 1.99.11)
  - gnome-python2-bonobo   (my version = 1.99.11)
```
I am a Linux beginner and I have no idea how to find and install these packages. (Didn't find them in Synaptic.)

Edit: The "my version" info refers to the system of the readme author.

---


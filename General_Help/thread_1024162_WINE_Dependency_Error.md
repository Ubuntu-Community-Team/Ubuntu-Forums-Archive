---
title: "WINE Dependency Error"
date: 2008-12-28
forum: General Help
---

### Post by lightshayde on 2008-12-28
I am using the DEB package for Wine, but when I run the file, the following error message comes up and it won't let me install. 

The red text, presumably, is the error message: it reads, "Dependency is not satisfiable: libaudio2".

What does this mean? Should I google "libaudio2" or what?

---

### Post by ibuclaw on 2008-12-28
Why not add wine to your sources.list from winehq?

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)


But, to answer your question, open a terminal and type in the following:
```
sudo dpkg -i wine*deb
sudo apt-get install -f

```
and apt will fix (install) any dependencies required by the wine deb package, and ultimately install the dependency broken wine package that you tried to install in the first place.

Regards
Iain

---

### Post by dagwaging on 2008-12-28
What version of WINE are you trying to install? I tried to install WINE 9.4.6 due to regression problems and got this too. I found libaudio2 but it too had dependencies. Finally I satisfied all but one dependency which it wouldn't let me install. If possible, try installing a newer version of WINE.

---

### Post by lightshayde on 2008-12-28
This is the newest version of WINE in a .deb package, 1.1.10.

And the problem is, the computer that is running on Ubuntu is not connected to the internet. Which means I can't use APT...right?

---

### Post by ibuclaw on 2008-12-28
Unfortunately, this does mean that apt will not work.

If possible, I would advice you to perhaps get it connected to install the software, it will save a lot of headaches from manually downloading/installing the dependencies for wine yourself.

[http://packages.ubuntu.com/intrepid/wine](http://packages.ubuntu.com/intrepid/wine)

Regards
Iain

---

### Post by lightshayde on 2008-12-28
So, if I didn't connect to the web, then I would have to install ALL the dependencies manually? >.<

K, thanks.

---


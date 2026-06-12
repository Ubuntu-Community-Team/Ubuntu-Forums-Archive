---
title: "QAvimator"
date: 2012-07-10
forum: Gaming &amp; Leisure
---

### Post by Scott Vierge on 2012-07-10
Hola,

Downloaded the latest version of qavimator, though having a hard time getting the program running. If a person could take a gander, the program is free to download @[http://qavimator.org/#download]("http://qavimator.org/#download"), just difficult to get running appears.

Muchos Gracias.

---

### Post by BcRich on 2012-07-11
Hi Scott Vierge
Thanks for pointing out this app, looks really interesting. I see what you mean about it being a little difficult to get running :)
It's in development so you'll probably need to add some additional packages to your system. This is what worked for me

```
sudo apt-get install subversion build-essential libqt4-dev freeglut3 freeglut3-dev qt4-qmake qt3-dev-tools cmake
``` 

I also installed pyside-tools (but I don't think this was necessary)
I'm not sure if cmake is a part of build-essentials but it was listed as a dependency on the qavimator install doc so I added it to the list. Basically it's what worked for me on an (almost vanilla) Ubuntu 12.04, you'll also need your graphics card drivers working prior to installing the listed packages.
you can then follow the instructions on the website [http://qavimator.org/#download](http://qavimator.org/#download) under Linux (SVN)

if you get any errors be sure to post the output from terminal here and I'll do my best to help you.
Good luck :)

---


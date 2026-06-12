---
title: "optirun problems"
date: 2012-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blackmail on 2012-05-12
Hello, I have a problem with my Optimus mainly under linux Ubuntu 11.04

I have recently bought a Dell Inspirion N5110 laptop. If I know correctly it has a Core i5 processing unit, an nVIDIA 525 and also some Intel video card. now the pain is with the "smart" switching between the cards.

I know i am supposed to run the application with the optirun command but this works right after purging everything and reinstalling the mesa drivers as well as the nVIDIA drivers and then bumblebee. When I restart it runs like a charm, but if i start up a game with optirun, let's say World of Warcraft, well the whole thing works perfectly. Ok, i finish playing and stop the game, when i reboot my computer or suspend it and then resume usage, the open gl support goes away and the command glxinfo outputs:
```
glxinfo | grep "OpenGL version"
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

and if i purge again and reinstall, well then i will have the functionality back, but i don't think this is the right way to do it, also it is curious that with optirun from terminal WOW still runs like a charm...

---

### Post by Lekensteyn on 2012-05-14
When installing Bumblebee, it also installs the nvidia-current driver. After removal of bumblebee, it does not automatically remove the nvidia driver. For that, you need to run:
```
sudo apt-get purge nvidia-current
```

Btw, you do not need to install nvidia-current manually if you install bumblebee as it's pulled in as dependency. [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by blackmail on 2012-05-15
Well I had also other issues because of the outdated kernel, so i just decided to install Ubuntu 12.04, and install bumblebee as well as switch to the gnome interface, and things seem ok for now, but since unity everything has become a bit of an uncertainty :)

anyway hope this works, also I am very curious how Ironhide is supposed to work... maybe i will try that as well, just out of curiosity :)

---

### Post by Lekensteyn on 2012-05-16
Ironhide uses the same idea as Bumblebee (both are forks of the old bumblebee from Martin Juhl). See also [http://wiki.bumblebee-project.org/FAQ](http://wiki.bumblebee-project.org/FAQ)

Bumblebee aims at stability and uses bbswitch as more reliable card toggle method.

---


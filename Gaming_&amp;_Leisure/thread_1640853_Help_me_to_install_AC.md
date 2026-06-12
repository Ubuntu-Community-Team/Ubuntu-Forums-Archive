---
title: "Help me to install AC"
date: 2010-12-08
forum: Gaming &amp; Leisure
---

### Post by xXDestroyerGRXx on 2010-12-08
Hello im running ubuntu 10.10 and i want someone to make installation with tarball to my desktop from his pc because i am sooooooo noob :D

---

### Post by xXDestroyerGRXx on 2010-12-08
I found this code at google.

```
cd ~ && wget  http://downloads.sourceforge.net/project/actiongame/AssaultCube%20Version%201.1.0.4/AssaultCube_v1.1.0.4.tar.bz2  && tar -xjf AssaultCube_v1.1.0.4.tar.bz2 && mv 1.1.0.4  .AssaultCube_1.1.0.4 && rm AssaultCube_v1.1.0.4.tar.bz2  && cd ~/.AssaultCube_1.1.0.4 && sh  install_desktop_menu.sh

```

---

### Post by Jahid65 on 2010-12-08
This command means
1 cd ~ means your home directory.
2 wget & the link means you are downloadind AC. 
3 tar option means you are extracting the tar package.
4 sh menas you are installing it.

you can run the command. But be sure that, the download link is correct. I would suggest you to manually download it first in your home folder. Then run this command
```
cd ~/.AssaultCube_1.1.0.4 && sh install_desktop_menu.sh
```You'll need to make sure the appropriate OpenGL drivers are installed, plus these libraries:
* *libSDL 1.2*
* *libSDL_image*
* *OpenAL-soft*
you can install these
```
sudo apt-get install libsdl1.2 libsdl-image1.2 libopenal1 libsdl-ttf2.0-0
```

---


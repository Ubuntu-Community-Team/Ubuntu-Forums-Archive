---
title: "How to install AssaultCube 1.1.tar.bz2?"
date: 2010-08-05
forum: Gaming &amp; Leisure
---

### Post by TheNerdAL on 2010-08-05
So AssaultCube 1.1 has been released yesterday and it is not in the repos yet so I wanted to install using the tar.bz2 files but I have no idea how. Can anyone help me? 

Thank you! :)

---

### Post by Perfect Storm on 2010-08-05
[http://assault.cubers.net/docs/getstarted.html](http://assault.cubers.net/docs/getstarted.html) Tells you how to use it.

---

### Post by TheNerdAL on 2010-08-05
> **Artificial Intelligence said:**
> [http://assault.cubers.net/docs/getstarted.html](http://assault.cubers.net/docs/getstarted.html) Tells you how to use it.

I'm sorta a noob at Linux here. :P

---

### Post by Perfect Storm on 2010-08-05
> Linux
You'll need to make sure the appropriate OpenGL drivers are installed, plus these libraries:
* libSDL 1.2
* libSDL_image
* OpenAL

You'll find them in synaptic package manager, or by terminal:
```
sudo apt-get install libsdl-image1.2 libopenal1
```


> Linux
Download the tarball from Sourceforge. Extract it somewhere where you have permissions to read/write.

Download: [http://assault.cubers.net/download.html](http://assault.cubers.net/download.html)
right click it and choose extract.
or via 
```
wget http://sourceforge.net/projects/actiongame/files/AssaultCube%20Version%201.1.0.0/AssaultCube_v1.1.0.0.tar.bz2/download
tar jxf AssaultCube_v1.1.0.0.tar.bz2
```


> Linux
In a console, change your location (cd) to the main AssaultCube directory and then execute assaultcube.sh.

click the 1.1.0 folder. 
Click  'install_desktop_menu.sh' and choose run.
There'll now be a game launcher in the Applications menu for AC 1.1.0
Or by terminal
```
cd /into/Assault/directory
./install_desktop_menu.sh #or
./assaultcube.sh # for just launching the game
```

---

### Post by TheNerdAL on 2010-08-06
Wow, that was easy! Thanks! :)

---


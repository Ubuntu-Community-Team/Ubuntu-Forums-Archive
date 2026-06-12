---
title: "NeoRageX + Wine ... No joystick support?"
date: 2005-07-22
forum: Gaming &amp; Leisure
---

### Post by KirinRiotCrash on 2005-07-22
Hello,

I decided to give it another shot in installing Linux and so far, I kind of like. It's not the same as my old Mac but at least I'm not using Windows, which I really don't feel too comfortable working in. However, one thing I do miss is a bit of emulation. Right now, I'm trying to get NeoRAGEx under Wine to work properly. I'm using the 20050524 build of Wine. I tried using the wine that came with Crossover Office but NeoRAGEx doesn't load properly. So I'm using the Wine downloaded from the wine.sourceforge.net repository, which would allow me to run it properly, only there's no joystick support.... which leads to my real problem:

My problem is that I can't get my Microsoft Sidewinder USB to work with NeoRagex. KDE's Joystick control panel in the Settings knows that it's there but it doesn't want to work under NeoRage ... is there something I have to do in Wine to get it to work? What I was really thinking is finding some kind of button-mapping program and use that but I can't think of such a thing for Linux.

---

### Post by KirinRiotCrash on 2005-07-22
I just want to follow up my own post and tell everyone that I found one solution to this. 

After a bit of Googling, I found and installed QJoyPad and used it to remap my Sidewinder's buttons to certain keys on the keyboard.

You can download QJoyPad here: [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/) ... there's a Debian build, but when I used it, it couldn't tell I was running the program until I noticed a big invisible gap in my system tray so I  just downloaded the source code and rebuilt it myself using the "./config-make-make install" mantra and it worked like a charm. Once it's installed, just click on the icon on the system tray that resembles a controller and then you can configure your keymappings and that sort of thing.

Enjoy!

---

### Post by bored2k on 2005-07-23
Just a question: any of you got sound on NeoRageX ? How ? Right now I'm emulating finalburnalpha via Cedega 4.4 and its working great, except I got no sound :(.

---

### Post by bored2k on 2005-07-23
I am _not_ being able to load roms to neoragex. How are you guys doing it ?

---

### Post by KirinRiotCrash on 2005-07-23
[QUOTE=bored2k]I am _not_ being able to load roms to neoragex. How are you guys doing it ?[/QUOTE]
 When loading roms, I just dump the rom zips in the usual /roms folder and load it like normal. As with the sound problem, if you're using the Wine from the Ubuntu repositories, you might also have to install the libwine-alsa package as well. That's just a guess there. Personally, I haven't had problems with the sound.

---

### Post by synap on 2005-07-31
[QUOTE=KirinRiotCrash]I just want to follow up my own post and tell everyone that I found one solution to this. 

After a bit of Googling, I found and installed QJoyPad and used it to remap my Sidewinder's buttons to certain keys on the keyboard.

You can download QJoyPad here: [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/) ... there's a Debian build, but when I used it, it couldn't tell I was running the program until I noticed a big invisible gap in my system tray so I  just downloaded the source code and rebuilt it myself using the "./config-make-make install" mantra and it worked like a charm. Once it's installed, just click on the icon on the system tray that resembles a controller and then you can configure your keymappings and that sort of thing.

Enjoy![/QUOTE]

When I attempt to make I get the following error:
make: *** No rule to make target `/usr/lib/qt/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.

I cant find what package that QT is in, any help would be appreceated.

---

### Post by KirinRiotCrash on 2005-07-31
[QUOTE=synap]When I attempt to make I get the following error:
make: *** No rule to make target `/usr/lib/qt/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.

I cant find what package that QT is in, any help would be appreceated.[/QUOTE]
 My guess is that you need to install Qt, or at least the -dev stuff related to Qt to build the app. Synaptic has a bunch of Qt packages. If I had to guess, it would be libqt3-mt-dev ... but someone correct me on that.

---

### Post by synap on 2005-08-01
Thanks! That seems to have taken care of it.

---


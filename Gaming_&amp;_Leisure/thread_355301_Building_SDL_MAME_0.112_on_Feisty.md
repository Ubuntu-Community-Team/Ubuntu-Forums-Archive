---
title: "Building SDL MAME 0.112 on Feisty"
date: 2007-02-07
forum: Gaming &amp; Leisure
---

### Post by benbruscella on 2007-02-07
Since MAME has just had its 10th anniversary, I thought others might want to try MAME with ubuntu, so here are the instructions to build and use SDLMAME on a fresh Feisty install...

**Package Preparations:**

Install Compilers:
```
sudo apt-get install build-essential
```

Install ZLIB development package:
```
sudo apt-get install zlib1g-dev
```

Install SDL development package:
```
sudo apt-get install libsdl1.2-dev
```

Install expat libraries:
```
sudo apt-get install libexpat1-dev
```

Install xinerama libraries:
```
sudo apt-get install libxinerama-dev
```

Thats it.  Now you need the sdl source code, so download it from here:
[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)
[http://rbelmont.mameworld.info/sdlmame0112.zip](http://rbelmont.mameworld.info/sdlmame0112.zip)
Note: you can't use wget, you have to visit the web page and download it.

unzip it:
```
unzip sdlmame0112.zip
```
```
cd sdlmame0112
```

Build it:
```
make
```

When it's done, you'll see mamepm in the directory.

To actually run MAME, you'll need some arcade roms.  Get a legal one here:
```
cd roms
wget http://www.mamedev.org/roms/gridlee/gridlee.zip
cd ..

```

Try it out:
```
./mamepm gridlee
```

Have fun

---

### Post by vvlist on 2007-02-12
Great, thank you for posting this. I'll try it when I upgrade to feisty.

---

### Post by Brunellus on 2007-02-12
moving this to gaming forum.

---

### Post by c.falco on 2007-02-26
As posted on the [SDLMame  forum]("http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1"), I uploaded the source package on REVU for reviews.
I hope they will be included in the official universe/multiverse repository in the future. :)

Binary are also available for dapper, edgy and feisty [here]("http://wallyweek.altervista.org").

---


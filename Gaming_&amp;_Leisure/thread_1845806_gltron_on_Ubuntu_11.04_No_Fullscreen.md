---
title: "gltron on Ubuntu 11.04 No Fullscreen?"
date: 2011-09-17
forum: Gaming &amp; Leisure
---

### Post by TurtleKing on 2011-09-17
Anybody know how to make the game go full screen? There is a recommendation to edit config in a .gltron folder in home, but I don't have one.:(

---

### Post by michaelb28 on 2011-09-19
[B]UPDATE: I just reinstalled it.  Please read my next post.
[/B]
I don't have gltron installed anymore, but I remember editing the config file to make it fit my EeePC screen (800x480).

If you run gltron from the terminal, does it give you an error message about not finding ~/.gltronrc, using defaults instead?


You may try searching in the application's folder to see if they have a default config file and copy that to your home folder as a basis for your .gltronrc file.

try typing this at the command prompt to find out where is is:
```
whereis gltron
```

---

### Post by michaelb28 on 2011-09-19
On my system (Ubuntu 11.04), the ~/.gltronrc is created the first time the application runs.

Its a hidden file, are you sure you don't have it? See if you have the file with this command:
```
ls ~/.gltronrc
```

Change the line
```
settings.windowMode = 1
```
to 
```
settings.windowMode = 0
```

and you should get it fullscreen.

There is also a settings.width and settings.height line you can change to match your screen resolution if you need to.

---

### Post by TurtleKing on 2011-09-20
I was looking for a hidden folder not a file.:lolflag: Thanks for the help.

---

### Post by tnkie on 2011-09-21
I made an art pack for this about 10 years ago (I was like 13), it's still there too! What a great game :)

---


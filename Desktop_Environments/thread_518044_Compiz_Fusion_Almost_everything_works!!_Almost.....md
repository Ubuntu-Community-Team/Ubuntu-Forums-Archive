---
title: "Compiz Fusion: Almost everything works!! Almost......."
date: 2007-08-05
forum: Desktop Environments
---

### Post by noneedforwindows on 2007-08-05
(linux newbie)
Hello, I recently installed ubuntu on my pc. I have almost everything working that I need except 3 things. I am using the ati fglrx driver and have compiz fusion installed. Windows are waving at me cubes are turning, but I cant seem to get mouse cursors to work, Full screen screensavers are kinda choppy (when I click view fullscreen its fine, when it is acually running the screensaver it is very slow) and my Java windows open blank (limewire) . With the java problem I installed  ubuntu restricted extras from add/remove. I believe it installed java 6 as I had java 5 before. Any suggestions???? I would greatly appreciate it, I will be a happy man

---

### Post by noneedforwindows on 2007-08-05
Nothing, eh?

---

### Post by jairo.serrano on 2007-08-05
the fix..

```
sudo gedit /etc/environment
```

add the next line:

```
AWT_TOOLKIT="MToolkit"
```

[Haciendo que beryl y java swing funcionen/]("http://edgjavier.wordpress.com/2006/11/19/haciendo-que-beryl-y-java-swing-funcionen/")

:guitar:

---

### Post by noneedforwindows on 2007-08-05
tried the last command and edited the file, now limewire finishes the load, then doesn't open. I tried this too, did this mess it up??? [http://www.antbook.org/display/antbook/Installing+Java+6+on+Ubuntu+7.04](http://www.antbook.org/display/antbook/Installing+Java+6+on+Ubuntu+7.04)

---

### Post by noneedforwindows on 2007-08-05
hmmm frostwire works now?? Tried to reinstall limewire still wont open??

---

### Post by markoid8 on 2007-12-14
The easiest way is to just install java 6 which has compiz support!!!!!!!!!!!!!!

open terminal and type:


sudo apt-get install sun-java6-jdk #sun-java6-plugin

type your password. 

Everything will be fixed with no issues


:)

---

### Post by rainwalker on 2007-12-14
Go to [www.frostwire.com](www.frostwire.com), and install FrostWire instead. It's all packaged for Ubuntu and everything, and the latest version fixes that white window bug that LimeWire has.

---


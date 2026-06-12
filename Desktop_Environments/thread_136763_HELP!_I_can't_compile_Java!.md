---
title: "HELP! I can't compile Java!"
date: 2006-02-26
forum: Desktop Environments
---

### Post by Kyle Kroll on 2006-02-26
Whenever I try to compile anythign with javac i get bash: javac is not recoginzed. Here's my compile code:
```
Desktop/jdk1.5.0_06/bin/javac
(cd BotClasses;
javac -cp .:./../BotClasses:./../OUTPUT:./../OUTPUT/unrenamed.jar ./../OUTPUT/sign/*.java ./../OUTPUT/*.java *.java)
``` the first line is me getting very ******* frustrated and trying to get it to work. in a file called Compile.sh.

---

### Post by hw-tph on 2006-02-26
First off, install Java the Debian way. That will most likely help a bit. apt-get install java-package and use it (make-jpkg) on the downloaded .bin file to create a .deb you can install.


Håkan

---


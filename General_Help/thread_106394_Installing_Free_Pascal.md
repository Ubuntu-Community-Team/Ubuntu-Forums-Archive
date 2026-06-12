---
title: "Installing Free Pascal"
date: 2005-12-20
forum: General Help
---

### Post by ubuntuubuntu on 2005-12-20
I downloaded the file fpc-2.0.2.i386-linux.tar from freepascal.org and ran the installation. When I type fpc (name of a source file) on a terminal, I get the message "bash: fpc: command not found". What should I do in order to compile Pascal source codes with fpc?

---

### Post by schilcha on 2005-12-20
I've never installed freepascal, but it seems as if fpc is not in your path. If you happen to be in the directory where fpc is located, . (the current dir) is probably not in your path. Try prepending the full path to fpc when starting it, or (if you're in fpc's dir) starting it as ./fpc...

Good Luck!

---

### Post by ubuntuubuntu on 2005-12-27
[QUOTE=schilcha]I've never installed freepascal, but it seems as if fpc is not in your path. If you happen to be in the directory where fpc is located, . (the current dir) is probably not in your path. Try prepending the full path to fpc when starting it, or (if you're in fpc's dir) starting it as ./fpc...

Good Luck![/QUOTE]

It works. But I've seen in other computers that it's possible to compile only by "fpc name_of_the_file", without going to fpc's folder. Also, when I use g++ (a c++ compiler) I can compile by typing "g++ name_of_the_file"? How can I make it possible to compile only by typing "fpc name_of_the_file"?

---

### Post by fordfan753 on 2005-12-27
If you copy the freepascal directory to /usr/local/lib/ and the fpc file to /usr/local/bin/ you should be able to start it with just fpc...

---

### Post by fordfan753 on 2005-12-27
Oh, first....you said you ran the installation? was it a self installing binary? or just something you compiled? If it was a self installer did you run it as root? If it was just something you compiled did you remember to do a sudo make install ?

---


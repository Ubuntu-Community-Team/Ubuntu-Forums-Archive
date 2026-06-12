---
title: "trouble with the make clean command"
date: 2005-12-25
forum: General Help
---

### Post by tuvok302 on 2005-12-25
whenever i try to use the make command it says something along the lines of "make command not a real command" (you know the error where it tells you it isnt there). it also says the same thing with make 536

any help would be appreciated.

---

### Post by stuporglue on 2005-12-25
1) Have you installed build-essential? It includes make, gcc and other developer goodies. If you haven't, install it and it should work. 

2) If you have installed it, what's the output of just "make"? 

3) If just "make" gives the same error, what's your $PATH variable set to? Running "echo $PATH" should print out a line or two with that info.

---

### Post by tuvok302 on 2005-12-25
how would i go about installing build-essential? 
sudo apt-get install build-essential?

---


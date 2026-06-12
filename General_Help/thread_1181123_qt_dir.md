---
title: "qt dir"
date: 2009-06-07
forum: General Help
---

### Post by thedoctor81877 on 2009-06-07
I am trying to install mux2d & when i type ./configure into the terminal, I get the following back:

loading cache ./config.cache
checking searching for Qt...... qt dir doesn't exists!
exit: 1: Illegal number: -1

I tried sudo-apt get install qt, but then I got: cannot find qt.

Help???

---

### Post by SeanTater on 2009-06-07
Chances are, this is what you need to build:

sudo apt-get install libqt4-dev

---

### Post by SeanTater on 2009-06-07
Also, as a general rule, you may want to try this

```
sudo apt-get build-dep SOME_PROGRAM
```

Where SOME_PROGRAM is the most similar program already available (maybe even another version of the same program)  -- That program should get a lot of libraries you need before you build

---

### Post by thedoctor81877 on 2009-06-07
I installed said program, but when I did ./configure again, I got the same exact error message: qt dir doesn't exist.

-Michael

---

### Post by SeanTater on 2009-06-07
Looks like it's a QT3 program then.

Here's the code for qt3 (instead of qt4)

```
sudo apt-get install libqt3-headers
```

---

### Post by thedoctor81877 on 2009-06-07
I am still getting the same error message. BTW, thanks for all your help.

---


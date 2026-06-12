---
title: "This browser does not have a Java Plug-in."
date: 2009-02-25
forum: General Help
---

### Post by Sarbazeirani on 2009-02-25
Hi, when i try to play the game on this website [http://www.dr-mikes-math-games-for-kids.com/online-traffic-jam-game.html](http://www.dr-mikes-math-games-for-kids.com/online-traffic-jam-game.html) the flash game doesn't load and the following message is displayed: 

This browser does not have a Java Plug-in.
Get the latest Java Plug-in here

when i type into the terminal: 
ameer@a1525:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)

what am i missing? i've tried downloading Java Plug-in Download Page for Linux from the Sun microsystems website, i'm not sure if i've installed it correctly

**this being my first post in any type of online forum, i apologize if i've linked to other websites. I'm learning the rules as we go. thanks!

---

### Post by taurus on 2009-02-25
Install the ubuntu-restricted-extras either from add/remove, synaptic, or apt-get.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Don't forget to restart firefox.

---

### Post by Sarbazeirani on 2009-02-25
thank you! i'm downloading it now .

---

### Post by taurus on 2009-02-25
If you happen to get to a java license screen, press the Tab key to highlight the <OK> and Return to accept it.

---

### Post by Sarbazeirani on 2009-02-26
ok got it! how do i mark it as solved? and how do i get 75 points to write on people's profiles?

---

### Post by mikene on 2010-12-22
it didn't work for me. any ideas ?

also, download links are dead for linux on oracle's [website]("http://www.oracle.com/technetwork/java/index-141825.html").

---


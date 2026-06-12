---
title: "Puzzle Pirates"
date: 2005-10-04
forum: Gaming &amp; Leisure
---

### Post by edm00se on 2005-10-04
Here's the skinny:
1- I love Ubuntu, not using it is not an option
2- I love pirates
3- I love puzzles
4- Therefore, I love this game called ["Puzzle Pirates"]("http://www.puzzlepirates.com") (can download and play for free, if use non-pay "oceans"/servers)
6- I had no trouble playing Puzzle Pirates in Warty, save for sound
7- My sound works flawlessy now, under Hoary, however playing the game gets funky, i.e.- it crashes randomly, usually when under a heightened processor load (which shoots up when I play the game)
To my knowledge, the game is entirely in java and should be flawless, theoretically. I am at school, and we have a T1 line or two, and have never experienced speed problems with the internet.
Somebody help, my beloved Puzzle Pirates is unplayable until it works again!

---

### Post by MrMrs on 2006-11-04
i need help, I have installed puzzle pirates. But the problem is i cant run it. if you no why i cant run it please tell me.

---

### Post by livingtarget on 2006-11-04
You most likely need the java runtime. I.e.: the sun-java5-bin package

You can install it with this:
> sudo apt-get install sun-java5-bin

It's in the multiverse repositories, to enable multiverse go to: System -> Administration -> Software Sources and select "Software restricted by copyright or legal issues"

Restart the browser and/or launch puzzle pirates.

---

### Post by mediax on 2006-11-06
I've just tried it and it runs perfectly in Edgy.  Fun game too! :D

---

### Post by K.Mandla on 2006-11-06
Hmm. Iceweasel wants Gnash, which suggests it's a Flash game, in which case maybe the Flash beta is an idea. I'm not sure of that though.

---

### Post by BRFC on 2008-08-30
I'm trying to install Puzzle Pirates, I get this far then get stuck anyone any ideas?


Do you agree to the above license terms? [yes or no] 
yes

Which Java Virtual Machine would you like to use?
Note: the JVM must be version 1.4.1 or newer.
[]

---

### Post by Perfect Storm on 2008-08-30
Well, firstly did you installed Sun Java?

---

### Post by BRFC on 2008-08-30
Okay, I have Java Console 6.0.00.6.0 installed through Firefox from the Mozilla website. Any help welcome.

---

### Post by Perfect Storm on 2008-08-31
Install sun Java 1.6 or 1.5 - [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by doorknob60 on 2008-09-01
No need for medibuntu, run this:
```
sudo aptitude install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```

---


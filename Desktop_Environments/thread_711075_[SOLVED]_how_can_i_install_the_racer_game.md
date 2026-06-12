---
title: "[SOLVED] how can i install the racer game ?"
date: 2008-02-29
forum: Desktop Environments
---

### Post by tropcky on 2008-02-29
is any one know how to install the racer game ? 
helo plez ?

---

### Post by jan quark on 2008-02-29
is it in synaptic?

if not, can you pleae post a link to the website of this game?

---

### Post by r4ik on 2008-02-29
It is in Synaptic.

More games here,

[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

Good luck !

---

### Post by tropcky on 2008-02-29
I cant   faind it in Synaptic

---

### Post by kellemes on 2008-02-29
You mean [torcs]("http://torcs.sourceforge.net/")? Pretty cool game.

Just do from terminal..
```

sudo apt-get install torcs

```

---

### Post by tropcky on 2008-02-29
i mean the game with real cars u know 
like need for speed

---

### Post by kellemes on 2008-02-29
You mean [Racer]("http://www.racer.nl/")?

---

### Post by tropcky on 2008-02-29
Ya Thats What I Mean   Now How Can I Install It

---

### Post by kellemes on 2008-02-29
Visit the download page [http://www.racer.nl/]("http://www.racer.nl/"), choose the beta-version and you'll see the instructions..

---

### Post by tropcky on 2008-02-29
Man I Am New To Linux And Dont Know How To Do That  Or I Dont Understand   So If U Can Help Me   The File Is In My Home   Now How To Make It Work

---

### Post by tropcky on 2008-02-29
eny help 
 plez guys i am dieing for thes game

---

### Post by tropcky on 2008-03-01
ppl plez any help

---

### Post by tropcky on 2008-03-01
come on guys i am sure that ther is some body know how    plea help guys

---

### Post by trappleye on 2008-03-03
Here's what you need to do
    * Download the Linux Racer beta tgz file from the racer website.
    * Make sure it is in your ~/ (home) directory
    * run 'tar xzvf racer054b1.tgz' from your home directory (first run 'cd ~'). this will unpack it into the ~/racer directory
    * If you want sound then you need to Install fmod. go to the fmod site [http://www.fmod.org/index.php/download](http://www.fmod.org/index.php/download), get the version you need, unpack it, and then cd to the directory it is unpacked and run 'sudo make install' and that will install it
    * cd ~/racer
    * ./racer (if it doesn't want to start, try 'chmod +x racer' first)

I hope that works for you.

---


---
title: "Help Wanted - Creating a Strategy/Board Game for Linux"
date: 2008-02-09
forum: Gaming &amp; Leisure
---

### Post by Cheiron on 2008-02-09
Hello everyone,

We're creating a strategy/board game that is something like Risk, but not an exact copy. The game has a random map generator to keep things interesting, and is made for Linux (with a Windows port, too). We're looking for anyone interested in helping out with the project. Called OpenFracas, it is based on a discontinued computer game for windows called Fracas.

We have already made good progress on the game and have several releases of it so far, but we still have a lot of ground to cover. 
You can take a look for yourself at [http://www.openfracas.org]("http://www.openfracas.org")

OpenFracas has reached a point where we feel that the project would greatly benefit from the added contribution of others. We're looking for anyone interested in helping out; we have a long list of things that we want to accomplish with the game that cover a variety of topics and skills.

OpenFracas is written with Ruby/GTK, and we have a variety of tasks that we need to address, including adding new features, creating sounds and music for the game, building packages for various linux distros (already have an ubuntu package), creating an osx port, bug testing, and more.

Specifically for adding new features, we're looking to add 
[LIST]
[*]network (LAN) play - we have an idea of how to do this, and have designed the game in a way that should make this fairly painless. If someone is really ambitious, we were considering using something like Avahi for automatic discovery of a local server.
[*]sounds and music - we have *some* of the sounds effects created already, but we have no nice way to play them cross-platform. Presumably this would need a very small interface to the rest of the code, and would be treated as a black box.
[*]map editor - We've made some preliminary progress on this, but many of the features are still missing.
[/LIST]

There are also other things that can be done if anyone feels like diving deeper into our code. 

We also need things like sound effects and music for the game. We can provide samples of sound effects that we've created. For the music, we're open to anything that sounds like a good fit, but perhaps music from games like Risk II or Warcraft would be a reasonable template

We will always welcome help from anyone who feels that they can contribute to the project in some other way that has not been covered. If you have any questions, please comment; you can also contact us through our forums at [http://forums.openfracas.org]("http://forums.openfracas.org")


[SIZE="1"]*Mods, I'm not sure if this is the right place for this post, so I appologise if it is in the wrong spot.*[/SIZE]

---

### Post by jorgerosa on 2008-02-09
Looks really kool, **Cheiron**. Remembers me the great old classic "**North and South**" ([video]("http://www.youtube.com/watch?v=CHcoemBuUZ0")) in Commodore Amiga.
Is it similar? Anyway, i´ll be around, maybe i could help somehow.

---

### Post by Vadi on 2008-02-09
Ooh, I'll go get it.

---

### Post by Vadi on 2008-02-09
Instructions kinda broke my sources.list:

> vadi@ubuntu:~/bin$ echo 'deb [http://ubuntu.openfracas.org](http://ubuntu.openfracas.org) gutsy' | sudo tee -a /etc/apt/sources.list
deb [http://ubuntu.openfracas.org](http://ubuntu.openfracas.org) gutsy
vadi@ubuntu:~/bin$ sudo apt-get update
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
vadi@ubuntu:~/bin$ 

---

### Post by Vadi on 2008-02-09
Graphical instructions didn't work either. I'll go with the .deb :)

---

### Post by Cheiron on 2008-02-09
Vadi, thanks for pointing that out; sorry for messing up your sources.list file. I think I've found the problem.

the line the instructions said to add was

```
deb http://ubuntu.openfracas.org gutsy
```

when it should have been

```
deb http://ubuntu.openfracas.org gutsy/
```

including a trailing slash. Hopefully it works for you now.

---

### Post by Cheiron on 2008-02-10
Hello Jorgerosa,

I've not played that game, but it looks somewhat similar (it looks to be the same type of game, at least)

We'd love any help you can offer; are there any areas that overlap your own strengths, or that you would feel most comfortable with?

---


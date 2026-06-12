---
title: "best 2D game engine."
date: 2013-05-28
forum: Gaming &amp; Leisure
---

### Post by Timmix on 2013-05-28
hello all, i would like to program a game that can export to all os's but i would like to run the engine in ubuntu. What is the best recomendation? thanks all.

---

### Post by Arthur_D on 2013-05-28
[http://freegamedev.net/wiki/Free%2C_cross-platform_game_engines](http://freegamedev.net/wiki/Free%2C_cross-platform_game_engines)
Best? Hard to say. pygame might be one of the "easier" ones, at least it you are familiar with Python.

---

### Post by King Dude on 2013-05-28
Allegro.
[http://sourceforge.net/projects/alleg/](http://sourceforge.net/projects/alleg/)

It's primary programming language is C, and can use Ada, C++, C#, D, Lisp, Lua, Mercury, Pascal, Perl, Python, and Scheme bindings.

---

### Post by Mikeb85 on 2013-05-29
> **Timmix said:**
> hello all, i would like to program a game that can export to all os's but i would like to run the engine in ubuntu. What is the best recomendation? thanks all.

Javascript (or Coffee-Script) and HTML5 Canvas.  You can run it in any modern browser, and assuming your target audience has a somewhat modern computer (and updated browser), it will run without installing anything.

---

### Post by King Dude on 2013-05-29
> **Mikeb85 said:**
> Javascript (or Coffee-Script) and HTML5 Canvas.  You can run it in any modern browser, and assuming your target audience has a somewhat modern computer (and updated browser), it will run without installing anything.
Javascript sucks up CPU like nobodies business.

Depending on what the OP wants to do, if he would like to make an online game then perhaps the language Dart will be of an interest to him, since Dart is designed to replace Javascript. If the OP would like a game that runs on the computer, Allegro is the best solution I can see.

[http://www.dartlang.org/](http://www.dartlang.org/)

---

### Post by Mikeb85 on 2013-05-29
> **King Dude said:**
> Javascript sucks up CPU like nobodies business.


It does, but it's cross platform, has WebGL, and is easy to get started with.  You can use libraries like this: [http://voxeljs.com/](http://voxeljs.com/)  to make Minecraft-like worlds in only a few lines...  Or you can create games like:  [http://www.chromeexperiments.com/webgl/](http://www.chromeexperiments.com/webgl/)

Ludum Dare is an interesting place to see 2d game frameworks in action:  [http://www.ludumdare.com/compo/](http://www.ludumdare.com/compo/)

Here's a few of my favourites from the most recent competition:  [http://www.deconstructeam.com/games/gods-will-be-watching/](http://www.deconstructeam.com/games/gods-will-be-watching/)  and [http://blue-brick.com/LD26/be/the/wind/#](http://blue-brick.com/LD26/be/the/wind/#)

Dart is a funny recommendation BTW, since it simply compiles to Javascript at the moment - no browser ships with the Dart VM (except a certain developer version of Chromium).

---

### Post by King Dude on 2013-05-29
I recommended Dart with the future in mind. Even though it's not used today, a year or two down the road it may become more popular.

---


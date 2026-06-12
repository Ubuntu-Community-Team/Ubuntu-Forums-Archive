---
title: "First Game Project?"
date: 2011-09-27
forum: Gaming &amp; Leisure
---

### Post by Carpentr on 2011-09-27
I've recently started taking computer courses in college and I'm being taught some C++ this semester. I've made a few console applications which are mostly used to solve business problems such as net pay, taxes, revenue, et cetera. Simple stuff so far.

Does anyone have any ideas for on where I could start if I was interested in creating a simple game in C++? When I say simple I'm talking along the lines of pong. I'd prefer to make a 2D graphical one, although I'm not sure how feasible that would be. I've read about SDL but I'm not sure how beginner friendly that is. 

Any suggestions would be welcome.

---

### Post by nickleboyblue on 2011-09-27
If I were you, I would get to writing something like Sudoku for a console first.  If you can get the computer to solve a Sudoky puzzle on it's own, you'll probably be about half way to where you would need to be to write something like Pong.  SDL is a great library if you can figure out how to use it, but ANYTHING graphical requires a lot of time and effort to figure out.

Other game suggestions: Asteroids, Skeet, lunar lander.  Look up all the old classics.  They are very useful for learning the ropes.

Just so you know, game writing is a bit above beginning C++.  Object-Oriented programming is the way to go, so until you get past the procedural stuff, I would suggest you focus completely on console games.

---

### Post by Sofox on 2011-09-27
SDL is relatively beginner friendly. If you're learning C++, you're already dealing with more complexity then what most people are used to so SDL won't be much of a problem on top of that.

Couple of things to watch out for:

There's no easy way to quickly draw solid primitives, circles, sqares etc. (Direct access to screen pixels and easy drawing of sprites and images mean that this shouldn't be a problem)

No easy way to rotate sprites, that'll require learning a bit of OpenGL.

SDL will require a bit of work on your behalf if you want your game to support multiple resolutions (as opposed to OpenGL where you can set things to strech and scale with the window)

Overall, I think SDL is the right choice for you right now. Over time, I think you may want to move onto OpenGL (which of course can be used for 2D), but for now SDL seems the right option, it's straighforward and will handle your needs.

EDIT: Completely forgot about [SFML]("https://duckduckgo.com/k/?u=http%3A%2F%2Fsfml-dev.org%2F") which you could use instead of SDL. It's newer, seems promising, but I haven't used it enough to compare with SDL so I can't say whether it's better.

---

### Post by thatguruguy on 2011-09-27
You may want to take a look at [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php) for tutorials on game creation in C++ and SDL.

---

### Post by BeRoot ReBoot on 2011-09-27
If you're only familiar with writing text-based applications, you may want to start with ncurses, as opposed to SDL. For a simple exercise, try writing a terminal-based minesweeper clone, nothing complicated, just initialise an array of cells, randomly seed mines onto them, use arrow keys for moving around the field, space to open a cell, another key to flag it.

---

### Post by kostkon on 2011-09-27
Check the [*Allegro*]("http://alleg.sourceforge.net/") game lib (there are various allegro packages in the repos).

---

### Post by Carpentr on 2011-09-27
Thanks for the suggestions guys. I'll have to try SDL in a couple months when I'm a little more skilled in programming. Maybe I'll play tinker with it for now.

Besides Sudoku and Minesweeper does anyone have any other ideas for console games I could make? Perhaps I should make a few console games before I attempt even a simple graphical game, then.

---

### Post by BeRoot ReBoot on 2011-09-27
Tetris
Go
Card games (solitaire)

---

### Post by thatguruguy on 2011-09-27
I recently made a "video poker" game in Python. Something like that may be fun.

---

### Post by Sofox on 2011-09-28
> **Carpentr said:**
> Thanks for the suggestions guys. I'll have to try SDL in a couple months when I'm a little more skilled in programming. Maybe I'll play tinker with it for now.

Take my advice from a programmer of a few years: Never assume that programming skill works like a RPG levelling system where you can only use a certain "skill" when you have enough "experience". In real life, you can pretty much attempt anything from the get go no matter what your level of experience is. In fact it's usually a good idea that you do that because not only do you learn something in the process, but you also learn early on which areas you need to focus on to improve.
The truth is, that doing a game in your spare time could complement your education. You try and experiment in your spare time, and you can ask your college lecturer questions that arise from your work. Sometimes you may spend time working on a game subsystem only to learn of a much better way of doing it, but that's going to happen constantly throughout your entire programming career so there's no point getting worried about it.

Other game ideas:
Lights Out (popular, look it up if you don't know what it is)
Connect 4
Snake (timing based)
Go
Tic tac toe (straightforward)
Multigenre 3d FPS/Driving MMORPG with realistic economy system and comprehensive skilltree (hmmmm, might want to leave that one for a bit)

---

### Post by LinuxGamer on 2011-09-28
One of my first games years a go was 21 Match Sticks... I see several out there now for mobile. Seems like it would be good practice to start...[21 Matches]("http://www.softdensity.com/technology/mobile-application/21-matches/")

---

### Post by JDShu on 2011-09-28
My first game was tetris.

---

### Post by DangerOnTheRanger on 2011-09-28
My first game was/is [this]("http://openblox.sourceforge.net"). And I'm still working hard on it.

---

### Post by Carpentr on 2011-09-29
21 Match Sticks seems like a good one for me to begin with and then move on to others.

Admittedly I have spent many nights tinkering with game engines such as LOVE which use LUA. After I program a few console games maybe I could choose one and create a graphical version of it using SDL or something of the sort.

[QUOTE=DangerOnTheRanger 	
]My first game was/is this. And I'm still working hard on it. [/QUOTE]

Wow, nice. What did you use to make the 3D models?

---

### Post by ferrarirs on 2011-09-29
I had done sudoku for the first time in my application.I really like it

---

### Post by DangerOnTheRanger on 2011-09-29
> **Carpentr said:**
> 
Wow, nice. What did you use to make the 3D models?

Actually, all those games are made with (for lack of a better analogy) a bunch of Lego bricks. I drag and drop them around to make the world I want. Very nice for people who aren't that good at 3D modeling, like me :) But to answer your original question, I used Blender to make the Lego brick model.

---

### Post by pieman711 on 2011-09-30
The first game I made evolved from a labyrinth type puzzle game I started from a tutorial while learning Qbasic. I then rewrote it in blitz basic and finally I used it to help me to learn C++ this summer. As soon as I've got the code to a point where I'm not embarrassed by it (I'm entirely self taught purely as a hobby) I'll upload it somewhere. 
Its quite a good first game because it has no AI so was quite simple and after the basic engine is finished it will be very expandable by making new mazes for it.

---

### Post by Carpentr on 2011-10-05
> **DangerOnTheRanger said:**
> Actually, all those games are made with (for lack of a better analogy) a bunch of Lego bricks. I drag and drop them around to make the world I want. Very nice for people who aren't that good at 3D modeling, like me :) But to answer your original question, I used Blender to make the Lego brick model.

Nice, that must of been fun to code! :)

Once this schoolwork relents perhaps I shall get started on something ... C++ exam tomorrow. A lot of studying to do tonight! ](*,)

EDIT:

I made a program a few days ago that does the calculations for ticket sales, ticket type sales, and total sales using input from a file and then outputting the results onto the console and into a .txt file. It was pretty fun to code. My biggest problem was arranging the columns and rows to be perfectly lined up using setw().

---

### Post by DangerOnTheRanger on 2011-10-06
> **Carpentr said:**
> Nice, that must of been fun to code! :)

Once this schoolwork relents perhaps I shall get started on something ... C++ exam tomorrow. A lot of studying to do tonight! ](*,)

EDIT:

I made a program a few days ago that does the calculations for ticket sales, ticket type sales, and total sales using input from a file and then outputting the results onto the console and into a .txt file. It was pretty fun to code. My biggest problem was arranging the columns and rows to be perfectly lined up using setw().

Actually, I'm still working on it, with a few other people. But yeah, it's fun to work on it :)

Also, to keep your interest in programming, I suggest making various small programs that you find useful from time to time. For example, I made an RSS reader in Python a short while ago that fetches all the feeds I want it to download, and alerts me to new articles via libnotify (i.e, those little black alert boxes). Making something like that is both fun and useful.

EDIT: Post #202 - 202 is a palindrome, won't happen again for 101 posts :)

---


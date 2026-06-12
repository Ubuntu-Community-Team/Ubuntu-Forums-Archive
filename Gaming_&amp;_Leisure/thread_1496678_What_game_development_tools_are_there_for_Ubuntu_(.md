---
title: "What game development tools are there for Ubuntu (and related distros)?"
date: 2010-05-29
forum: Gaming &amp; Leisure
---

### Post by Nick_Jinn on 2010-05-29
What are some of the ones available? How would you rate their ease of use on a scale of 1-10 (Higher is easier)? What knowledge is required to use them (languages, ect)? 

Link to any tutorials if you have them?

---

### Post by accLinux on 2010-05-29
> **Nick_Jinn said:**
> What are some of the ones available? How would you rate their ease of use on a scale of 1-10 (Higher is easier)? What knowledge is required to use them (languages, ect)? 

Link to any tutorials if you have them?

Well, there are different libraries (opengl, openal)

Engines: Cube2, idtech 1,2,3 spring

/Programming /Scipting /Whatever  C C++ Python Lua etc.

Graphics: GIMP Blender etc.

Not quite sure what you want. Are you making a scolling space shooter? FPS? RTS? ????

---

### Post by Nick_Jinn on 2010-05-29
How about a first person shooter with dialogue and elements of an RPG game with live action combat?

A homebrew fallout 3?

Morrowind quality would be acceptable.




I dont have a lot of coding skills but I am going to learn Python this year.

---

### Post by accLinux on 2010-05-29
Are you going to use an existing engine or are you planning to create your own? Most First Person Shooters are coded in C/C++ for speed.

---

### Post by del_diablo on 2010-05-29
Remember: Using an existing engine WILL save you time, because reinventing the wheel is stupid without a groundbreaking idea in the correct place.

---

### Post by Nick_Jinn on 2010-05-29
Considering that I am not a programmer, I want as much of the work done for me as possible.

I think learning one language is enough for now, unless there is good reason to choose C++ for a first language.

---

### Post by Sockerdrickan on 2010-05-30
Use new stuff! :D

[LIST]
[*]C++0x
[*]SDL 1.3
[*]OpenGL 3.3/4.0
[/LIST]
 My favorite combination!

---

### Post by teh_drizzle on 2010-05-30
Try taking a look at PyGame ([http://www.pygame.org/news.html](http://www.pygame.org/news.html)).

There are tons of example games on the site, and the learning curve is not much steeper than python. :)

---

### Post by Simian Man on 2010-05-30
> **Nick_Jinn said:**
> How about a first person shooter with dialogue and elements of an RPG game with live action combat?

A homebrew fallout 3?

Morrowind quality would be acceptable.




I dont have a lot of coding skills but I am going to learn Python this year.

I think you're setting your sights *way* too high for a beginner, but there's no way for you to find that out without trying :).

Given that you are learning Python and want a 3D game, I'd suggest Panda3D which is a professional quality game engine for use with Python.  I've never used it, but it's been used for professional games before and supports Linux.

And if anyone tells you that you need C++ for speed, you should probably discount anything else they have to say.

---

### Post by Nick_Jinn on 2010-05-30
Thank you for all the useful advice.


Is Python a good beginning language? I want something useful with a shallow learning curve for my first language. I want to be able to write applets and other stuff.

I was also considering pearl and basic.

---

### Post by accLinux on 2010-05-30
> **Simian Man said:**
> I think you're setting your sights *way* too high for a beginner, but there's no way for you to find that out without trying :).

Given that you are learning Python and want a 3D game, I'd suggest Panda3D which is a professional quality game engine for use with Python.  I've never used it, but it's been used for professional games before and supports Linux.

And if anyone tells you that you need C++ for speed, you should probably discount anything else they have to say.

Tell me, then why are all commercial first person shooters coded in C or C++ ?????????????????????????

---

### Post by KiraLexi on 2010-05-30
accLinux: A lot of reasons. For one thing, a lot of them use derivatives of the Quake engines, which were written in C and largely predated object-oriented languages with fast JIT compilers and rich libraries. C/C++ are also good for writing cross-platform code.

---

### Post by Letrazzrot on 2010-05-30
> **accLinux said:**
> Tell me, then why are all commercial first person shooters coded in C or C++ ?????????????????????????

In commercial games, you may also find parts coded in Lua, Python, C#, Java, Ruby, etc.  Especially in the tool chain, AI, and Logic portions of the game code.

The key word here, though, is *commercial.*  Unless you are a AAA game studio, with bagillions of dollars to pay programmers to sort out the issues of maintaining, updating, and porting legacy code, and trying to low-level optimize the rendering of zillions of dollars of art assets on hardware with tight constraints (consoles), the question is meaningless.

To the OP:  I think Python would be a fine beginner language, especially considering all of the great tutorials/docs you can find on-line.  I would discourage BASIC, not because of speed, but because it becomes difficult to maintain when the code gets too large, and it lacks some of the niceties of modern languages.

---

### Post by accLinux on 2010-05-31
C is still a lower level programming language (higher then assembly and binary of course, but few people use binary or assembly for game programming, because that would be far too complex) making C fairly fast (faster then Basic, etc)

---

### Post by del_diablo on 2010-06-01
C and C++ = Speed, but it takes skill and time, and its hard to use
Scripting language: What is used for interal game logic and more, i think it was invented/used because doing that in C or C++ would be a too large mess

---


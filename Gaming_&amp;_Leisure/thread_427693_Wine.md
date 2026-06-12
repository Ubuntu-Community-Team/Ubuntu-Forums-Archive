---
title: "Wine"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by MartenH on 2007-04-29
How much juice does it take to run games through wine? What I mean is, if you take the criterias for running a game on a PC, how much should you add to those to be able to play it through wine? A rough estimate would be ok :)

---

### Post by disturbedite on 2007-04-29
this is a moot point/question.  it is completely random.  wine emulates some parts of windows and not others, so it is going to be completely different from game to game.

use the wine appdb to check for game/app compatibility.

---

### Post by lakersforce on 2007-04-30
A rough estimate would be that games under wine runs at about 3/4 speed of windows. But like the above post says, it is different from game to game.

---

### Post by noerrorsfound on 2007-04-30
> **lakersforce said:**
> A rough estimate would be that games under wine runs at about 3/4 speed of windows. But like the above post says, it is different from game to game.
Call of Duty (the first, not second) is said to work better in Wine than on Windows. I'm assuming they mean it's faster but I don't know because I haven't tried it yet.

---

### Post by DoktorSeven on 2007-04-30
Ideally, the game would run as fast (or a bit faster) than Windows.  But as someone else said, you have to take into consideration Wine's limitations, so you might get significantly slower.

---

### Post by disturbedite on 2007-04-30
there is the rare case that a game runs faster with wine, but there are some...

---

### Post by reiki on 2007-04-30
> **lakersforce said:**
> A rough estimate would be that games under wine runs at about 3/4 speed of windows. But like the above post says, it is different from game to game.

And also, apparently, from computer to computer. If you use frames per second (objectively) and play experience (as a subjective test), then I have to say my machine plays World of Warcraft better in Ubuntu using wine that it does on the exact same machine running World of Warcraft in Windows XP. 

I do absolutely agree that there seem to be a number of factors that determine whether a game will simply PLAY or whether it will PLAY WELL.

---

### Post by YokoZar on 2007-05-01
From the (under construction) new FAQ for Wine:

**Is Wine slower than just using Windows?**

Actually, Wine is sometimes faster. The speed of an application depends on a lot of factors: the available hardware and their drivers, the quality of the code in the APIs the application uses, the quality of the code in the underlying operating system, and the quality of the application code itself.

Driver code matters a lot. If you're running a graphics-heavy application using a video card with very poor drivers such as an ATI card under Linux, performance will degrade substantially. On the other hand, Linux has superior memory management, and comes out ahead of Windows in many CPU-related tasks; see [benchmarks] for more information.

Sometimes, bugs in Wine can make applications excessively slow; see Performance-related bugs.

---


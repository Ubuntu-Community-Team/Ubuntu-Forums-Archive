---
title: "XP faster than Ubuntu for games on same hardware"
date: 2009-01-15
forum: Gaming &amp; Leisure
---

### Post by cybergrunt on 2009-01-15
Why do the same games run slower in Ubuntu than they do in Windows XP on the same hardware (Latitude D620)? Take Warzone 2100 as an example. Even with Compiz and every necessary service disabled the game runs like a complete dog even if I window it into a resolution so small I can hardly make out what I am moving yet in XP I can play it in fullscreen mode, full graphics enabled and 8 players hammering me at the same time with very little slow down? 

Now I know it's not a game machine and I admit it's mostly used for coding and word processing but sometimes I just need to play something else other than Blackjack to distract me. Can anyone shed some light on this because I am truly baffled. Everything else I do on Ubuntu runs twice as fast as XP: or faster! Is there some secret 1337 trick I am missing here?

Thanks

---

### Post by Bucky Ball on 2009-01-15
Using Wine? Is it all games? If it is a low-spec machine wine may be the culprit. You use your games on top of windoze when in windoze, on top of Ubuntu *and* wine when in Ubuntu. More resources devoured.

---

### Post by jacksaff on 2009-01-15
You do understand, don't you, that linux is an entirely different operating system from windows and that programs for windows will NOT run on linux? Wine is an open-source implementation of some (most) of the functions that windows uses so that windows programs can run, but as windows is closed source, wine has had to be reverse-engineered and it's only through a minor miracle (and a lot of people's hard work) that it works at all.
Saying a windows program works better in windows than on linux is like complaining that your ferrari doesn't run while your truck goes great on the very same diesel.

---

### Post by Bucky Ball on 2009-01-15
Like what jackstaff said. 

Wine is known to slow the machine (and occasionally the operator!).

---

### Post by cybergrunt on 2009-01-15
Um, who said anything about wine guys? I am talking about games which are released on both *nix and Windows platforms. And jacksaff, I do understand but that is not what I am asking (perhaps you'd care to actually read my post before belittling me..?)

---

### Post by getaceres on 2009-01-15
It may be due to the drivers. What's your graphic card? Anyway, the graphics system is the weakest point in a Linux system. I think that Xorg is a beast that must be replaced with some other lighter graphic stack but I don't think that this will happen in the near future.

---

### Post by HavocXphere on 2009-01-15
Don't know, but a couple of guesses:
[LIST]
[*]Game code was optimised for MS systems
[*]Devs know all the tricks in the book for getting speed on MS platform
[*]*Nix graphics drivers are miles behind MS drivers :(
[*]Game market backs MS, hence optimization takes place there
[*]Wider range of gfx drivers on nix systems
[*]MS DirectX dominance
[/LIST]

I seem to recall that the unreal torunament 04 gap between nix and MS wasn't that big.

---

### Post by Bucky Ball on 2009-01-15
> **cybergrunt said:**
> Um, who said anything about wine guys?

Apologies, my mistake.

---

### Post by Naegling23 on 2009-01-15
It depends on the game really.  If I remember correctly, Doom3 runs better on linux than windows.  

You also need to check the settings, sometimes things like water or lighting effects cause problems in linux, and disabling them bumps your frame rates back up.  I'll also second checking the drivers for your video card.  And, I know this is silly, but your comparing XP 32bit with ubuntu 32 bit right?  

As for wine, usually there is some small loss in performance with the games that run, but it only really is noticable for those that are near the edge as far as system specs go.  

One last thing, if your having problems with the performance of a specific game, check this forum, and the google.  Often time there may be a tweak or a tip to maximize performance.

---

### Post by iheartubuntu on 2009-01-15
Whats your system anyways? I notice this if I run Future Pinball on an older P4 laptop, but thats running through wine. My sister bought a serval performance from System76 just so she can play World of Warcraft on Ubuntu... it kicks butt.Its a top of the line system no doubt and its just awesome on it. If you got a good enough system & video card whatever differences there might be arent going to be too noticeable.

---

### Post by Iendicis on 2009-01-15
It depends on too many factors to be able to nail down one good answer here. I run in to the same thing as well, sometimes. It depends on the game, OS settings, and computer.

OpenArena and Nexuiz run amazingly compared to Windows XP, but Unreal Tournament 2004 (even on OpenGL mode) runs better in Windows. It really depends on so many variables that nobody can really tell.

---

### Post by Bölvaður on 2009-01-15
> **cybergrunt said:**
> Is there some secret 1337 trick I am missing here?

hmm.. yes... Computers are not simple objects. There are too many variants that interfere and can make games run faster or slower. On top of that games are made differently which some graphical card might be more optimized for. It is just way to complicated to say games in general.. you would need to point out exact version of some game, running exactly same hardware and drivers with same os and same packages. there are more things to think about but for simplicity, you can only change 1 of these and compare.. if you change more or have something like all fps games... or all intel cores... then it would be way too... wait.. I think I made my point clear already.

---

### Post by cybergrunt on 2009-01-15
It's a Dell Latitude D620 laptop. It's not that old but it's def not a games machine. However I did have XP on it before I moved to Ubuntu and I was running things like Neverwinter Nights, UT, Warzone 2100 and KOTOR2 on it without any slowness problems at all. Even the Chess game that comes Gnome games is a little bit slow on it under Ubuntu when really something like that should just run as it was meant to when that same laptop can run Neverwinter Nights under a different OS. I guess I just wanted to play some of the open source *nix games out there as a change of scenery.

---

### Post by 0bso on 2009-01-15
Which video card does that laptop have in it? If you're having a problem with all 3d apps it sounds like you probably have a driver problem.

---

### Post by cybergrunt on 2009-01-16
It's a Intel 945GM/GMS integrated. Nothing much at all really. I thought it might be a driver prob as well but the system doesn't have any problems with the driver and knows exactly what type of card it is.

---

### Post by Melcar on 2009-01-16
It's definitely drivers.  Open source drivers tend to be slower and usually lack full opengl2.1 support (which can slow down many modern games).

---

### Post by iheartubuntu on 2009-01-16
> **cybergrunt said:**
> It's a Dell Latitude D620 laptop. It's not that old but it's def not a games machine.

RAM is so inexpensive these days... If you can upgrade your laptop, say from 1GB to 2 GB or up to 4GB ram, Id do it if it was my machine. Then your games will be faster than when it was running XP. :) Its not the answer youre looking for, but it will definitely help. I notice computers Ive installed Ubuntu on.... less than 1GB seems to drag, over 1GB and it start kicking some butt.

If youre in USA... try [http://www.pricewatch.com](http://www.pricewatch.com) to find some RAM (good prices) that will work in your system.

---

### Post by FranMichaels on 2009-01-16
System -> Preferences -> Appearance

Click the Visual Effects tab, and select None.

Until we get the new linux kernel, new xorg and GEM (next Ubuntu), you won't get acceleration in games while effects are on that intel graphics... 

Hope that helps.

---

### Post by iheartubuntu on 2009-01-16
> **FranMichaels said:**
> System -> Preferences -> Appearance

Click the Visual Effects tab, and select None.

Until we get the new linux kernel, new xorg and GEM (next Ubuntu), you won't get acceleration in games while effects are on that intel graphics... 

Hope that helps.

When you say next Ubuntu, do you mean the next LTS or the next one which would be 9.04?

---

### Post by cybergrunt on 2009-01-17
Yeah, I have it set to none and have even uninstalled Compiz. Interestingly it handled Extra desktop effects with no problem at all. I've had computers which I considered more powerful than this not be able to handle anything higher than Normal. It's all very perplexing :)

---

### Post by cybergrunt on 2009-01-17
Ok I'll have a look around for some new drivers for it and see how I go. And you're right shirteesdotnet it's not the answer but useful nevertheless. I'll def get some more RAM for it - 1GB is pretty lame these days but that's what it shipped with at the time.

---

### Post by betrunkenaffe on 2009-01-31
Don't know if this is still an issue for you or if you resolved, I've found that some linux ports in the past were just using a bundled compatibility layer (Eve uses Cedega). I know I have had success by installing the windows counterpart through wine instead (specifically Eve, the linux port looks terrible, works terrible and is not user friendly. wine = perfect play with some fps loss)

---

### Post by RaiCoss on 2009-01-31
> **cybergrunt said:**
> Um, who said anything about wine guys? I am talking about games which are released on both *nix and Windows platforms. And jacksaff, I do understand but that is not what I am asking (perhaps you'd care to actually read my post before belittling me..?)

Maybe its your card? Pretty much every cross platform game/demo I've played runs as good as, or better than XP on Linux, I get great FPS under WINE for 99% of games, even with DirextX DRU. If you own ATi, you WILL get lower performance than Windows XP, because of the simple fact that ATi's drivers are well behind the curve of nVidia's.

---


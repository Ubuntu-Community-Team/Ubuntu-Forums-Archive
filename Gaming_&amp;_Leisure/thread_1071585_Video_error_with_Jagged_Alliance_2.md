---
title: "Video error with Jagged Alliance 2"
date: 2009-02-16
forum: Gaming &amp; Leisure
---

### Post by whydoesitburn on 2009-02-16
So I managed to installed Jagged Alliance 2 without any problems, but whenever I go to play the game, all I get is a black screen. When I ran the game under command-line it gave me the message "Video Error: Unable to init the display." I am running Ubuntu Hardy and my video card is a nVidia 8400 gs.

---

### Post by wiebeest on 2009-02-20
> **whydoesitburn said:**
> So I managed to installed Jagged Alliance 2 without any problems, but whenever I go to play the game, all I get is a black screen. When I ran the game under command-line it gave me the message "Video Error: Unable to init the display." I am running Ubuntu Hardy and my video card is a nVidia 8400 gs.

Used to work fine for me under Hardy. I do have JA2 GOLD version (the one that doesnt need a CD after installation). 

Works great still under Ibex, just tested it with newest version of Wine (version 1.1.15). I did install the unofficial 1.13 patch ( [http://ja2v113.pbwiki.com/]("http://ja2v113.pbwiki.com/") ), which is great stuffed with new features, such as 1024*768 resolution, much more weapons, tweaked characters, etc. But I used to play JA2 vanilla under Hardy and it worked. 

Maybe it's a Wine setting? Under graphics tab from configure Wine I only activated the first box. Maybe you coald try that? And what about WineHQ? Did you search for JA@ in their appsdatabase [http://appdb.winehq.org/]("http://appdb.winehq.org/")?

---

### Post by whydoesitburn on 2009-02-20
I'm actually using the distribution ported for Linux.

---

### Post by daddysmonsters on 2009-05-25
Same here but without any sort of error message. I also tried running it windowed with no luck. There is an sdl port of this floating about so I might have to go that route. Please let me know if you find a fix. Also I'll add that I installed it using term but also with loki installer both installed fine but game doesn't give video upon launch just a black window.

EDIT: Ok this may not help your issue but I found that the problem for me was that my monitor (32 inch hdtv) does not properly display 640x480 in Ubuntu. Not sure if it's a refresh rate the game is trying to set that is above 60hz or what. Ultimately I just ran it in Cedega and although it still does not work with fullscreen it ran fine windowed. I am determined to find out how to get it to run native in fullscreen however. But this may require using the sdl port or "staciellia" that's almost certainly wrong but it's another port to modern linux systems. Google would correct it if you want to search it out.

---

### Post by daddysmonsters on 2009-05-29
OK in Cedega this worked fine, I upgraded to the unofficial 1.13 patch that gives 800x600 and 1024x768 support and viola all better. Now I know you are running native and I'm going to try this here shortly as well, but im thinking you could simply use wine to install the patch and then take the contents of that and override the native version. This has a very slim chance of working if it involves windows binaries but if it's simply dat files config files etc it may very be succsessful. If all else fails I'm sure people coudl tell you how to link the old glibc and dated files that the native jagged ran on and get it to work in a modern distro. Sad thing is how many Linux fanboys will jump to say yeah look at the list of games we have when so many of them are incredibly difficult to get them to function on a modern linux distro. I don't recommend cedega it has bailed me out a few times but ultimately it can be as much of a pain and it's expensive for something that does what wine can do. I will say though, that the whole wine vs cedega thing is tired, wine does some things right cedega does others I also have crossover games (also nonfree) and between the three of them they might run a game. I don't consider any of them to be prime well polished apps by any means.

---


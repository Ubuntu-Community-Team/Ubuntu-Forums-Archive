---
title: "Simple Question about SDLmame"
date: 2009-10-25
forum: Gaming &amp; Leisure
---

### Post by ilpiero on 2009-10-25
Hi all I just installed SDL mame and wahcade frontend, the frontend works, but honestly, I don't like it much...
So the question is : when I start mame without command line argument a sort of GUI starts up with some option and a game list. 
The games in the list seem to be random, is there a way to browse all the roms from that list or I get only a bunch of random games to choose from?
And by the way where I can find documentation about SDLmame?

Thanks!

---

### Post by williamts99 on 2009-10-25
Wahcade is best for use in a cabinet, but works well out of the cab also.

Yes, just start typing the the name of the game that you want to play and it will go to that game.

[http://rbelmont.mameworld.info](http://rbelmont.mameworld.info)

Or in a terminal, type in:
man sdlmame

Best Regards,
Williamts99

---

### Post by ilpiero on 2009-10-25
that's just what i wanted to know, i feel a little stupid... ;) 
Thank you!

---

### Post by williamts99 on 2009-10-25
No problem, there was a time that I didn't know about 'man'.  A third option for man pages is to go to google, and use 'man sdlmame' if you want to view it from a web browser.

Also if you want to be kept up to date with the latest versions, you can check out 
[http://sdlmame.wallyweek.org/]("http://sdlmame.wallyweek.org/") for SDLmame debs and a repo
and of course you probably already know about
[http://www.anti-particle.com/wahcade.shtml]("http://www.anti-particle.com/wahcade.shtml") for Wahcade, but I will leave that here for others.

The only other thing that I might mention is if you have an issue with 100%cpu is an issue with sdlmame and pulseaudio, you just have to install libsdl1.2debian-pulseaudio
sudo apt-get install libsdl1.2debian-pulseaudio

Best Regards,
Williamts99

---


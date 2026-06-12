---
title: "FoFiX (Frets on Fire X aka Alarian-MFH Mod) -- does anyone have it working with 8.04?"
date: 2008-11-30
forum: Gaming &amp; Leisure
---

### Post by unknownmosquito on 2008-11-30
Hey all;
I'm trying to get the MFH-Alarian mod, now renamed Frets on Fire X working on my 8.04 system, but songs don't load. I can get to the selection screen, but upon selecting a song it bumps me back to the menu.

I was wondering if anyone else has this problem, or if anyone has it working. If you want to give it a try the project is on Google Code:

[http://code.google.com/p/fofix/](http://code.google.com/p/fofix/)

And I downloaded the Guitar Hero III songs from Geetar Freaks:
[http://www.geetarfreaks.webs.com/Viva%20La%20Music%20-%20GUITAR%20HERO%20III.html](http://www.geetarfreaks.webs.com/Viva%20La%20Music%20-%20GUITAR%20HERO%20III.html)

---

### Post by nautilus on 2009-01-19
Have you got this sorted?  I have it running on every system I own now without issues from the latest 3.030 version at [http://code.google.com/p/fofix/downloads/list?can=2&q=&sort=-uploaded](http://code.google.com/p/fofix/downloads/list?can=2&q=&sort=-uploaded)

--

Just to expand on that, it may have to do with the case sensitivity of the song data.  Have you verified that the required files (song.ogg, notes.mid, song.ini, and guitar.ogg) are all lower-case?  Once you have that verified, check in song.ini to make sure it references lower-cased files.

I know it's a chore, but we have those win32ers to blame.  Those heartless freaks make life miserable for us nixers.  ... just kiddin', heh.

---

### Post by frasmit on 2009-04-30
> **nautilus said:**
> Just to expand on that, it may have to do with the case sensitivity of the song data.  Have you verified that the required files (song.ogg, notes.mid, song.ini, and guitar.ogg) are all lower-case?


Thanks Nautilus!  that fix the prob for me in one go.

---


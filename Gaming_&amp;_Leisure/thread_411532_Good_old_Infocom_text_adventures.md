---
title: "Good old Infocom text adventures ?"
date: 2007-04-17
forum: Gaming &amp; Leisure
---

### Post by Browser_ice on 2007-04-17
For all of you guys who are probably as old as I am, you maybe the only ones remembering these text adventure games from Infocom. But any whereabouts of Linux versions ?

Zork-1, -2, -3
Infidel
Planetfall
Suspended
...

---

### Post by Matakoo on 2007-04-17
I guess I'm an old fart too then ;)

They work fine. As long as you have the datafiles from Windows/Amiga/Mac/whatever they can be made to run under Linux very easily. Well, the ones I've tried at least. Beyond Zork, Planetfall, Leather goddesses of Phobos, and Zork 2.

Download either xzip (for X) or frotz (console and ncurses based) from the standard repos, and you're ready to go. Just open up a console-session, change into the directory where you have the datafile is located (ends in .z5) and type

xzip name-of-game.z5 OR
frotz name-of-game.z5

And Bob's your uncle.

---

### Post by Browser_ice on 2007-04-19
I have nothing, none of these games. That's why I was askign if they are still around and hopefully, in Linux versions.

I miss Floyd the robot with the knowledge of an encyclopedia but the mind of a 5 yeasr old child, especialy when  by mistake I typed "get all"

some wiki links :
[Infocom]("http://en.wikipedia.org/wiki/Infocom")
[Planetfall]("http://en.wikipedia.org/wiki/Planetfall") and [package content images]("http://gallery.guetech.org/planetfall/planetfall.html")
[an actual java simulated interface to a Planetfall game ?]("http://www.xs4all.nl/~pot/infocom/planetfall.html")

---

### Post by Doctor J. on 2008-10-07
The big name titles you mention most likely belong to  big name studios that could sue the pants off Canonical - they'll never be in our repository.  Do a web search for whichever game you're interested, you might find a pirate archive available for download.  There really is no incentive for anybody to work this stuff over and spend time making a 'native' version.  As Matakoo stated, the interpreters are readily available for linux, that is where the developers spend their time.  The only 'nostalgic' games that are directly available through the repository are two lesser known titles "Flight of the Amazon Queen" and "Beneath a Steel Sky".  Note that both these are not text adventures, but graphic adventures a la "Indiana Jones and the Fate of Atlantis"; instead of XZip, they run on the SCUMMVM interpreter.

---

### Post by ::: on 2008-10-07
The Zork Series is free: [http://www.infocom-if.org/downloads/downloads.html](http://www.infocom-if.org/downloads/downloads.html)

---

### Post by FranMichaels on 2008-10-07
Very cool. One thing I'd like to clarify, as the OP is looking for a "Linux version". These text adventures are really 2 things, the engine and the game data. So, there are programs that "interpret" this data, called interpreters, and can run on a plethora of platforms.

The one I use, frotz (it is in the ubuntu repos)

[http://frotz.sourceforge.net/](http://frotz.sourceforge.net/)

Install it with a simple
```
sudo apt-get install frotz
```

So for the official free downloads of zork posted above. Download the zip file, look inside, there is a folder called DATA, there is a file called ZORK1.DAT.
Extract it (let's say the home folder for ease.)

In a terminal type
frotz ZORK1.DAT

You should then see
> West of House
You are standing in an open field west of a white house, with a boarded front
door.
There is a small mailbox here.

If you enjoyed graphical adventures, I recommend scummvm.
[http://www.scummvm.org/](http://www.scummvm.org/)

Also in the Ubuntu repos, and many freed games available on the scummvm site, and some in the Ubuntu repos as mentioned (flight of amazon queen & beneath a steel sky)

There is the original text adventure, also know as colossal caves in a package called bsdgames.

To install and launch:
```
sudo apt-get install bsdgames && adventure
```

---

### Post by solitaire on 2008-10-07
Oh! I loved the Infocom games!!

Think there was a website (legally) with web based versions of Zork and Hitchhickers.

Gonna have to dig those games up now.... :D

---

### Post by Grishka on 2008-10-08
> **solitaire said:**
> Oh! I loved the Infocom games!!

Think there was a website (legally) with web based versions of Zork and Hitchhickers.

Gonna have to dig those games up now.... :D

there are quite a few such websites, you could, for example, try [http://www.douglasadams.com/creations/infocomjava.html](http://www.douglasadams.com/creations/infocomjava.html) for HGG, and [http://www.gameszoo.org/rezork/](http://www.gameszoo.org/rezork/) for Zork.

---


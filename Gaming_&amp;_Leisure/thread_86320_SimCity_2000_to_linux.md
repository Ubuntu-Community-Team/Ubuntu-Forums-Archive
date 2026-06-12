---
title: "SimCity 2000 to linux"
date: 2005-11-04
forum: Gaming &amp; Leisure
---

### Post by Nasso on 2005-11-04
I have been googling like crazy for simcity 2000 for linux, is it not available? :/

read this in a forum
"I know Sim City 2000 is available for Linux. SC3000 might be, but SC4 is not. It is on Mac."
[http://www.macworld.com/forums/ubbthreads/showflat.php?Cat=&Board=UBB22&Number=228245&page=16&view=collapsed&sb=5&o=&fpart=1](http://www.macworld.com/forums/ubbthreads/showflat.php?Cat=&Board=UBB22&Number=228245&page=16&view=collapsed&sb=5&o=&fpart=1)

found this, its what got me going :) (image below)

can anyone help me find it?

[img]http://www.sorn.net/sandy/screenshots/apps/simcity.png[/img]

---

### Post by aysiu on 2005-11-04
Maybe that's being run in Wine?

---

### Post by Jonne on 2005-11-04
[http://en.wikipedia.org/wiki/Simcity_2000](http://en.wikipedia.org/wiki/Simcity_2000)
[quote=wikipedia]SC2K was released by Maxis in 1993 for computers running the Apple Macintosh and MS-DOS operating systems. It was later re-released on a number of different platforms[1], including: Amiga (1994), Microsoft Windows, SNES (1995), Sega Saturn (1996) PlayStation (1996), Nintendo 64 (1998 ), and Game Boy Advance (2003).[/quote]
So I guess you're seeing WINE in action there.

---

### Post by Nasso on 2005-11-04
[QUOTE=aysiu]Maybe that's being run in Wine?[/QUOTE]

yeah, but the forumpost said that there was a linux-version available :)

i guess i have to start using wine :/ i wanna run native!!!! ^_^

---

### Post by Hobgoblin on 2005-11-06
Wasn't it a DOS game?  If so I'm sure you could run it under dosbox.

---

### Post by Jonne on 2005-11-06
[QUOTE=Nasso]i guess i have to start using wine :/ i wanna run native!!!! ^_^[/QUOTE]
I don't think you'll see a lot of difference between using XP to run it, or WINE. Both will be able to handle it, but you'll get a 100% CPU use either way.

...which I don't get at all. I like playing abandonware'd games too, and it sucks that these games were written in a way that a modern processor *still* has to use 100% of its power doing nothing.

---

### Post by jaavaaguru on 2007-05-08
Hi

The screenshot was from a small collection of [mostly Linux screenshots]("http://www.sorn.net/sandy/screenshots/index.php?Show=apps") on my web site.

It is indeed Sim City 2000 running under Wine on Linux. It runs really well that way and involved no messing around with settings to get it working.


Sandy

---

### Post by BoyOfDestiny on 2007-05-08
> **Hobgoblin said:**
> Wasn't it a DOS game?  If so I'm sure you could run it under dosbox.

Yup. Runs perfectly, just as good (if not better) as on my 486... Or was it 386... It's been a long time... Oh well.

Screenie.

[[IMG]http://img515.imageshack.us/img515/4116/sc2000fi5.th.jpg[/IMG]](http://img515.imageshack.us/my.php?image=sc2000fi5.jpg)

:guitar:

---

### Post by Xaimas on 2007-05-08
I Really hope they make a special Linux Doom patch, as well as other games of course, that way i won't have to switch to XP every time i want to play a game -_-

---

### Post by nbv4 on 2007-08-25
I can't get simcity to install...

```

nbv4@nbv4:~/games/Simcity 2000$ wine INSTALL.EXE
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

```

...then it just hangs. I have to ctrl+c to return to the command prompt.

I tried using different windows versions in wine, but they all give me that same error.

---

### Post by stimpack on 2007-08-25
DosBox is a much better bet for DOS games than Wine.

---

### Post by DoktorSeven on 2007-08-25
SimCity 3000 had a native Linux install, but you had to get it from the new defunct Loki, and running the thing is problematic since it's built on an old version of Linux, and therefore is hard to get going since some things in Linux has changed a bit.

Your best bet?  **lincity-ng**, a Linux game heavily inspired by SC.  It's in the Universe repositories (as of Feisty, not sure about others).

---

### Post by SOULRiDER on 2007-08-25
IMHO Lincity-ng isnt nearly as good as SC2k

---

### Post by asnd16 on 2008-02-29
I got an issue  . . .when I try and load a city or save a city it stalls . .. and must be forced to quit?? Any Ideas?

---

### Post by barrybingham on 2008-03-19
> **asnd16 said:**
> I got an issue  . . .when I try and load a city or save a city it stalls . .. and must be forced to quit?? Any Ideas?

I also have this issue with the Win95 version of SC2000. I have found however that it is possible to load cities and to save any changes providing you load the city using the "winefile" command and browsing for your saved cities. Double click the .sc2 city file and wine launches SC2000 and loads the city of your choice. If you then save it (without changing the name or target directory!) it does so without problem and without causing SC2000 to exit.

Of course this is a long way from a solution, since you still cannot start a new city and save it... othwer than by the ridiculously roundabout means of starting it on a M$ wIndows or Dosbox installation and then accessing the file from winefile. I do this because both graphics and performance seem better on the Win95 version than under DosBox.

But as to why SC2000 cannot save or load direct, I have no idea..... it's a real PITA:confused:

---


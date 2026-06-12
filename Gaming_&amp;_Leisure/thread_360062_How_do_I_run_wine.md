---
title: "How do I run wine??"
date: 2007-02-12
forum: Gaming &amp; Leisure
---

### Post by Entity` on 2007-02-12
Im a bit of an idiot installing wine and then trying to use it without reading anything.
I installed a game under it, but i dont know how to run it.

Any help please...

---

### Post by dojo on 2007-02-12
Well what i just do is after i installed a game i open the terminal 
2.type cd ~/.wine/drive_c/Program\ Files/
3.type Dir
4.A list of files will come up for the game you have installed,mine displayed World\ of\ Warcraft.
5.SO then i type cd World\ of\ Warcraft because i want to play that game.
6.thn type DIR and find the main .exe for the game in my case it would be wow.exe
7.Then i type wine wow.exe
8.If you want to run the game using opengl type -opengl at the end of your wine command.
Hope this helped.Alternetivly In ubuntu u can go to Application>Wine>Program files.

---

### Post by handy on 2007-02-12
I always run [_***WineTools***_]("http://www.von-thadden.de/Joachim/WineTools/") & use it to set up Wine after an install.

---

### Post by Sammi on 2007-02-13
Personally I hate WineTools. Isn't it outdated too?

This is an excellent resource 
for info on everything that has to do with Wine on Ubuntu: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

It includes info on running programs.

---

### Post by handy on 2007-02-14
WineTools works for me...

& personally I don't know what hate is, thankfully...

---

### Post by Sammi on 2007-02-14
> **handy said:**
> personally I don't know what hate is, thankfully...
Alright alright...

But it still is outdated. There is a unofficial bugfix version though, that you can find here: [http://download.formationos.net/](http://download.formationos.net/)

Thanks [wikipedia]("http://en.wikipedia.org/wiki/WineTools") ;)

---

### Post by machoo02 on 2007-02-14
> **Sammi said:**
> But it still is outdated. There is a unofficial bugfix version though...
Not only is it outdated, but it precludes you from getting any assistance to get your application working from the WINE developers

---

### Post by handy on 2007-02-18
> **machoo02 said:**
> Not only is it outdated, but it precludes you from getting any assistance to get your application working from the WINE developers

I only run DVDshrink, so my needs are not as great as yours...  :)

---

### Post by YokoZar on 2007-02-18
> **handy said:**
> I only run DVDshrink, so my needs are not as great as yours...  :)

You can run DVD Shrink easily without even touching Winetools.

Looks like it should work out of the box.

---

### Post by handy on 2007-02-19
> **YokoZar said:**
> You can run DVD Shrink easily without even touching Winetools.

Looks like it should work out of the box.

I have occasionally looked at other software through Wine; the fonts & other bits & pieces that WineTools installs has helped.  That was many months ago though. :)

---

### Post by handy on 2007-02-21
> **YokoZar said:**
> You can run DVD Shrink easily without even touching Winetools.

Looks like it should work out of the box.

I just did an Edgy install, used Automatix as usual to install some bits & pieces including Wine, I then installed DVDshrink clean as can be.  I think you are right, I for one probably never needed WineTools anyway... :KS

---


---
title: "Online Chess"
date: 2005-03-15
forum: Gaming &amp; Leisure
---

### Post by earobinson on 2005-03-15
is there a good program i can install to play chess online with lots of other users?

---

### Post by edwina on 2005-03-18
[QUOTE=earobinson]is there a good program i can install to play chess online with lots of other users?[/QUOTE]
 Yup, there are a few about. I usually play through FICS ([www.freechess.org](www.freechess.org)) and rather like the Jin interface, although it's a little buggy. Just click on the "Graphical interface" button on the FICS homepage, near the bottom, and it will give you some options. FICS is friendly and there are plenty of players at all levels.

I hope that helps.

---

### Post by lao_V on 2005-03-18
So we have chess lovers here on Ubuntu?!...Nice!

---

### Post by node on 2005-03-18
I play on [www.gameknot.com](www.gameknot.com) and [www.letsplaychess.com](www.letsplaychess.com)

---

### Post by Jad on 2005-03-18
games.yahoo.com

---

### Post by kb00heda on 2005-03-18
I usually use xboard. It's possible to, e.g., log on to servers like ICC and FICS, which I find to be good places to play chess at.

Just run

ICC: "xboard -ics -icshost chessclub.com"
FICS: "xboard -ics -icshost freechess.org"

Try them out! :)

/David

---

### Post by fng on 2005-03-18
eboard is also another client for ICC and FICS

---

### Post by ipreferpi on 2007-06-11
I am having trouble getting fics to work. It loads the new window and says welcome, but nothing else happens. Also, I can't install the jin-2.14.1-unix.tar.gz
I dont actually know how to compile anything, but ive read several guides for installing programs from .tar.gz and i can't get it to work.... Basically, i don't know anything. 
oh, I have java installed (i think). Sorry for hijacking your thread.

---

### Post by ScottLij on 2007-06-12
> **ipreferpi said:**
> I am having trouble getting fics to work. It loads the new window and says welcome, but nothing else happens. Also, I can't install the jin-2.14.1-unix.tar.gz
I dont actually know how to compile anything, but ive read several guides for installing programs from .tar.gz and i can't get it to work.... Basically, i don't know anything. 
oh, I have java installed (i think). Sorry for hijacking your thread.

Typically all you have to do to install Jin on Ubuntu/Linux is to extract the folder from the tar.gz file and then "create a launcher" that points to the Jin file in the root Jin folder.

---

### Post by jacksaff on 2007-06-12
The best client for fics IMO is babas chess. It doesn't run on linux but versions before the latest one run perfectly under wine.
Anyone know what happened to knights? It was looking good a couple of years ago but it seems to have been abandoned.

---

### Post by ipreferpi on 2007-06-12
It took some work, but i  now have java version 1.6. The program will run and give me an option to log in, but after that the window is blank and it says "welcome to the free internet chess server."

---

### Post by jubalj on 2007-10-13
The latest babas chess (4.0 w2k version) works fine under gutsy install. However there is a sig lag in the  UI, i am loosing a couple of seconds per move because of it.. Anyone worked out the most optimised settings for both wine and babas to get the latency down?

---

### Post by UbuWu on 2007-10-14
The next version of pychess will be able to play on FICS.

---

### Post by RealMabu on 2008-01-22
> **kb00heda said:**
> I usually use xboard. It's possible to, e.g., log on to servers like ICC and FICS, which I find to be good places to play chess at.

Just run

ICC: "xboard -ics -icshost chessclub.com"
FICS: "xboard -ics -icshost freechess.org"

Try them out! :)

/David

Hello David.
How did you manage to make xboard work?
I get a "missing font" error.
To be precise:
```

xboard: no fonts match pattern -*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*

```

Can you help me?
Thanks.
Mabu

---

### Post by mivo on 2008-01-22
Mabu, did you install the xfonts-75dpi package? An alternative is also xfonts-100dpi. Either of them should work.

---

### Post by RealMabu on 2008-01-23
> **mivo said:**
> Mabu, did you install the xfonts-75dpi package? An alternative is also xfonts-100dpi. Either of them should work.

Yes, both of them according to Synaptic Package Manager and aptitude:
```

----.----$ aptitude show xfonts-75dpi xfonts-100dpi
Pacchetto: xfonts-75dpi
**Stato: installato**
Installato automaticamente: sì
Versione: 1:1.0.0-3
Priorità: opzionale
Sezione: x11
Responsabile: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Dimensione pacchetto installato: 4674k
Dipende: xfonts-utils (>= 1:1.0.0-6)
Consiglia: xfs | xserver
Descrizione: Caratteri per X a 75 dpi
...

Pacchetto: xfonts-100dpi
**Stato: installato**
Installato automaticamente: sì
Versione: 1:1.0.0-3
Priorità: opzionale
Sezione: x11
Responsabile: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Dimensione pacchetto installato: 5014k
Dipende: xfonts-utils (>= 1:1.0.0-6)
Consiglia: xfs | xserver
Descrizione: Caratteri per X a 100 dpi
...

```

Although it's in italian language I guess you can easily understand the bold part.

Any other ideas?
Thanks.

---

### Post by mivo on 2008-01-23
ttf-freefont is probably installed as well? XBoard works fine here, and on this box it is a fairly "vanilla" Ubuntu installation without any major tweaking.

---

### Post by ynnhoj on 2008-01-23
[chess at work](http://www.chessatwork.com/) is a cool site for playing correspondence games.  there are a few other urls (redhotpawn.com, redhotchess.com, and one or two others) that also access the same service; same users and games, just different looks.

---

### Post by RealMabu on 2008-01-23
> **mivo said:**
> ttf-freefont is probably installed as well? XBoard works fine here, and on this box it is a fairly "vanilla" Ubuntu installation without any major tweaking.

Everything seems to be related to the fact that I was connecting to the ubuntu box through NX:
-FreeNX server (ubuntu)
-NX Client (Win32).

I thank everybody but I switch to the other thread:
[http://ubuntuforums.org/showthread.php?p=4193066](http://ubuntuforums.org/showthread.php?p=4193066)

Thanks
Mabu

---

### Post by thenickrulz on 2011-05-06
> **edwina said:**
> Yup, there are a few about. I usually play through FICS ([www.freechess.org]("http://www.freechess.org")) and rather like the Jin interface, although it's a little buggy. Just click on the "Graphical interface" button on the FICS homepage, near the bottom, and it will give you some options. FICS is friendly and there are plenty of players at all levels.

I hope that helps.
Yes but i need java.. how do i get online on x board???:confused:

---

### Post by Perfect Storm on 2011-05-06
Necromancing. Thread closed.

---


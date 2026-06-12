---
title: "want a good game for linux."
date: 2011-05-15
forum: Gaming &amp; Leisure
---

### Post by abhishek39 on 2011-05-15
i have a very slow computer, but i can get ubuntu run perfectly on it.
also, i have a very very slow net, donno y bt it's catching jst 2 or 3 kbps speed, since i got ubuntu.
AND i want a good game on my ubuntu which is nt to large to download.
i prefer role playing and strategy games.
any help will be greatly admired.
thanks

---

### Post by HolgerB on 2011-05-15
Try nethack:
[http://en.wikipedia.org/wiki/NetHack](http://en.wikipedia.org/wiki/NetHack)

There are also some other roguelike games such as DoomRL

---

### Post by Perfect Storm on 2011-05-15
Best Rogue game ever (IMHO): [Dungeon Crawl Stone Soup](http://crawl.develz.org/wordpress/)
Get the dev version, a lot of improvements since the last stable release.

---

### Post by goodbyemrevans on 2011-05-15
adom
[http://www.adom.de/adom/download.php3](http://www.adom.de/adom/download.php3)

roguelike again

---

### Post by abhishek39 on 2011-05-15
> **HolgerB said:**
> Try nethack:
[http://en.wikipedia.org/wiki/NetHack](http://en.wikipedia.org/wiki/NetHack)

There are also some other roguelike games such as DoomRL
the link you gave led me to a site, 
i found much information about the game except the download,
or even it was available, it's too complicated for such a slow network connection.
so i jst wanna have a download link which starts download directly, or the commands to type in the terminal.
same message for the second reply by some Artificial Intelligence.

---

### Post by krapp on 2011-05-15
Go to the Ubuntu Software Center. Type in Wesnoth in the search field, and install The Battle for Wesnoth. It's not the smallest game in the repositories, but it's not huge either. It's a turn-based strategy with role-playing elements set in a swords-and-sorcery world. It's like a giant chess game with many, many, many units to level; with many single player campaigns to play (you can play multiplayer too); with a very active community at [http://www.wesnoth.org/](http://www.wesnoth.org/). And it's relatively light on resources, and published under the best license of all (GPL).

---

### Post by Perfect Storm on 2011-05-15
> **abhishek39 said:**
> the link you gave led me to a site, 
i found much information about the game except the download,
or even it was available, it's too complicated for such a slow network connection.
so i jst wanna have a download link which starts download directly, or the commands to type in the terminal.
same message for the second reply by some Artificial Intelligence.

```
gksu gedit /etc/apt/sources.list
```

add those two lines at the buttom:

**## Dungeon Crawl Stone Soup v 0.8**
**deb [http://crawl.develz.org/debian](http://crawl.develz.org/debian) crawl 0.8**

Then:
```
wget http://crawl.develz.org/debian/pubkey -O - | apt-key add -
sudo apt-get update
sudo apt-get install crawl-tiles
```

Just ignore authenticated warning if it complains.

When you start the game, it's highly recommendable to run the Tutorial first.

Also the ultimate handbook for Dungeon Soup (everything from Species, stats, weapons, which god to worship etc. compendium): [http://crawl.chaosforge.org/index.php?title=CrawlWiki](http://crawl.chaosforge.org/index.php?title=CrawlWiki)

---

### Post by HolgerB on 2011-05-15
> **abhishek39 said:**
> the link you gave led me to a site, 
i found much information about the game except the download,
or even it was available, it's too complicated for such a slow network connection.
so i jst wanna have a download link which starts download directly, or the commands to type in the terminal.
same message for the second reply by some Artificial Intelligence.
Ahaaaa ? 

So "a slow network connection" disables brain function ? :confused:

How complicate can it be enter the following keyword: "nethack linux download"

Ok, lets try it:
[http://lmgtfy.com/?q=nethack+linux+download](http://lmgtfy.com/?q=nethack+linux+download)

Hm, the first link is pretty much the same I could get when following the links inside Wikipedia to the main site of nethack which reveals a download page only two clicks apart.

That is even possible on an 28.8k modem.

Peace...

---

### Post by abhishek39 on 2011-05-16
i love installing files from commands.
and yours worked perfectly.
thanks

apart from that i have also downloaded these files wasting my lot of time and data
1> adom-111-elf.tar.gz
2> stone_soup-0.8.0.tar.bz
plz help me installing them.

---

### Post by eltommo on 2011-05-16
Anything wrong with minecraft?

---

### Post by abhishek39 on 2011-05-16
[B]Dungeon Crawl Stone Soup v 0.8
i hav installed this one form the codes gives by arti. int.
but my computer hangs on starting the game
after it loads.
a page comes where we enter name
choose type of game etc.
i can move my mouse pointer after some time but cant click any where
the keyboard doesn't seem to work that time.
i cant even exit d game.
i had to reset my computer.
wat to do.
[/B]

---


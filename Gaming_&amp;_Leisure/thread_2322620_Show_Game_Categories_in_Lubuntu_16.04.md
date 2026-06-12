---
title: "Show Game Categories in Lubuntu 16.04"
date: 2016-04-29
forum: Gaming &amp; Leisure
---

### Post by West Swan on 2016-04-29
Howdy,

I don't think this has been asked before.

Am running 32bit Lubuntu 16.04  and have over 300 games installed.

As the attached screenshot shows these appear as a long list basically from numbers first then A-Z

Is there any program that will automatically put these games into categories .e.g First Person Shooter or Card Games or Educational or Strategy or Adventure or Other etc?

Just some way of finding the type of game you want to play more quickly?  Some require scrolling down and down and down.

I know most loved games can be pinned to the desktop.

Regards,

Paul

---

### Post by vasa1 on 2016-04-29
I suspect you'll have to do that yourself :(

I think, but I'm not sure, that Lubuntu (or any other *buntu) looks at the "Category" section of each application's .desktop file in */usr/share/applications* to decide where to slot what.

---

### Post by vasa1 on 2016-04-29
I'm assuming your games have *.desktop* files and that these *.desktop* files are in */usr/share/applications/* and that you're willing to take a little trouble to get things sorted.

Open a terminal and run *grep -i game /usr/share/applications/*.desktop* and post the entire output, including the command, between code tags.

The idea is to see how the games are already categorized. On my system, I have just the one game and I see this:```
$ grep -i game /usr/share/applications/*.desktop
/usr/share/applications/gnome-mahjongg.desktop:Keywords=game;strategy;puzzle;board;
/usr/share/applications/gnome-mahjongg.desktop:Categories=GNOME;GTK;Game;BoardGame;
$ 
```

---

### Post by West Swan on 2016-04-29
> **vasa1 said:**
> I'm assuming your games have *.desktop* files and that these *.desktop* files are in */usr/share/applications/* and that you're willing to take a little trouble to get things sorted.

Open a terminal and run *grep -i game /usr/share/applications/*.desktop* and post the entire output, including the command, between code tags.

The idea is to how the games are already categorized. On my system, I have just the one game and I see this:```
$ grep -i game /usr/share/applications/*.desktop
/usr/share/applications/gnome-mahjongg.desktop:Keywords=game;strategy;puzzle;board;
/usr/share/applications/gnome-mahjongg.desktop:Categories=GNOME;GTK;Game;BoardGame;
$ 
```


Hi Vasa1

I am in Margaret River for the weekend    [https://en.wikipedia.org/wiki/Margaret_River_%28wine_region%29](https://en.wikipedia.org/wiki/Margaret_River_%28wine_region%29)   enjoying some of what life has to offer :P

Will do as you requested upon my return.

Regards,

Paul

---

### Post by vasa1 on 2016-04-29
> **West Swan said:**
> Hi Vasa1

I am in Margaret River for the weekend    [https://en.wikipedia.org/wiki/Margaret_River_%28wine_region%29](https://en.wikipedia.org/wiki/Margaret_River_%28wine_region%29)   enjoying some of what life has to offer :P

Will do as you requested upon my return.

Regards,

Paul Have fun!

That file maybe a bit bulky. In that case you could paste the output into a plain text editor. save it and upload it here as an attachment.

---

### Post by West Swan on 2016-05-01
> **vasa1 said:**
> Have fun!

That file maybe a bit bulky. In that case you could paste the output into a plain text editor. save it and upload it here as an attachment.


Thanks Vasa1 - certainly had fun but now having a quiet recovery day.

I'm afraid even a simple text file is too large to attach as it is very long and 32Kb in size.  Actually Zip files are also accepted here so here it is :-)

Regards,

Paul

---

### Post by vasa1 on 2016-05-02
Sorry for the delay. But it looks like these are the main categories:
ActionGame
AdventureGame
ArcadeGame
BlocksGame
BoardGame
CardGame
Education
KidsGame
LogicGame
RolePlaying
Simulation
SportsGame
StrategyGame

Some games will obviously appear in more than one category.

I'll look at this later :)

---

### Post by West Swan on 2016-05-02
Thank you :-)

---

### Post by vasa1 on 2016-05-02
And here's a spreadsheet with two columns, games and type. Some are missing the type but I guess you can fill that in.

The next step will be to include the games category-wise into a right-click menu which can be done without too much trouble.

---

### Post by West Swan on 2016-05-05
> **vasa1 said:**
> And here's a spreadsheet with two columns, games and type. Some are missing the type but I guess you can fill that in.

The next step will be to include the games category-wise into a right-click menu which can be done without too much trouble.


Hi Vasa1,

Got that thanks :-)

Is that right click menu something I can do e.g. by some kind of sudo apt-get command?

Regards,

Paul

---

### Post by vasa1 on 2016-05-05
> **West Swan said:**
> ...

Is that right click menu something I can do e.g. by some kind of sudo apt-get command?

...
No the right-click menu is built into Lubuntu. It is just a collection of commands arranged according to the user's fancy. No extra software needed.

I'm facing a deadline now but I'll put up a sample for you to play with in a couple of days.

But for now, please look at [http://pclosmag.com/html/Issues/201108/page10.html](http://pclosmag.com/html/Issues/201108/page10.html)

---


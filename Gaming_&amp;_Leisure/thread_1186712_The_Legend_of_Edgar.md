---
title: "The Legend of Edgar"
date: 2009-06-13
forum: Gaming &amp; Leisure
---

### Post by riksweeney on 2009-06-13
Parallel Realities have a new game out. The Legend of Edgar is a 2D platform game with a persistent world. Currently the game is only at version 0.1 but there is still a lot of gameplay available.

[http://www.parallelrealities.co.uk/projects/edgar.php]("http://www.parallelrealities.co.uk/projects/edgar.php")

If you haven't played any of Parallel Realities' other games, they're well worth checking out while you are there.

Enjoy!

---

### Post by hansdown on 2009-06-13
This could be fun.

Thanks riksweeney.

---

### Post by efikkan on 2009-06-13
It seems ok so far, considering it's version 0.1.
When the graphics and gameplay are polished, this might be a game worth playing.

Bug: The player fails to jump while walking on slopes.

---

### Post by riksweeney on 2009-07-23
I've updated the game to 0.20 and it contains a wealth of fixes. I've also uploaded a video to YouTube of part of the game (the sound's a bit of of sync though).

---

### Post by riksweeney on 2010-01-05
[The Legend of Edgar]("http://www.parallelrealities.co.uk/projects/edgar.php") is still under development and is at version 0.45. There are currently 11 maps to explore and at least 5 bosses to fight along the way

[IMG]http://www.parallelrealities.co.uk/images/edgar/02.png[/IMG]

---

### Post by farrell2k on 2010-01-06
> **efikkan said:**
> It seems ok so far, considering it's version 0.1.
When the graphics and gameplay are polished, this might be a game worth playing.

Bug: The player fails to jump while walking on slopes.

Yeah, because a game has to have great graphics to be worth playing. :roll:

It's nice, TC.  Keep up the good work.

---

### Post by Lepodo on 2010-01-06
Great graphics and a solid game. Thanks for the info!

---

### Post by riksweeney on 2010-02-26
The Legend of Edgar has been updated to 0.50. This release adds a new map and features (optional) medal support.

---

### Post by riksweeney on 2010-03-08
The Legend of Edgar has been updated to 0.51

Changes

Added the missing Basement boss
Fixed the broken translations in the Windows build
The repellent clouds can no longer be picked up when you reload a game
Fixed the crash in the Library when reading the book
The game no longer segfaults if it is installed incorrectly

---

### Post by riksweeney on 2012-01-13
I haven't posted here for a while, but the game is still being developed. The main story is completable, and the optional side quest is being finished off.

The most notable changes include a much smaller village map, offline medal support (think Achievements and Trophies), the ability to continue if you die against a boss and a large number of bug fixes and features.

You can download pre-built binaries and the source code from here

[https://sourceforge.net/projects/legendofedgar](https://sourceforge.net/projects/legendofedgar)

---

### Post by oldrocker99 on 2012-01-15
Thanks! I'm installing it now!

---

### Post by riksweeney on 2012-02-10
The Legend of Edgar has been updated to 0.97

Changes

Added the next part of the optional quest
Changed a puzzle in the Laboratory map
Made a change to the Fortress Mine map
Added a new medal: "Completed the game without continuing"
Added another cheat that prevents instant death in lava
Fixed memory leaks in the menus
Corrected some spelling problems

[https://sourceforge.net/projects/legendofedgar](https://sourceforge.net/projects/legendofedgar)

---

### Post by riksweeney on 2012-04-12
The Legend of Edgar has been updated to 0.99

Changes

The game is now 100% completable (barring any bugs)
Added the final boss
Windows should now render UTF-8 strings correctly (such as Russian)
The Watchdog no longer occasionally freezes after charging at Edgar
The secret wall in the Crypt can now be destroyed
Made the final flooded tunnel in the Dungeon wider
The Lightning Sword charges are no longer reset to 10 when an enemy steals it
The Black Book now turns into the Gargoyle rather than the Golem
Fixed a bug in the cutscene when fixing the power generators
Fixed a potential crash when changing maps from the Outskirts to the Fortress
Fixed a problem where you sometimes could not jump on ice cubes or floating snappers

[https://sourceforge.net/projects/legendofedgar](https://sourceforge.net/projects/legendofedgar)

---

### Post by QOLIM on 2012-05-16
It looks like fun, but I got a bug when I press one of the arrow keys (or another if I change it in the settings) to walk, he only walks one pixel further and then stops. 
So it's quite unplayable if you have to keep hitting the arrowkeys like a madman just to get a bit further.

I did a google search, but it looks like I'm the only one with this problem

---

### Post by riksweeney on 2012-05-16
That sounds odd. What are you running (12.04 32bit etc)? I'll try and reproduce it.

---

### Post by QOLIM on 2012-06-13
I'm using kubuntu 11.10 (32 bit)

---

### Post by riksweeney on 2012-06-18
> **QOLIM said:**
> I'm using kubuntu 11.10 (32 bit)

I couldn't reproduce this unfortunately, but it might be that SDL thinks that something connected to your machine is a joystick. You could try running the game from the command line with "-nojoystick" e.g.

```
edgar -nojoystick
```

You can view a list of the command line options by typing in

```
edgar -h
```

---

### Post by QOLIM on 2012-07-12
Thanks man, tried it again today and yes, with the nojoystick it works like a charm, thanks!
Now I can finally enjoy the game :D

---

### Post by riksweeney on 2012-12-12
The Legend of Edgar has been updated to 1.05

Changes

Updated Italian, Russian and Ukrainian translations
Added a call switch to a lift in the Sewer
Added a reset switch for the crate behind the bombable wall in the Basement
Spiders are now colour coded based upon their energy
Other minor bug fixes

[https://sourceforge.net/projects/legendofedgar](https://sourceforge.net/projects/legendofedgar)

---

### Post by holastickboy on 2012-12-13
> **riksweeney said:**
> The Legend of Edgar has been updated to 1.05

Changes

Updated Italian, Russian and Ukrainian translations
Added a call switch to a lift in the Sewer
Added a reset switch for the crate behind the bombable wall in the Basement
Spiders are now colour coded based upon their energy
Other minor bug fixes

[https://sourceforge.net/projects/legendofedgar](https://sourceforge.net/projects/legendofedgar)

Might give it a try, thanks for sharing!

---

### Post by jessica5 on 2013-09-23
Hola, buenas tardes, escribo para compartir unos aportes y reportar algunos errores en el juego "The legend of edgar"
El motivo surge a partir de un proyecto de la facultad que consiste en cooperar con el sofware libre. Es por ello que baje este juego y lo estuve probando:
Aporte:
Estaria bueno que al inicio, cuando empiezan a hablar los personajes, en vez de decir The edgar´s father, diga el padre de edgar, porque el texto a continuacion queda en castellano.

Reporte:
Por otro lado, algunos errores que me saltaron al ejecutarlo:
Al abrirlo y cerrarlo, pide hacerlo dos veces.
Cuando abris el juego y lo dejas un rato abierto, al retomarlo aparece el cartel de menu, le das quitar y cuando moves a edgar unos pasos te vuelve a aparecer y te pregunta si queres salir del juego, le presionas escape como para salir del menu y retomar el juego, y hace lo mismo.
Por ello hoy no he podido seguir la busqueda.
Me gustaria que me ayuden como hacerlo.
Muchas Gracias!!!
Jessica

---

### Post by bibek2 on 2013-09-23
> **jessica5 said:**
> Hola, buenas tardes, escribo para compartir unos aportes y reportar algunos errores en el juego "The legend of edgar"
El motivo surge a partir de un proyecto de la facultad que consiste en cooperar con el sofware libre. Es por ello que baje este juego y lo estuve probando:
Aporte:
Estaria bueno que al inicio, cuando empiezan a hablar los personajes, en vez de decir The edgar´s father, diga el padre de edgar, porque el texto a continuacion queda en castellano.

Reporte:
Por otro lado, algunos errores que me saltaron al ejecutarlo:
Al abrirlo y cerrarlo, pide hacerlo dos veces.
Cuando abris el juego y lo dejas un rato abierto, al retomarlo aparece el cartel de menu, le das quitar y cuando moves a edgar unos pasos te vuelve a aparecer y te pregunta si queres salir del juego, le presionas escape como para salir del menu y retomar el juego, y hace lo mismo.
Por ello hoy no he podido seguir la busqueda.
Me gustaria que me ayuden como hacerlo.
Muchas Gracias!!!
Jessica
Welcome to the forum :) I wish I could understand what you typed though :(

---

### Post by jessica5 on 2013-09-25
Hello, good afternoon, I write to share a few contributions and report some errors in the game "The legend of edgar&#8221;
contribution: would be good that at the beginning, when they start to talk about the characters, translate every word to Spanish.
 
report: on the other hand, some errors that I jumped to run it:. To open it and close it, asks him to do to-do times when abris game and leave no open time to retake it appears the poster menu, you give to remove and when moving an edgar steps you reappears and it asks you if you want to exit the game, press you escape to exit and return to the game, and does the same thing. I would like to help me how to do it. Thanks a lot...

---

### Post by riksweeney on 2013-10-22
I'm looking for people to help translate the game into their native language. You can contribute by logging into Launchpad. I'm not expecting anyone to translate all 1500 sentences, just one or two is good enough (any little helps).

[https://translations.launchpad.net/edgar](https://translations.launchpad.net/edgar)

Any help is appreciated!

Richard

---


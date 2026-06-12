---
title: "Planescape: Torment in wine"
date: 2006-04-29
forum: Gaming &amp; Leisure
---

### Post by jjf on 2006-04-29
I've installed the 2-CD version of Planescape Torment through wine, and I'm trying to run it.  The game starts fine, and I can create a character with no problems.  When I try to start the game, I see the first splash screen and the progress bar at the bottom.  Then Torment crashes. 

Because of the timing, I suspect that Torment doesn't know where to find the data from the play cd.  I have the second cd in my drive, and I've directed wine that D: is /media/cdrom0.  I also copied the data to my Torment directory in a subdirectory called "cd2."  Here are the first few lines of my Torment.ini file.  Any help would be appreciated:

```
[Alias]

HD0:=c:\Program Files\Black Isle\Planescape - Torment\

CD1:=c:\Program Files\Black Isle\Planescape - Torment\

CD2:=c:\Program Files\Black Isle\Planescape - Torment\cd2\

CD3:=c:\Program Files\Black Isle\Planescape - Torment\cd3\

CD4:=c:\Program Files\Black Isle\Planescape - Torment\cd4\
```

---

### Post by Rinzwind on 2006-04-30
Cuz I love Torment I did have a go and see if I get it working.

- I installed wine with this topic: [http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585) )
- I used this installer to install Torment: [http://www.liflg.org/?catid=7&gameid=40](http://www.liflg.org/?catid=7&gameid=40)
and Torment works with 1 problem(**). Had to change the INIT file to Z: instead of G: Torment crashed after I started with G: (maybe that's your problem? The letter you need is shown in the startup inside the terminal window).

Accoring to that website you also need WINEX 3.3.1 for Torment to work. 3.3 doesn't work.  What version do you have?


(**)Sound doesn't work. Could someone tell me if the changed anything to get sound working?

---

### Post by linuxa on 2006-05-01
Try the torment thread at winehq:

[http://appdb.winehq.org/appview.php?appId=294](http://appdb.winehq.org/appview.php?appId=294)

---

### Post by Perfect Storm on 2006-05-01
Why don't you guys get the loki installer instead? [http://www.liflg.org/?catid=7&gameid=40](http://www.liflg.org/?catid=7&gameid=40)

---


---
title: "KAG - Rights issue when i copy game in /opt root folder"
date: 2017-01-30
forum: Gaming &amp; Leisure
---

### Post by zohran on 2017-01-30
Hello, in first sorry if sometimes i don't speak english very well, i'm french :)
[U][B]
I use Ubuntu 16.10 and i would like to use KAG:[/B][/U] [https://www.kag2d.com/en/](https://www.kag2d.com/en/)

The game works  fine when it's in my folder, but when I copy it to the root / opt folder  (and I've changed the permissions) the game does not run properly ... If I do not run the game with the sudo command, the game does not run properly.

I also create a shortcut for the game.

```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=King Arthur's Gold
Comment=Build freeform constructions as a medieval Builder, fight in sword duels as a Knight or snipe with your bow as an Archer.
Icon=/opt/KAG/KAG.ico
Exec=/opt/KAG/KAG
Categories=Game
```

Finally, I add my user to the group games

_**/opt/KAG** rights directory:_ [U][URL="http://img11.hostingpics.net/pics/260987opt.png"]http://img11.hostingpics.net/pics/260987opt.png
[/URL]
**/usr/share/applications/KAG** rights shortcut:[/U] [URL="http://img11.hostingpics.net/pics/245877kag.png"]http://img11.hostingpics.net/pics/245877kag.png


[/URL]

---

### Post by howefield on 2017-01-30
Thread moved to the "*Gaming & Leisure*" forum.

---

### Post by Perfect Storm on 2017-01-30
When you say it won't run properly - what do you mean? Won't it load?

---

### Post by zohran on 2017-01-30
It does not launch the updates or the edges of the window disappear if I do not launch the application as root

---

### Post by oldrocker99 on 2017-01-30
Where is the data for the game? If it's not in your /home directory, it may need chown for you to run it.

```
sudo chown yourusername:yourusername /path/to/data
```

chown stands for "change owner"

Of course, if the executable is in your /home directory, it'll run without root. Try that.

---

### Post by zohran on 2017-01-30
It's good, thanks you for your help, i made a mistake !

---

### Post by oldrocker99 on 2017-01-30
Please mark this thread as [SOLVED]. Whose advice did you use?

---

### Post by zohran on 2017-01-31
I was wrong, the problem is not always solved. The bug window again.The outline of the window disappears and its icon in the dashboard when the app is opened is not displayed

[IMG]http://img11.hostingpics.net/pics/912249Capturedu20170131122135.png[/IMG]

---

### Post by zohran on 2017-01-31
I found out where the problem comes from. The bug window when the window animations are activated!

That was not an issue of law.

I do not know if we can correct that ...

---


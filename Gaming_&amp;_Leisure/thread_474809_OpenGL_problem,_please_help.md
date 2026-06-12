---
title: "OpenGL problem, please help"
date: 2007-06-15
forum: Gaming &amp; Leisure
---

### Post by Ryan Sullivan on 2007-06-15
I am wanting to play openGL games using an XGL session with beryl, and i have read that i can be done i have done the guide and i get this following error.


ryan@ubuntu:~$ nonXgl JediAcademy.exe
Password:
xhost:  unable to open display ":93"
exec: 15: JediAcademy.exe: not found
ryan@ubuntu:~$

Can anyone help me with this problem please. Do i hae to put the .exe any a specific file because im using the disk to play this game (start wars jedi academy).

Please help!!!!

---

### Post by cogadh on 2007-06-15
Install and use Wine to run the game, .exe files can't be run in Linux otherwise. Wine is an open source implementation of the Windows API, including DirectX functions. It's pretty much the best way (IMO) to run Windows games on Linux. In fact, according to Wine's AppDB, Jedi Academy is rated Platinum for usability: [http://appdb.winehq.org/appview.php?iVersionId=2315](http://appdb.winehq.org/appview.php?iVersionId=2315)

---

### Post by Ryan Sullivan on 2007-06-16
I am able to run the game perfectly in gnome, but i want to run the game in Beryl, but the thing is beryl uses all my graphics card so i can't open openGL. I followed a guide posted in this forum and i got the last error.

---

### Post by shad0w_walker on 2007-06-16
try this:

```
nonXgl wine JediAcademy.exe
```

---

### Post by Ryan Sullivan on 2007-06-16
Nope, no luck, i get this 

xhost:  unable to open display ":93"
wine: cannot find '/home/ryan/.wine/drive_c/Program'
ryan@ubuntu:~$   


Any ideas??  How can i see my display number?

---

### Post by shad0w_walker on 2007-06-16
Can you link me to the guide you followed for this nonXgl thing? Its always helpful to get more information on how things are being done.

---

### Post by cogadh on 2007-06-16
> **Ryan Sullivan said:**
> Nope, no luck, i get this 

xhost:  unable to open display ":93"
wine: cannot find '/home/ryan/.wine/drive_c/Program'
ryan@ubuntu:~$   


Any ideas??  How can i see my display number?

Not sure about the display number thing, but the Wine error is due to the space in the name "Program Files". When you enter the Wine command, put a backslash between "Program" and "Files":
```
wine /home/ryan/.wine/drive_c/Program\Files/game/executable
```

---

### Post by Ryan Sullivan on 2007-06-16
[http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

This is the link to the guide that i followed

And i tried what you said and nothing happened


Please help!!!!!

---


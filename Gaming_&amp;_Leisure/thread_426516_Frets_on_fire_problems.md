---
title: "Frets on fire problems"
date: 2007-04-28
forum: Gaming &amp; Leisure
---

### Post by djqz on 2007-04-28
Hi

I just found out about and downloaded frets on fire (1.2.451). Once I'd downloaded I extracted the .tar.gz to my desktop and then was able to run it by clicking on the fretsonfire icon. 

Everything looked good, the menu loaded and I was able to go to the settings & change resolution etc. However when I try to start the game or run the tutorial I get the following message " Name or service not known" & I get booted back to the main menu.

Any ideas??

I am running Edgy 6.10 on an Athlon XP 3000 with 1GB of ram and Nvidia 5500 graphics

---

### Post by buttons on 2007-04-28
> **djqz said:**
> Hi

I just found out about and downloaded frets on fire (1.2.451). Once I'd downloaded I extracted the .tar.gz to my desktop and then was able to run it by clicking on the fretsonfire icon. 

Everything looked good, the menu loaded and I was able to go to the settings & change resolution etc. However when I try to start the game or run the tutorial I get the following message " Name or service not known" & I get booted back to the main menu.

Any ideas??

I am running Edgy 6.10 on an Athlon XP 3000 with 1GB of ram and Nvidia 5500 graphics

Run it from terminal and see if you get a more useful message?

---

### Post by djqz on 2007-04-29
Just tried running it via terminal by navigating to the /FretsOnFire directory and typing

 ```
exec ./FretsOnFire.bin
```

The application failed to load, my terminal window closed and it killed my mouse!? - After restarting X my mouse started responding again.

---

### Post by djqz on 2007-04-29
Just tried running again using 

```
./FretsOnFire.bin
```

Same problems with mouse but got following code in terminal

```
File "/home/skyostil/src/ex_Freeze3.03/initscripts/console.py", line 27 in ?
File "src/FretOnFire.py", line 64 in ?
File "src/GameEngine.py", line 166 in ?
File "src/Svg.py", line 77 in __init__
File "src/Svg.py", line 240 in __init__

AttributeError: 'module' object has no attribute 'GMatrix33'
```

HELP

---

### Post by djqz on 2007-04-29
Previous post was the result of running ```
./FretsOnFire.bin
```

If I run ```
./FretsOnFire 
``` the game launches fine but I still get the 'name or service not known' error when I try to start a game from the main menu, I get the following output in terminal:

```

Traceback (most recent call last):
  File "src/MainMenu.py", line 99, in harness
  File "src/MainMenu.py", line 131, in newSinglePlayerGame
  File "src/GameEngine.py", line 260, in startServer
  File "src/Server.py", line 33, in __init__
  File "src/Network.py", line 178, in __init__
  File "/usr/lib/python2.4/asyncore.py", line 304, in bind
    return self.socket.bind(addr)
  File "<string>", line 1, in bind
gaierror: (-2, 'Name or service not known')
```

Cheers

---

### Post by djqz on 2007-04-30
I got my problems fixed [here..]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=4910")

It was because my  /etc/hosts file did not define "localhost" as "127.0.0.1"

:guitar:

---

### Post by aiwarrior on 2007-05-01
How did you get it to run??
Im running Feisty and both FretsonFire.bin and ./FretsonFire return errors.
The .bin one returns:
./FretsOnFire.bin: error while loading shared libraries: libpython2.4.so.1.0: cannot open shared object file: No such file or directory

and the normal returns a lot of error that i dont know how to fix, as its about not finding alsa in my system, because i use OSS drivers from NVIDIA binaries.
Anyone want to shed some light?

---

### Post by djqz on 2007-05-01
> How did you get it to run??

I had to edit the first line of my /etc/hosts file from.
```
127.0.1.1 daves-pc.DAVES
```
to
```
127.0.0.1 daves-pc.DAVES localhost
```

I don't think your problems are the same as mine. I suggest you go on over to [www.fretsonfire.net](www.fretsonfire.net) forums. The people there were very helpful to me.

Good luck!!

---


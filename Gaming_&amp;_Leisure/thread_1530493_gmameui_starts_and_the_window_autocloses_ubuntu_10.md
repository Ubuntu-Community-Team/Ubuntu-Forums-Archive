---
title: "gmameui starts and the window autocloses ubuntu 10.04"
date: 2010-07-13
forum: Gaming &amp; Leisure
---

### Post by Salvagluque on 2010-07-13
Hello

I have this problem with gmameui in ubuntu 10.04.

Qhen I installed it yestarday everything worked well, but then I tried to instal kxmame to compare them. As result the gmameui starts but inmediatly after opening it shuts down itself.

salvador

Hello 

when I installed gmameui yesterday everything worked well, but then I tried to install kxmame to compare them. As result the gmameui starts but right after after opening it, it shuts down itself.

I&#7743; in ubuntu 10.04

I discovered I don't have mame.ini but I have installed sdlmame and also I have gmameui installed.  how can I get the mame.ini installed? and also my gmameui closes itself before it finishes starting up.

Thanks

---

### Post by ucal on 2010-07-13
Can you try running it in the terminal?  Just type this into the terminal:

```
gmameui
```

Afterwards, post whatever messages the terminal provides. Often times it's a missing library, and the terminal will tell you exactly what you need.  Other times, the solution might be a bit more complex :D

---

### Post by cariboo on 2010-07-13
Merged your thread into a new thread, posting at the end of old threats won't get you help any faster.

---

### Post by Salvagluque on 2010-07-13
I found my computer doesn't have the mame.ini /etc/sdlmame/mame.ini (I don't have even the folder). don't know why.

the terminal shows this:
Command 'gmameui' is available in '/usr/games/gmameui'
The command could not be located because '/usr/games' is not included in the PATH environment variable.
gmameui: command not found

thanks

---

### Post by Salvagluque on 2010-07-14
the same post is in this thhread

[URL="I also started this tread  http://ubuntuforums.org/showthread.php?p=9585874#post9585874"]
Re: MAME Emulator Recommendation - Ubuntu 9.10[/URL]

---

### Post by Salvagluque on 2010-07-14
I just discovered this.

when I try gmameui in the Applications>Accesories>terminal, it says it doesn't have the path /usr/games in the path variable environment.

But when I try the AWN terminal, in the avan window navigator it says really different stuff. Here the images.

---

### Post by ucal on 2010-07-14
Well, I would first suggest reinstalling mame.  That should get you your mame.ini back, and any other files you're missing from mame.

---

### Post by Salvagluque on 2010-07-15
Ok, I installed mame (and I took out all the xmame files. Now I have a mame folde and inside of it is the mame.ini.

/etc/mame/mame.ini

The app still cloeses itself until now.

then I installed sdlmame.  didn't add a folder just gave me this list

sdlmame4ubuntu.major.list in this address /etc/apt/sources.list.d

the app still closes itself.

I think a folder for sdlmame is missing :P

also made a sdlmame myself and added all the files from the mame folder at /etc/sdlmame. Same result :p

then I erased the mame folder but nothing changed.

jajajaja frustrating :P

then installed xmess-sdl and nothing. gmameui closes itself.:p

---

### Post by Salvagluque on 2010-07-16
My problem with gmameui is solved!!

what I had to do was rename/erase these folders /Home/PERSONAL_FOLDER/.config/gmameui and /Home/PERSONAL_FOLDER/.config/mame. That reconstructs those folders and the game can be started from Applications>Games>Gmameui.

Now the emulator runs just a good as it did before.

Thanks for the help :-)

Salvador

---


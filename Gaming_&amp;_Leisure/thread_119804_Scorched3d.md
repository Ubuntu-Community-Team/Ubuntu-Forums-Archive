---
title: "Scorched3d"
date: 2006-01-20
forum: Gaming &amp; Leisure
---

### Post by Ubuntuud on 2006-01-20
Hi, I've got a problem with scorched3d, it keeps on crashing when I double-click on the icon representing your tank (maybe it can crash on other ways, but I didn't try it). What should I do? Thanks.

---

### Post by Perfect Storm on 2006-01-20
run it through terminal, so you can check the error output.

---

### Post by Ubuntuud on 2006-01-20
There isn't any, I can run it normally but when I double click on the icon, the screen turns black, I need to restart an d lose the terminal info.

---

### Post by Harleen on 2006-01-20
With restart you mean restart the computer? :shock:
Or do you have another terminal in mind than AI? You did start the game from the command line interface?

---

### Post by Ubuntuud on 2006-01-20
I know what the terminal is. I need to restart the computer indeed. Even in windowed mode the screen turns totaly black and the cursor changes from normal to 'thinkmode' for eternity.

---

### Post by Harleen on 2006-01-20
Oh, that really shouldn't happen...
Maybe you can you kill the X-Server by pressing <CTRL>+<ALT>+<BACKSPACE> or switch to a text terminal. If not, you have a bigger problem than just a freezing application.

You can redirect the text output of Scorched3d into text files to examine the output later by starting it like that: "scorched3d > stdout.txt 2> stderr.txt"

---

### Post by Ubuntuud on 2006-01-20
In Xterm mode it crashes... If you kill the X-Server, the game won't run... And I have put the output in a text file, but where can I find the file?

---

### Post by Ubuntuud on 2006-01-20
Oh wait, I found it:
Gdk-ERROR **: X connection to :0.0 broken (explicit kill or server shutdown).
That's all...
What does it mean?

---

### Post by Harleen on 2006-01-20
The game has ran fine and stopped because someone killed the X-Server. :-\"

So the game doesn't give out any error. That doesn't make it any easier...

---

### Post by Ubuntuud on 2006-01-20
But what kan kill it? The game? Double clicking?

---

### Post by Harleen on 2006-01-20
You have killed X on my advise. Your double click caused no error message. That's what makes this difficult.

---

### Post by Ubuntuud on 2006-01-20
But I restarted my PC before running the terminal, so X should have restarted, no?

---

### Post by Ubuntuud on 2006-01-20
AI, where are you when I need you?

---

### Post by Perfect Storm on 2006-01-21
I'm a busy man ;).

I havn't been able to figure out what your problem is. It sounds like a hardware problem. Maybe it had something to do with your 3d card. I have even googled and search Scorched3d forum for your problem, but so far none.

How runs your other 3D games?

By the way how did you install the game, which package? Did you apt-get it?

---

### Post by Ubuntuud on 2006-01-21
I installed it with (this is freely translated) "instal applications". And about my other 3D games (ppracer, slune)... They run fine, but they haven't got a very high FPS rate, usualy somewhere around 25. 

And thanks for the googling...

---


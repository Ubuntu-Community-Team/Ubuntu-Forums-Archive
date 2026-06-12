---
title: "X3: Reunion - Sound issues"
date: 2009-12-30
forum: Gaming &amp; Leisure
---

### Post by Cerox Rex on 2009-12-30
Heya.

I'v resently Installed my LGP - X3: Reunion port, Such a great game, sadly I experience sound issues, that is. I get what souns like Radio static most of the time, then it suddenly migth get normal after a while and evrything sounds nice, then the damn static is comming back. Almost like i hav some Aliens trying to tak over my computer. 

I only experience this when playing X3, Evrything else work splenid.

I'm running Ubuntu 9.10 amd64.

any help on cracking this anoying invasion in my speekers is much apreciated :)

---

### Post by Sindwiller on 2009-12-31
Sounds like an app-/engine-related bug. I suggest you mail LGP about this and ask. (maybe they even have a bugtracker; I don't know for certain, since I've never bought an LGP game before)

Both X2 and X3 are known to have some sound issues on Windows which might have been passed over in the porting process.

The other cause I can think of is the 64-bit port with all those fuzzy 64-bit libraries and stuff. Don't know for sure though. I still think you should [mail LGP]("http://www.linuxgamepublishing.com/faq.php?id=35&#faq_7_1").

---

### Post by Technophobia on 2009-12-31
You could try the pulseaudio trick that works for Penumbra. 

> -Edit or create the file: "~/.pulse/client.conf" so it says "autospawn = no"
-Then kill pulseaudio by typing "killall pulseaudio" in the Terminal.
-Play Penumbra, hopefully with perfect audio!
-Type "pulseaudio -D" in the Terminal when done playing. -Jens

[http://www.frictionalgames.com/forum/showthread.php?tid=3264&pid=26667#pid26667](http://www.frictionalgames.com/forum/showthread.php?tid=3264&pid=26667#pid26667)

---

### Post by Cerox Rex on 2010-01-02
LGP have been mailed. Awaiting resposne, 

> **Technophobia said:**
> You could try the pulseaudio trick that works for Penumbra. 



[http://www.frictionalgames.com/forum/showthread.php?tid=3264&pid=26667#pid26667](http://www.frictionalgames.com/forum/showthread.php?tid=3264&pid=26667#pid26667)

pulse audio trick changed nothing. problem still there no matter what sound engien i'v tried. 

Hopfully LGP is able to help resolve this :)

---

### Post by Sindwiller on 2010-01-02
Someone posted [this]("http://ubuntuforums.org/showpost.php?p=2378018&postcount=3") in [this thread]("http://ubuntuforums.org/showthread.php?t=519507") just a while ago.

Worth a try, right? There is no guarantee that the port uses SDL though (Egosoft use all that fuzzy Direct* and Windows Media ******** :P).

---

### Post by ubu_dynamite on 2010-03-09
Maybe a little late but have you tried to update the game or
run the LGP test tool. This may tell you what your problem is

[http://www.linuxgamepublishing.com/support.php](http://www.linuxgamepublishing.com/support.php)

I don,t have the game myself but just found this reading about X3 Reunion.

---


---
title: "Found a &quot;new&quot; game for Linux - Clonk !"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2007-08-23
About a month ago I've came across an unfamiliar strategy game named Clonk.
Actually there are several games in the series
but currently only one has a native Linux client + source code , and it's free !

take a look :

[http://www.clonk.de/contents_en.html](http://www.clonk.de/contents_en.html)

---

### Post by MonkeyBoy on 2007-08-23
Well spotted!

It's quite good too...

I haven't had a proper go yet but it looks great.  Quite difficult as well.

---

### Post by sejwan on 2007-08-24
Looks interesting I'm downloading it now I will check it out after work today thanks .

---

### Post by Dark Star on 2007-08-24
Looks nice though screenshots would have helped :| Nonetheless am downloading right away :D

---

### Post by siman on 2007-08-24
yes! I know clonk from 10 years ago or so... was a great game!

---

### Post by ADT on 2007-08-24
Looks good. But I don't think my PC would be able to handle it. Dont have OpenGl capable video card.

---

### Post by siman on 2007-08-24
well, the 3d version is not really runable - it's just a test.

I played the clonk classic on a pentium 90 back then, so you should be good. Its really fun, especially in split-screen mode.

---

### Post by Stefan Wouters on 2008-05-08
I've known this game for quite some time now. It's very nice and worth every cent you pay for it.
Good to see that there's a linux version now.

---

### Post by MaximB on 2008-05-10
> **Stefan Wouters said:**
> I've known this game for quite some time now. It's very nice and worth every cent you pay for it.
Good to see that there's a linux version now.

Clonk rage is free (money free, not source ;)).

---

### Post by Bunnywinkles on 2008-05-26
Stupid question.
Ive been looking all over and cant find a play guide.
im having a hard time catching on how to play this.
i made an elevator though!
So any tips?

---

### Post by pkkid on 2008-05-27
Good find, bookmarked for playing it later this week. :)

---

### Post by Officer Dibble on 2008-05-28
Downloaded Rage, extracted, installed, doesn't do anything... nothing starts... :(

---

### Post by MaximB on 2008-05-28
> **Officer Dibble said:**
> Downloaded Rage, extracted, installed, doesn't do anything... nothing starts... :(

Have you made sure the file is executable ?

---

### Post by anjilslaire on 2008-05-28
hmm, is this it?
[http://en.wikipedia.org/wiki/Clonk]("http://en.wikipedia.org/wiki/Clonk")

EDIT:
Yup, and its pretty fun, too :)

---

### Post by Hyper Tails on 2008-05-28
Its looks pretty fun to be

never heard of it but great job 8)

---

### Post by Officer Dibble on 2008-05-30
> **MaximB said:**
> Have you made sure the file is executable ?

Yeah, it says it is executable in properties and the icon indicates it is executable... but on clicking it makes a slight effort on the Panel and then disappears completely.

My video card is 8500GT 512MB, RAM 1GB, so there's no problems with spec's etc. What's really irritating is that it runs fine in XP... but I don't want to play it in XP - I'm trying to get rid of the thing. :)

---

### Post by tatrefthekiller on 2008-05-30
Try to tun it in console using :
```
cd /repertory/game/
```
And execute the game :
```
./clonk
```
If it says the file isn't executable, type :
```
chmod +X clonk
```

If the console prints errors, paste it here.

I don't know if everybody got the same version. Here is mine :
[http://www.clonk.de/contents_en.html](http://www.clonk.de/contents_en.html)
Scroll down, and select the Linux version.

The game seems to be a little bit complicated, anybody found a guide or a manual ?

---

### Post by Officer Dibble on 2008-06-01
K... after entering those lines I'm getting the following error:

> ./clonk: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory

---

### Post by noerrorsfound on 2008-06-01
> **Officer Dibble said:**
> K... after entering those lines I'm getting the following error:
**sudo apt-get install libvorbis**, maybe? If you're on x86_64 you might have problems with it running if the binary is looking for the 32-bit version of libvorbis.

---

### Post by Officer Dibble on 2008-06-02
> **noerrorsfound said:**
> **sudo apt-get install libvorbis**, maybe? If you're on x86_64 you might have problems with it running if the binary is looking for the 32-bit version of libvorbis.

Tried that and got this error:
> 
Building dependency tree       
Reading state information... Done
E: Couldn't find package libvorbis

Edit: do you think this would work in Gutsy?:

[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)[/COLOR]

Many thanks for any advice. :)

---

### Post by Officer Dibble on 2008-06-04
That link I posted solved the problem - but the game messes up my refresh rates and resolution now, and tries to force wide screen for some reason. Ah well... :(

Thanks for your help all. :)

---

### Post by Orlsend on 2008-10-27
Does Anyone knows a .deb file for this?

I hate doing my own installs...

---

### Post by Perfect Storm on 2008-10-27
You'll rarely find any .deb for commercial or freeware games.

---

### Post by curvedinfinity on 2008-10-28
I'm surprised I haven't heard of it before... the wiki says it goes back to MSDOS days. I'll try to give it a shot later.

> Does Anyone knows a .deb file for this?

I hate doing my own installs... 

I made this how to a while back:
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

Its really easy to make a deb if its not very complex.

---


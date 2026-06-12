---
title: "UT2004 - Wont start"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by MikeReiner on 2007-05-10
I have tried...

Running it as root
killall esd
updating it (even updating it AFTER putting the Bonus pack on)
updating video card drivers (i'm using the restricted proprietary ones, and I assume since I can play half-life2, diablo2, GZDoom, and some others with relatively no issues, i'd assume graphics acceleration is working.
 
whenever I try running it from the terminal, it just gives me:
mike@solution:~$ /home/mike/ut2004/System/ut2004-bin



:

Exiting due to error

I'm at a loss here. Last year sometime, I think during 6.10, I ran UT2004 on there without any issue of any kind... just popped the disc in, ran the linux installer, followed the on screen instructions, and all was well...

Specs:
Ubuntu 7.04 Feisty (X-86)
AMD 64 X2 4200+
eVGA nVidia GeForce 7600GT PCI-E
MSI-K8N Neo4-F

I've read around and used the search function, and nothing was of any help to my particular issue. Help would be appreciated! :guitar:

---

### Post by B. Gates on 2007-05-10
Two things:

(a) Have you installed the latest Linux patch for UT2004?

(b) Have you tried running running ut2004-bin via a console so you can see any messages it prints?

---

### Post by MikeReiner on 2007-05-10
A. Yes.
B. By console do you refer to the terminal?.. if so then yes... the terminal just closes immediately.. no message posted.

---

### Post by noerrorsfound on 2007-05-10
> **MikeReiner said:**
> A. Yes.
B. By console do you refer to the terminal?.. if so then yes... the terminal just closes immediately.. no message posted.
He means open a terminal and then start the game from the terminal. I don't have UT 2004 but you can probably start it by typing ut2004 or ut2004-bin.

---

### Post by MikeReiner on 2007-05-10
/home/mike/ut2004/System/ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Cappy on 2007-05-10
Try
```

sudo apt-get install libsdl1.2debian-alsa

```

---

### Post by MikeReiner on 2007-05-10
Thanks to the ever so awesome IRC channel, I have resolved that issue... now comes another. The error I receive now is.. 

mike@solution:/usr/lib$ ~/ut2004/System/ut2004-bin



: 

Exiting due to error


I fail to see how that is even remotely helpful.

I searched around and found that some people had drivers that weren't installed got this error.. but judging by the 10,000 fps i get in glxgears.. i'd say their installed.

---

### Post by Cappy on 2007-05-10
what is the part you left out?

---

### Post by MikeReiner on 2007-05-10
Thats literally what the terminal said. However.. when I closed it, opened it agian, and tried running it, I got the same error as before.. I THOUGHT i fixed it... arhg...

mike@solution:~$ ~/ut2004/System/ut2004-bin
/home/mike/ut2004/System/ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory


I have all the libSDL packages installed.. so i'm at a loss here. The libsdl file is present in the usr/lib directory, same with the ut2004/system directory.. I don't understand.

EDIT: OK, i got the libsdl fixed up.. turns out I accidently copied it from the /ut2004/system directory to the /usr/lib... weird. Anyway.. now I literally get the weird error.

mike@solution:~$ ~/ut2004/System/ut2004-bin



: 

Exiting due to error

---

### Post by buttons on 2007-05-11
> **MikeReiner said:**
> Thats literally what the terminal said. However.. when I closed it, opened it agian, and tried running it, I got the same error as before.. I THOUGHT i fixed it... arhg...

mike@solution:~$ ~/ut2004/System/ut2004-bin
/home/mike/ut2004/System/ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory


I have all the libSDL packages installed.. so i'm at a loss here. The libsdl file is present in the usr/lib directory, same with the ut2004/system directory.. I don't understand.

EDIT: OK, i got the libsdl fixed up.. turns out I accidently copied it from the /ut2004/system directory to the /usr/lib... weird. Anyway.. now I literally get the weird error.

mike@solution:~$ ~/ut2004/System/ut2004-bin



: 

Exiting due to error

Hmm...since you didn't know about copying your libSDL libraries over (a requirement for running it, afaik) I'd wager you didn't put your openal.so in there, either.

But wait, don't get the one from your /usr/lib (libopenal.so.0), get a different one, according to [this post]("http://ubuntuforums.org/showthread.php?t=366789&p=2190048").

Remember, just copy the result into your System folder as openal.so

When I installed UT2k4 recently, the openal.so I had was causing a segfault every time I tried to open it until I did this, so give it a shot and perhaps that's the issue you're having as well.

---

### Post by MikeReiner on 2007-05-11
No affect.

---

### Post by MikeReiner on 2007-05-11
strace report:
[http://paste.ubuntu-nl.org/20293/](http://paste.ubuntu-nl.org/20293/)


Edit- the game starts now, if you look at that strace report, it's sorta obvious...
now to get the sound working.

---


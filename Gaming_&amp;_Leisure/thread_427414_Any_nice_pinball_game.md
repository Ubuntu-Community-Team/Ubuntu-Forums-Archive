---
title: "Any nice pinball game?"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by snowstorm on 2007-04-29
Is there any nice pinball game available on Linux, comparable to the one in Windows?

---

### Post by MonkeyBoy on 2007-04-29
Have you tried Emelia Pinball?  It isn't quite on par with the windows pinball but it has nice physics and a couple of boards.  It is in the repos too so nice and easy to install.

---

### Post by Sicarius99 on 2007-04-29
i'll try that out in like 10 min

---

### Post by disturbedite on 2007-04-29
yeah, that was the one i was gonna mention.  as said before, its not quite as advanced as the one in windows (in some ways) but it does everything i'd like in a pinball game...

---

### Post by Rytron on 2008-03-10
Is there any better pinball game than Emelia for Ubuntu?

Future Pinball was a great pinball game for Windows - it would be great to get a similar game for Ubuntu.

---

### Post by iheartubuntu on 2008-03-10
My high score on the TUX table in Emilia Pinball is 653,350. I was on a good roll, and then my wife interrupted me with some completely unimportant news :| dang! Im still trying to top that score!

I just did a search for more pinball games... try this one called "Roll em Up"...

[http://www.jmurray.id.au/rollem.html](http://www.jmurray.id.au/rollem.html)

[IMG]http://www.happypenguin.org/images/rollemup.jpg[/IMG]

I found this game by searching my fave linux game site.. [http://www.happypenguin.org/](http://www.happypenguin.org/)

and if you are new to linux and dont kow how to install RPM or TAR files, check this out...
[B]
How to Install ANYTHING in Ubuntu![/B]
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by arigram on 2008-03-10
You can also try Future Pinball, which is a Windows program but plays great under Wine.
It is a full 3D pinball engine/construction tool which means that it has dozens of tables created for it, many originals and others recreations.
[http://www.futurepinball.com/](http://www.futurepinball.com/)
See this thread:
[http://ubuntuforums.org/showthread.php?t=591528](http://ubuntuforums.org/showthread.php?t=591528)

---

### Post by iheartubuntu on 2008-03-10
Hey that looks beautiful!

> **arigram said:**
> You can also try Future Pinball, which is a Windows program but plays great under Wine.
It is a pinball engine/construction tool which means that it has dozens of tables created for it, many originals and others recreations.
[http://www.futurepinball.com/](http://www.futurepinball.com/)
See this thread:
[http://ubuntuforums.org/showthread.php?t=591528](http://ubuntuforums.org/showthread.php?t=591528)

---

### Post by iheartubuntu on 2008-03-11
> **arigram said:**
> You can also try Future Pinball, which is a Windows program but plays great under Wine.
It is a full 3D pinball engine/construction tool which means that it has dozens of tables created for it, many originals and others recreations.
[http://www.futurepinball.com/](http://www.futurepinball.com/)
See this thread:
[http://ubuntuforums.org/showthread.php?t=591528](http://ubuntuforums.org/showthread.php?t=591528)

I havent quite got it to work great under Wine yet. Every board I load up looks like it will start up but gets stuck while "compiling script". Any ideas? I played this last night on my dual boot in XP and it is SWEET.

---

### Post by iheartubuntu on 2008-03-11
I did get the game to work GREAT in Ubuntu here using Wine as described in the link below posted by arigram.

[http://ubuntuforums.org/showthread.php?t=591528](http://ubuntuforums.org/showthread.php?t=591528)

Just follow the steps on installing and all should work great! I must say, ALL of the tables are working for me here in Ubuntu, while in XP only about half the tables worked for me. This is an awesome pinball game.

---

### Post by Perfect Storm on 2008-03-11
An Ubuntu 64-bit guide is under construction for Roll em Up to those who want it.

---

### Post by MrBAL on 2009-10-24
It might be abit late but there is Pinball Fantasies an old dos (abandonware) game. It works great in DosBox.

---

### Post by Raffles10 on 2009-11-29
> **Artificial Intelligence said:**
> An Ubuntu 64-bit guide is under construction for Roll em Up to those who want it.

Looking forward to this guide, will it be stickied ? The lack of a good pinball game for linux has always been disappointing. :(

---

### Post by Perfect Storm on 2009-11-29
It doesn't exist anymore. Can't find it anywhere anymore. I might have it on a backup DVD somewhere. If I find it the guide needs to be reworked: [http://gwos.org/doku.php/guides:64bit:rollemup](http://gwos.org/doku.php/guides:64bit:rollemup)
...and maybe CK will host the file.

---

### Post by Perfect Storm on 2009-11-30
Okay, I found the game on my of my backup DVDs. Now we need someone who wants to host it (19.2MB). I'll see to the guide meanwhile.

---

### Post by Perfect Storm on 2009-11-30
Guides now updated and tested (only 64-bit).

[http://gwos.org/doku.php/guides:64bit:rollemup](http://gwos.org/doku.php/guides:64bit:rollemup)


I have set up a temp. download with limit bandweight until someone can host the file permanent.

[[img]http://www.imageviper.com/displayimage/147754/0/Rollemup-pre.png[/img]](http://www.imageviper.com/displayimage/147753/0/Rollemup.png)



enjoy.

---

### Post by Raffles10 on 2009-11-30
I never realized this thread was so old. Thanks for providing the guide and downloads , I followed the guide and it works perfectly. :D

This is certainly the best pinball game I've seen working in Linux. Much appreciated. :p

[[img]http://omploader.org/tMncwZQ[/img]](http://omploader.org/vMncwZQ)

---

### Post by Glucklich on 2009-11-30
Suddenly, I felt like playing Pinball again. I wonder why :P

---

### Post by adrianne on 2009-12-02
great information..... ubuntu linux has good visualization....

---

### Post by booksnmore4you on 2009-12-03
Any idea how to install this on i32?

---

### Post by Perfect Storm on 2009-12-03
> **booksnmore4you said:**
> Any idea how to install this on i32?

sudo apt-get install ia32-libs alien rpm

replaces with

sudo apt-get install alien rpm




sudo cp -r libstdc++.so.2.8.0 /usr/lib32/libstdc++.so.2.8

replaces with

sudo cp -r libstdc++.so.2.8.0 /usr/libstdc++.so.2.8

then try run a ldd on the binary file and see what you're missing.

---

### Post by booksnmore4you on 2009-12-26
Rollemup is hosted in numerous places.  Some links are at [http://www.filewatcher.com/m/Rollemup.tar.gz.20155934.0.0.html](http://www.filewatcher.com/m/Rollemup.tar.gz.20155934.0.0.html) and it is also at [URL="http://www.uberstudent.org/archive/programs/games/Rollemup.tar.gz"]http://www.uberstudent.org/archive/programs/games/Rollemup.tar.gz
[/URL] 
I'm trying to install it on i32 right now....

---

### Post by booksnmore4you on 2009-12-26
It's not a go. :(

Here's the results:

```
build@build-desktop:~$ cd ~/Desktop
build@build-desktop:~/Desktop$ wget ftp://ftp.chg.ru/pub/FreeBSD/ports/distfiles/rpm/i386/fedora/3/compat-libstdc++-8-3.3.4.2.i386.rpm
--2009-12-26 19:38:56--  ftp://ftp.chg.ru/pub/FreeBSD/ports/distfiles/rpm/i386/fedora/3/compat-libstdc++-8-3.3.4.2.i386.rpm
           => `compat-libstdc++-8-3.3.4.2.i386.rpm'
Resolving ftp.chg.ru... 193.233.9.194, 195.178.192.118, 2001:640:20:ff00::194
Connecting to ftp.chg.ru|193.233.9.194|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/FreeBSD/ports/distfiles/rpm/i386/fedora/3 ... done.
==> SIZE compat-libstdc++-8-3.3.4.2.i386.rpm ... 666891
==> PASV ... done.    ==> RETR compat-libstdc++-8-3.3.4.2.i386.rpm ... done.
Length: 666891 (651K)

100%[======================================>] 666,891      139K/s   in 5.4s    

2009-12-26 19:39:05 (121 KB/s) - `compat-libstdc++-8-3.3.4.2.i386.rpm' saved [666891]

build@build-desktop:~/Desktop$ sudo alien -t compat-libstdc++-8-3.3.4.2.i386.rpm
[sudo] password for build: 
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
error: incorrect format: unknown tag
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: compat-libstdc++-8-3.3.4.2.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
compat-libstdc++-8.tgz generated
build@build-desktop:~/Desktop$ tar zxfv compat-libstdc++-8.tgz
./
./usr/
./usr/lib/
./usr/lib/libstdc++-2-libc6.1-1-2.9.0.so
./usr/lib/libg++.so.2.7.2.8
./usr/lib/libstdc++-libc6.2-2.so.3
./usr/lib/libstdc++.so.5
./usr/lib/libstdc++.so.5.0.7
./usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
./usr/lib/libstdc++.so.2.8.0
./usr/lib/libstdc++.so.2.9.dummy
./usr/lib/libstdc++.so.2.7.2.8
build@build-desktop:~/Desktop$ cd usr/lib
build@build-desktop:~/Desktop/usr/lib$ sudo cp -r libstdc++.so.2.8.0 /usr/libstdc++.so.2.8
build@build-desktop:~/Desktop/usr/lib$ sh -c "cd ~/.Games/Rollemup && ./Rollemup" 
./Rollemup: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory
```

Any ideas?

Again, I'm on Karmic, i32.

---

### Post by booksnmore4you on 2010-01-05
bump

---

### Post by zzarko on 2010-11-25
> **booksnmore4you said:**
> bump
I just found out about a thread... :)
You copied the library in /usr/, and it should go in /usr/lib/

BTW, to get the sound in this, if it doesn't play, install alsa-oss package and run the game with aoss ./Rollemup

---

### Post by frostwork on 2010-11-26
I still hope that the futurepinball author opens his sources one day. unfortunately he doesn't seem to reply requests.

vpinball went opensource "recently" [http://sourceforge.net/projects/vpinball/](http://sourceforge.net/projects/vpinball/)
but the source looks very hard to port.

and there's still this quiet unknown "spinball" opengl pinball on
[http://www-graphics.stanford.edu/courses/cs248-videogame-competition/cs248-00/#Spinball](http://www-graphics.stanford.edu/courses/cs248-videogame-competition/cs248-00/#Spinball)
closed source, but worked fine last time I tried.

---

### Post by Rytron on 2010-11-26
Hi frostwork.

How did you link to that part of the page with spinball?

Wait I see now. Can you link to any part of a web page with a #?

> 
and there's still this quiet unknown "spinball" opengl pinball on
[http://www-graphics.stanford.edu/courses/cs248-videogame-competition/cs248-00/#Spinball](http://www-graphics.stanford.edu/courses/cs248-videogame-competition/cs248-00/#Spinball)
closed source, but worked fine last time I tried.

---

### Post by resolv_25 on 2010-12-20
Old post, but interesting one.
I installed Emilia Pinball, quite addictive, most probably because we've played a lot the real pinball years ago.
What's good is ability to shake the pinball, as on real one, and than one can handle this ball for a long time. :D
Fun.

---

### Post by dgerwin11 on 2011-03-19
has anybody found anything current? 2011

---


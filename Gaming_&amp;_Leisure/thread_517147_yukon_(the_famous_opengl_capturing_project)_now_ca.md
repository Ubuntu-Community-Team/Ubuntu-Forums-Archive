---
title: "yukon (the famous opengl capturing project) now captures sound!"
date: 2007-08-04
forum: Gaming &amp; Leisure
---

### Post by wereHamster on 2007-08-04
Yes, it's true! Yukon now captures sound as well :guitar:!

The project is currently undergoing a rewrite and the branch is not as stable as the trunk version, But if you want to capture your favorite game with sound, it may be good enough. I need testers, if you're interested see [http://neopsis.com/projects/yukon/wiki/WikiStart](http://neopsis.com/projects/yukon/wiki/WikiStart) and join our IRC channel (irc://irc.freenode.net/#yukon).

cheers

---

### Post by cor2y on 2007-08-04
I am glad yukon is progressing.

Is it still having trouble (slow frame captures) wiith ATI based cards?

If i'd only known how much ttrouble ATI is in linux i would have bought a Nvida card .

---

### Post by wereHamster on 2007-08-04
I'm sorry but I can't do much for you. Maybe it's not the card but the game or your system setup. Which game are you trying to capture?

---

### Post by luckyd on 2007-08-11
when i try to use it to capture compiz fusion, i get no output..

---

### Post by wereHamster on 2007-08-13
> **luckyd said:**
> when i try to use it to capture compiz fusion, i get no output..

[http://forum.ubuntu-fr.org/viewtopic.php?id=137391](http://forum.ubuntu-fr.org/viewtopic.php?id=137391)

If you don't understand french, just execute:  $ yukon compiz --replace

---

### Post by luckyd on 2007-08-13
I have tried that, then pressed f8 and f8 again to end the video. I still get no output whatsoever. maybe this will help > /usr/bin/compiz.real (Merging configuration from '%s (%s) - %s: %s'
) - Unknown: &#65533;&#65533;&#65533;&#65533;&#65533;
                  &#65533;&#65533;&#65533;&#65533;&#887;&#65533;d
/usr/bin/compiz.real (Merging configuration from '%s (%s) - %s: %s'
) - Unknown: &#65533;&#65533;&#65533;&#65533;&#65533;
                  &#65533;&#65533;&#65533;&#65533;&#887;&#65533;d
/usr/bin/compiz.real (Merging configuration from '%s (%s) - %s: %s'
) - Unknown: &#65533;&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#887;&#65533;d
/usr/bin/compiz.real (Merging configuration from '%s (%s) - %s: %s'
) - Unknown: &#65533;&#65533;&#65533;&#65533;&#285;&#65533;&#65533;&#65533;&#65533;&#887;&#65533;d
/usr/bin/compiz.real (Active configuration (log-level: 134688908):
) - Error: GLIBC_2.1
/usr/bin/compiz.real (   HOTKEY: %s (%s) - %s: %s, FPS: -0.0, INSETS: 134688814/0/0/0
) - Unknown: (null)
/usr/bin/compiz.real (   OUTPUT: %s (%s) - %s: %s, SCALE: 3216808275
) - Unknown: (null)


thats the output of yukon compiz --replace in the terminal, before the normal stuff

---

### Post by wereHamster on 2007-08-14
> **luckyd said:**
> I have tried that, then pressed f8 and f8 again to end the video. I still get no output whatsoever. maybe this will help 

thats the output of yukon compiz --replace in the terminal, before the normal stuff

Are you 'hayden' on freenode? If yes then you have to have a _little_ bit more patience then half hour, people have to sleep from time to time and half hour is definitely not enough!

Seems like compiz and yukon have both a function 'logMessage' and yukon ends up calling the wrong function. Unless you know how to change the yukon source I guess you're out of luck ;)

---

### Post by luckyd on 2007-08-14
ill be more patient, for the sleepers :) im too used to im, irc's laidbackness kind of took me by suprise

---

### Post by wereHamster on 2007-08-16
> **luckyd said:**
> im too used to im, irc's laidbackness kind of took me by suprise

You like IM more than IRC? Here's my jabber ID: [email]wereHamster@swissjabber.ch[/email], though I'm not always on, less that in the IRC channel actually, but with jabber I can send you replies while you are offline and you'll get them immediately after you login the next time.

---

### Post by cor2y on 2007-08-16
sorry
its neverwinter nights native linux.
An Ati x850XT
2gb ddr pc2700 ram
AMD Athlon XP 2800

Last time i used Yukon i raised the problem and it was listed that it was the ATI drivers that resulted in the slow capture frame rate.

---


---
title: "Cedega Help- Q3, JA, SOF"
date: 2006-03-08
forum: Gaming &amp; Leisure
---

### Post by deathbyswiftwind on 2006-03-08
Hey while I know this isnt the cedega forums I have to post here well cause the cedega forums SUCK

Anyways I run quake 3 and jedi academy on cedega. The program is that I cant change the default resolution (640 x 480) without the game crashing to desktop and not saving my settings.

Also I am trying to run soldier of fortune to run under cedega but it just crashes out to desktop after launch if anyone could help me with any of these problems Id really appreciate it!

---

### Post by Duncan_Idaho on 2006-03-08
you can run Quake3 natively, maybe you canchange the resolution that way

---

### Post by leech on 2006-03-09
Quake 3 and Soldier of Fortune have Native versions!

[http://www.tuxgames.com/details.cgi?nc=1141939969&gameref=19](http://www.tuxgames.com/details.cgi?nc=1141939969&gameref=19)

[http://www.tuxgames.com/details.cgi?nc=1141939969&gameref=14](http://www.tuxgames.com/details.cgi?nc=1141939969&gameref=14)

Actually with Quake 3 I think you can just download the Linux Binary and run it natively.

[http://ftp.games.skynet.be/pub/ftp.idsoftware.com/quake3/linux/](http://ftp.games.skynet.be/pub/ftp.idsoftware.com/quake3/linux/)

Leech

---

### Post by cdsboy on 2006-03-09
jedi academy also has a native installer. all of the stuff you are using cedega for  is useless.

---

### Post by deathbyswiftwind on 2006-03-17
Well Ive had alot of trouble with some of it. The linux version of sof is way outdated. Jedi Academy just gave me a bunch of trouble in linux. Kept saying please insert cd 1 into drive or something along the lines and I didnt have sound. And Ive played quake 3 in linux but then you cant get all of the same things for the linux version.

---

### Post by TLE on 2006-03-17
I saw a fix for a similar problem only, offcourse, for an entirely different game. Have a look  [here]("http://cedegawiki.sweetleafstudios.com/wiki/Need_For_Speed_Underground_2") under "Confirmed fix". Maybe, just maybe, you can do something similar, if you can find the correct settings file. Something that might be usefull if you are going to try and search for a file like that, is this command
```
cat *filename*|grep -i *searchword*
```
it'll search the file *filename* (can also be all files in directory *)for the *searchword* e.g. resolution. Best of luck to you

---

### Post by pharcyde on 2006-03-17
Have you tried running either of those games by setting resolution from the command line.  I can't remember the exact syntax but I'm fairly certain there is a way to do something like "quake3.exe -resolution 1024x768".  Just search on google for the exact syntax.

---


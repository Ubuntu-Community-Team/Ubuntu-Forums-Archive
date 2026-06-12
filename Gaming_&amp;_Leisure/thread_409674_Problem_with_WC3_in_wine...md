---
title: "Problem with WC3 in wine.."
date: 2007-04-14
forum: Gaming &amp; Leisure
---

### Post by eitan_a on 2007-04-14
Hey guys, running edgy on a sony vaio laptop.  I run beryl without too many problems and for the most part everything on my laptop works.  I've been trying to get warcraft 3 to play here though but it doesnt work.  I followed instructions in another post about this game.  When I run warcraft 3 with wine my system freezes, I mean completely freezes including mouse and keyboard to the point I need to reboot.  I installed it without any problems and put in the no-cd crack war3.exe.  I "believe" I have a good wine install.  My wine version is 0.9.30-0ubuntu2~edgy1.  I have an intel integrated graphics chip.  I run beryl fulltime.  I dont have problems with sound or video when watching movies, although the sound settings in wine are intense and I dunno how to parse through it.

Is there a way to debug what's going on so that I can figure out what's causing the freeze?

---

### Post by Sammi on 2007-04-14
You can always look at what output it produces when you run it in a terminal. Then again that might be a problem when the system freezes...

---

### Post by MurnShaw on 2007-04-14
Off the top of my head I'm going to say remember to add -opengl to the end of your execution line. And make sure your video drivers are bleeding edge.

Wine is up to 0.9.35 now. Upgrade! It helps.

:-)

---

### Post by cisforcojo on 2007-04-15
DEFINITELY use -opengl if you're not.

example: wine war3.exe -opengl

Also, make sure Beryl is NOT running. I know that it can mess with a lot of 3d apps.

Another recommendation is trying CEDEGA. I had warcraft 3 running -almost- perfectly with CEDEGA.
There were some transparency issues with building units but other than that it was perfect

---

### Post by prowler on 2007-05-07
Same problem here. I have Acer travelmate 2480 series with Intel graphics chip. I got warcraf 3 running 3 or 4 times, but now it freezes. I do use -opengl. Also renamed "Movies" folder. And I installed wine a week ago. I'm using 915resolution to correct to 1280x800. Any sensible explanation or fix ?

edit: this topic has same issues: [http://ubuntuforums.org/showthread.php?t=160501](http://ubuntuforums.org/showthread.php?t=160501)

---


---
title: "Freecraft segfault"
date: 2005-04-24
forum: Gaming &amp; Leisure
---

### Post by spiderworm on 2005-04-24
Hello,

Anybody been having problems with Freecraft?  When I try to run it, a black window comes up that looks like it's about 300 px wide by 200 px high, then it disappears and this error is on the command line:

Fatal signal: Segmentation Fault (SDL Parachute Deployed)

Any ideas what this might be?

System information: [http://hwdb.ubuntu.com/?xml=d196cb6c6324ea0833040a8e68816c7d](http://hwdb.ubuntu.com/?xml=d196cb6c6324ea0833040a8e68816c7d)

Thanx for your help.

spiderworm

---

### Post by Burgundavia on 2005-04-24
The game maybe trying to access /dev/dsp directly. One thing you can try is to 'killall esd' and run it again. After you are done playing the game, 'esd &' at the terminal will restart the daemon. 

Corey

---

### Post by spiderworm on 2005-05-03
That didn't work.  Any other ideas?  Thanx.

spiderworm

---

### Post by ShakingSpirit on 2005-05-04
Can you run any other SDL games? Does 'glxgears' segfault?

---

### Post by spiderworm on 2005-05-05
glxgears doesnt segfault, other sdl games work.  im not sure that all these are sdl games, i know some are.

lbreakout
neverball
egoboo
wenoth
frozen-bubble
armagetron
frozen blob solid
scorched3d

and more.  if it helps, im running on a 64 bit distro here on a laptop, the laptop has a native screen resolution of 1200x800.  just trying to think of things that might be relavent here.  oh also, ive only tried these through kde, not gnome, tho i dont believe that would make a difference.  thanx for your help.

spiderworm

---

### Post by spiderworm on 2005-05-29
* bump *

---

### Post by Gnobody on 2005-05-29
I am having the exact same problem on a 64-bit desktop machine.

---

### Post by spiderworm on 2005-08-11
I should have mentioned, this is a 64 bit desktop as well.  Is there a way to contact the person that built this 64 bit package directly so that we can let him/her know?

spiderworm

---

### Post by rafael-ec on 2005-10-15
I have the same problem with an amd64

---

### Post by manfo on 2005-11-08
Same problem with amd64...

---

### Post by almahtar on 2005-11-20
Same problem, amd64.  We should start a support group, guys!

---

### Post by User Name on 2006-05-10
I am having the same problem too on 5.10, AMD 64.

---

### Post by Deafboy on 2010-05-25
Old topic, but still same problem on 64bit linux (I have arch)

---

### Post by u235sentinel on 2010-05-25
> **Deafboy said:**
> Old topic, but still same problem on 64bit linux (I have arch)

Yeah... I've given up.  I'm running Ubuntu 10.04 and no go.

So I just run the native windows stuff under crossover games.  only way to make it work I guess

---


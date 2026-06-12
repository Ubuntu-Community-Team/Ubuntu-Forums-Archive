---
title: "Pingus and sound"
date: 2005-05-04
forum: Gaming &amp; Leisure
---

### Post by DarkGreen16 on 2005-05-04
I'm trying to run pingus as well as a few other linux based games but I have a problem. As far as games go like frozen-bubble...they work just fine as soon as I start up with sound..same with tuxracer/ppracer. However, with pingus I have to kill esd first before I can hear sound in it. I used to have to do the same for tuxracer and pingus but I no longer have to because I installed a new libesd as was recommended by a tutorial on these forums. Basically...is there anything I can do so pingus will get sound without killing esd?

thx in advance

---

### Post by DarkGreen16 on 2005-05-05
something new i just noticed...

if I run ppracer and then pingus, pingus has sound...but if i don't run ppracer first pingus doesn't have sound...but ppracer of course does.

Pingus is also throwing a ton of errors is this normal?

Error: XMLhelper: Encoding failed: ret: 32 in: 32 out: 32 str: tutorial/basher-tutorial-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 33 in: 33 out: 33 str: tutorial/bomber-tutorial2-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 33 in: 33 out: 33 str: tutorial/digger-tutorial2-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 33 in: 33 out: 33 str: tutorial/floater-tutorial-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 32 in: 32 out: 32 str: tutorial/jumper-tutorial-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 32 in: 32 out: 32 str: tutorial/miner-tutorial2-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow10-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow11-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow12-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow14-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow15-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow16-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow17-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow19-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow20-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow21-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 23 in: 23 out: 23 str: tutorial/snow22-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 22 in: 22 out: 22 str: tutorial/snow7-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 22 in: 22 out: 22 str: tutorial/snow8-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 22 in: 22 out: 22 str: tutorial/snow9-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 31 in: 31 out: 31 str: tutorial/solid-tutorial-grumbel
Error: XMLhelper: Encoding failed: ret: 8 in: 8 out: 8 str: finished
Error: XMLhelper: Encoding failed: ret: 1 in: 1 out: 1 str: 1
Error: XMLhelper: Encoding failed: ret: 11 in: 11 out: 11 str: leveldot_21
Error: XMLhelper: Encoding failed: ret: 1 in: 1 out: 1 str: 1
Error: XMLhelper: Encoding failed: ret: 1 in: 1 out: 1 str: 1
Error: XMLhelper: Encoding failed: ret: 1 in: 1 out: 1 str: 1


and ppracer gives this error

open /dev/sequencer: No such file or directory

how can i fix that?

---

### Post by pacho on 2005-09-05
It isn't normal. This is a bug. Gentoo users, like me, also have this problem but mandriva users, like me ;), don't have this.

On gentoo, look this bug:
[#99942](http://bugs.gentoo.org/show_bug.cgi?id=99942) 

And this:
[#85454](http://bugs.gentoo.org/show_bug.cgi?id=85454) 

How have you installed it?

What parches have been included?

Thanks ;)

---


---
title: "Compiz fusion + nvidia + suspend = Xorg crash"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by MrMunkily on 2007-09-16
Hi all:

I've seen a lot of problems reported about screen corruption and compiz crashes after suspend/resume, but I haven't seen much of anyone reporting Xorg crashes, so I started a thread.         

I've got a Toshiba M200 tablet with a GeForce 5200 MX Running on nvidia binary drivers. Compiz runs quite well, savefor one major issue. Whenever I resume from suspend while running compiz, Xorg crashes and restarts and I'm returned to GDM. 

Xorg dies with:

Caught signal 11.  Server aborting

In the server log, without any additional information.

I've tried the usual nvidia compiz voodoo involving Vsync and nVagp. etc without success. does anyone have any better ideas about how to diagnose this issue?

---

### Post by MrMunkily on 2007-09-16
Worked around - by shutting compiz off on suspend events and restarting.

---

### Post by gzy on 2008-02-25
Hi!
Please share Your compiz / xorg config.
I also have the m200 and can't really run compiz:

1) I'm getting the black window bug (on the lates nvidia drivers)

2) I can stop them if I run compiz with "indirect rendering" setting

3) But if I do that, I can't play video full screen (or even resize movies above their resolution)


Are You running compiz with funny indirect rendering settings?
Did You edit out the 64 mb requirement check?
Can You play video fine?
And finally did You work around the wacom stylus death problem on waking up from suspend / hibernation?

Please be so kind and help out. Love the visual style of compiz, but can't run it due to the above problems

---

### Post by drubin on 2008-02-25
I am also having problems,

My compiz used to work, and now if i run any thing to do with compiz it re-starts my xserver.

So please post solution, 
Thanks

---


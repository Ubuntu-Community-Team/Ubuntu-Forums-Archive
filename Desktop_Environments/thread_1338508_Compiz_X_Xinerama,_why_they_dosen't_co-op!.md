---
title: "Compiz X Xinerama, why they dosen't co-op!"
date: 2009-11-26
forum: Desktop Environments
---

### Post by gutomaia on 2009-11-26
I've never managed to make Compiz and Xinerama working togheter.

I saw in that post ([http://ohioloco.ubuntuforums.org/showthread.php?t=1307897](http://ohioloco.ubuntuforums.org/showthread.php?t=1307897)) that it is possible. I've also saw old 2006 you tube videos showing that, and those were not twinview (app windows were draged from one screem to another).

It's not supported any more?! 

thanks in advance for any help

EDITED: Unfortunelly they really don't co-op in any way. It's a fact. Although you can still use compiz with 2 monitors if you use the twinview ( that makes my screem saver to be at diferrent states on each monitor). Its not the same as xinerama.

---

### Post by scorp123 on 2009-11-26
Depends on your graphics chip I guess? I have Xinerama on my desktop PC (= Nvidia) but not on my laptop (= stupid old Intel GMA 945 chip).

---

### Post by gutomaia on 2009-11-30
> **scorp123 said:**
> Depends on your graphics chip I guess? I have Xinerama on my desktop PC (= Nvidia) but not on my laptop (= stupid old Intel GMA 945 chip).

I have an Nvidia card too... When I try to change for one of the visual efects profiles, a window popup with "the composite extension is not avaiable".

Do you have to make any special config on xorg and compiz to do that?!?

I've search the internet about it.

I found that compiz, the way it is was compiled needs RANDR.

Problem is, RANDR is switched off when xinerama is activated.
(when I open any gtk app ao a terminal it echos: "Xlib:  extension "RANDR" missing on display ":0.0".)

I know that to ran compiz with xinerama I must be able to run campiz without RANDR.

I wanna do that, without having to recompile compiz. (I don't really have time to recompile all that).

Any preset to do that?!? Sorry, for the lack of link references.

---


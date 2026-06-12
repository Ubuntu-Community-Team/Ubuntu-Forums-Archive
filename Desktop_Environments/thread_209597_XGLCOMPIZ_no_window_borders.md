---
title: "XGL\COMPIZ no window borders"
date: 2006-07-05
forum: Desktop Environments
---

### Post by konst88 on 2006-07-05
Hello.
I installed XGL using this guide: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
The ATI drivers are installed and warking correctly.
I chose the 2nd method with creates another session type called XGL, so u may choose which one to run.
After the installation I entered the XGL session, but there was no special effects until I write the line at the end of this guide.
But there were no borders at all in all of the windows..which is not so good...
Can you help me?
Dapper with ATI Radeon 9550.
Thanks.

---

### Post by desperado666 on 2006-07-05
install "gcompizthemer" und install a new window border.
Put this in your session->start up programm
gnome-window-decorator

---

### Post by konst88 on 2006-07-06
thx for the reply.
i installed the package, and chose a new theme, but nothing happened.
gnome-window-decorator says it doesnt exists..
i start the effects using:
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water &
thx for helping me.

---

### Post by PandorsBox on 2006-07-06
[QUOTE=konst88]thx for the reply.
i installed the package, and chose a new theme, but nothing happened.
gnome-window-decorator says it doesnt exists..
i start the effects using:
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water &
thx for helping me.[/QUOTE]

I actually know the answer to this one!  The problem is that compiz is trying to pull your settings from somewhere else (gconf) and they aren't there.  When you include gconf on the line it's ignoring everything else you throw at it.  

Same thing happened to me.  If you install compiz+xgl on a clean installation of Ubuntu it works fine the way you have it. However, for some reason, things get screwy real easy... as you well know.

Toss the "--replace gconf" into the trash and you should be good.

Note: I'm not on linux right now (dual boot system) or I'd be a little more descriptive with exactly what to do.  If you don't figure it out, I'll switch over and be more helpful.

---

### Post by konst88 on 2006-07-06
thx for helping me, but this way, there are no beatiful effects at all.. and the borders arent coming back..

---


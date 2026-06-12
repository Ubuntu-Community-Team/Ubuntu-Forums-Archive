---
title: "Where is the kill applet?"
date: 2012-01-12
forum: Desktop Environments
---

### Post by freebird54 on 2012-01-12
From time to time I will have a program misbehave, or perhaps get misused :) or perhaps get miswritten - and it will freeze up.  There used to be an 'instant kill' you could drop on the top panel that allowed a single click to clean up the mess. Is there some alternative under Unity? Or a way to make it an 'indicator applet'?

Sometimes you just want to KILL something!

---

### Post by mcduck on 2012-01-12
SInce Unity doesn't use Gnome-panel, there of course isn't such gnome-panel applet around any more.

You could make an indicator, but that would be quite complex solution when there are simpler ones around. Just create a launcher instead, point the command to "xkill" and you should have exactly the same functionality the kill applet provided. (and of course you can just add a keyboard shortcut for xkill if you prefer it that way)

---

### Post by lvly36 on 2012-01-12
[COLOR=#000000][FONT=verdana]You have the parent component argument set to null. 
[/FONT][/COLOR]

---

### Post by freebird54 on 2012-01-12
Thanks for the reply.  It made me get off my lazy .... and run a quick check on how a launcher is created in this 'brave new desktop'. The results I came up with are found [ here.]("http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html")

I'll mark it solved, and lurk on the desktop with the launcher loaded...

---

### Post by mcduck on 2012-01-12
> **freebird54 said:**
> Thanks for the reply.  It made me get off my lazy .... and run a quick check on how a launcher is created in this 'brave new desktop'. The results I came up with are found [ here.]("http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html")

I'll mark it solved, and lurk on the desktop with the launcher loaded...

You can actuaklly create one just like in any previous Ubuntu version as the desktop environment you are using is still Gnome (and .desktop files and menu hierarchy is actually XDG stanadard, supported by many different desktop environments and window managers).

So, just using the Alacarte menu editor would do the trick (it appears as "Main Menu" in settings, although I'm not absolutely sure if it's instaleld by default in 11.10 or not.)

---

### Post by freebird54 on 2012-01-12
Actually, neither the alacarte menu nor the right-click access to launcher creation method are available in 11,10 - but the link I put in my previous message describes a way to get it done.

Thanks for the direction! Continue the Happy New Year....

---

### Post by mcduck on 2012-01-12
> **freebird54 said:**
> Actually, neither the alacarte menu nor the right-click access to launcher creation method are available in 11,10 - but the link I put in my previous message describes a way to get it done.

Thanks for the direction! Continue the Happy New Year....

Alacarte sure is available, although it might not be installed by default. [apt:alacarte]("apt:alacarte")

(the right-click launcher creation indeed is not available any more (or yet ;)), most likely because Gnome 3 doesn't use desktop icons by default. The same behavior can easily be replicated using the Templates-menu, though.)

---


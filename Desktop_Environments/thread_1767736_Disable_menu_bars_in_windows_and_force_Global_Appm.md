---
title: "Disable menu bars in windows and force Global Appmenu"
date: 2011-05-26
forum: Desktop Environments
---

### Post by magicalplug on 2011-05-26
I'm using Filezilla in Natty and it keeps bringing up its own menu bar in its own window.

Obviously I want all my applications to only use the top new Global Appmenu Bar. It currently makes Filezilla look ugly and take up additional unwanted screen space.

Libreoffice fixes are all I can find. Does anyone know how to stop an application from using its own menu bar, and force it to only use the Global App Menu?

Can anyone help? Cheers.

---

### Post by mc4man on 2011-05-26
by default, (here), for some reason filezilla's   menu can show both in  the global menu and in it's window or just use the global menu

I think it may be a little bug in filezilla 

TRy this - open filezilla, maximize and close. Then reopen - it should only be using the GM. If you un max it still should only be using the Gm.

If you close un maxed and then re-open it will use both.
So here it must be closed maximized, it then will open maxed and using the GM

---

### Post by magicalplug on 2011-05-26
Ah.

Is there a way to force it to launch maximized at all times, via the launcher?

Or a way to disable the old school menu bars completely. I have no application which uses them under Unity, can't I just remove them so they don't even have the option of appearing?

---

### Post by mc4man on 2011-05-26
Actually today it's behaviour is somewhat inconsistent  - while it appears to always use the GM only  if opened maxed, if seems to sometimes use the Gm only when opened  un maxed, other times it has both.

(So there is some sort of bug with filezilla in this regard

Whatever size you close it at will determine how it opens the following time, by default in unity any window that is 75% or more of the available screensize is automatically maxed when opening

I know of no way to 'turn off' in window menus, the opposite is easy but not what your looking for (turn off the GM

---

### Post by magicalplug on 2011-05-26
I started a thread on the Filezilla forum:

[http://forum.filezilla-project.org/viewtopic.php?f=2&t=20591](http://forum.filezilla-project.org/viewtopic.php?f=2&t=20591)

The admin there says he thinks Ubuntu ships with a global menu exclusion list. I haven't been able to find anything about this on |Google. Given that the program is temperamental in the way it responds to drawing or not drawing its own menus, it does seem more likely at this point that its something about Filezilla itself that is causing the problem.

Does anybody have any other suggestions so I can investigate this further and try and determine was is causing the issue?

---

### Post by magicalplug on 2011-05-26
I've somehow fixed it by disabling certain FileZilla window features, making it more minimal in appearance. It doesn't do it anymore - I've loaded and unloaded it about 20 times straight.

Also, if anyone's interested, here's a FileZilla theme in keeping with Natty's Humanity theme.

With the new minimal appearance, lack of in-window menu bar, and this theme, it looks very pretty :)

---

### Post by mc4man on 2011-05-26
> ships with a global menu exclusion list There is a very small blacklist in the source, filezilla's issue is quite different

I'd just file a bug on, in terminal -  
ubuntu-bug filezilla

At least here, when opening from the unity launcher or dash lens it always works right when opening maxed or opening @ >75% and being auto-maxed. When opening un-maxed it's hit or miss, no real rhyme or reason

If instead opened directly from /usr/share/applications by d. clicking on the filezilla icon it almost always opens wrong (2 menus), even if opening maxed,  though it starts correctly and then the window menu drops down

Starting from the cli also tends to be 2 menus, though not with that little 'drop down' effect.

---


---
title: "What's the Command??"
date: 2009-02-25
forum: General Help
---

### Post by Karl10 on 2009-02-25
Hi All

Former XP user, been running Intrepid for several weeks now, with very little trouble (most of THAT self-inflicted!)  The resources here are phenomenal!!  If you can read and follow directions, you'll probably solve your problem.

Having said that, I'm trying to get several applets to load each time I start up by adding the command in SYSTEM > PREFERENCES > SESSIONS.  Problem is, I have no idea what the command to invoke the screenlet is, or how to go about finding it.

I tried using System Monitor, and it lists several "anonymous" Python apps, but no useful (for me, in this specific case) information.

How can I find the command for a given app?

Karl

---

### Post by dbbolton on 2009-02-25
> **Karl10 said:**
> Hi All

Former XP user, been running Intrepid for several weeks now, with very little trouble (most of THAT self-inflicted!)  The resources here are phenomenal!!  If you can read and follow directions, you'll probably solve your problem.

Having said that, I'm trying to get several applets to load each time I start up by adding the command in SYSTEM > PREFERENCES > SESSIONS.  Problem is, I have no idea what the command to invoke the screenlet is, or how to go about finding it.

I tried using System Monitor, and it lists several "anonymous" Python apps, but no useful (for me, in this specific case) information.

How can I find the command for a given app?

Karl
An easy way is to launch "alacarte", the menu editor for Gnome. You can click on virtually any entry in alacarte, then click "Properties" to see the command.

---

### Post by ibuclaw on 2009-02-25
Are you wanting to run **screenlets**?

If so. the command is
```
screenlets
```
(at least, to my memory, it is)

else:
You probably want to try out what ddbolton had to say :)

Regards
Iain

---

### Post by simeon87 on 2009-02-25
> **dbbolton said:**
> An easy way is to launch "alacarte", the menu editor for Gnome. You can click on virtually any entry in alacarte, then click "Properties" to see the command.

Which can be found at System > Preferences > Main Menu.

---

### Post by mb_webguy on 2009-02-25
If you right-click on a panel, select Add to Panel, and add an applet, that applet should load at startup from then on.  I've very rarely had to do anything with Sessions.

---

### Post by Karl10 on 2009-02-25
All good stuff, but so far no joy.  I'm trying to get four screenlets to load every time I boot up.  They're individually listed in.....

OK, never mind.  I just found it.  There's a checkbox within the Screenlet manager that allows for startup at logon.  Just highlight the applet you want, and check the box.

I've got what I wanted, but I'm still curious as to how to find the command-line command for a given app.  

Karl

---


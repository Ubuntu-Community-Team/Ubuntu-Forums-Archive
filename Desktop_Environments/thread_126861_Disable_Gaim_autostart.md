---
title: "Disable Gaim autostart?"
date: 2006-02-07
forum: Desktop Environments
---

### Post by geo926 on 2006-02-07
Is there a way to disable the auto-start on Gaim? My dad doesn't want it to pop up every time he starts ubuntu!\\:D/

---

### Post by skirkpatrick on 2006-02-07
Two ways.  If it's listed in System->Preferences->Sessions on the Startup Programs tab, delete it.  If not, shut down Gaim then System->Logout, check the box for Save Current Setup, and logout.  If you have that box checked most programs that are running at the time of logging out will auto-start when you log back in.

You could also create a new user for him and let him configure the desktop however he wants :)

---

### Post by geo926 on 2006-02-07
Well It's his laptop, I have my own and my own desktop and he has his own desktop. Thanks for the help!

---

### Post by geo926 on 2006-02-07
Bad news, It's not listed in the start up progs, in fact there aren't any at all!

---

### Post by HokeyFry on 2006-02-07
Wow... I didn't even know GAIM could autostart...

How do you get it to autostart?

---

### Post by byen on 2006-02-07
[QUOTE=geo926]Bad news, It's not listed in the start up progs, in fact there aren't any at all![/QUOTE]
then... as skirkpatrick suggested 
[QUOTE=skirkpatrick]If not, shut down Gaim then System->Logout, check the box for Save Current Setup, and logout[/QUOTE]
That should correct the problem..

---

### Post by byen on 2006-02-07
[QUOTE=HokeyFry]Wow... I didn't even know GAIM could autostart...
How do you get it to autostart?[/QUOTE]
Just open gaim and while it is still running just do >
System->Logout> check the box for Save Current Setup>Logout
This procedure can be used not just for gaim but for most programs that you would want to start during start-up. In this process..whenever you save a session..Ubuntu remembers and saves all the programs that you have running and during system-boot, restores the last saved session.
Hope that helps..goodluck.

---

### Post by HokeyFry on 2006-02-07
thanks byen. and good luck, geo.

---

### Post by geo926 on 2006-02-07
[QUOTE=HokeyFry]thanks byen. and good luck, geo.[/QUOTE]

That worked thanks again guys.

---


---
title: "Unity problem"
date: 2011-06-11
forum: Desktop Environments
---

### Post by HUN73R on 2011-06-11
Hi,
I just installed Ubuntu 11.04 amd64, which comes with Unity.

Unity seems interesting, but still a bit confusing.. ok, just a matter of getting used.

While setting some compiz options (desktop cube), I had to disable some other plugins, even with messages saying something like "unity uses this".

I thought "ok, it won't use it anymore as the functionality is provided be this desktop cube plugin, so it'll be replaced and then back to work". I was wrong.

Now I can't see any border or menus. In other words, I had to move back to windows 7, but I still believe that there's a way to fix my ubuntu.

Does anyone have an advice?


Thanks in advance,
Mauro

---

### Post by VOT Productions on 2011-06-11
Use the compiz options again but enable Window Decorations.

---

### Post by HUN73R on 2011-06-11
Ok, but how can I open compiz options again? I can't click or see any menu.

---

### Post by VOT Productions on 2011-06-11
Press **ALT+F2** then type **ccsm**.

---

### Post by Frogs Hair on 2011-06-11
(If Alt F2 is not working)


When the Ubuntu login opens select your user name . From the session list below the greeter box select recovery console and login  . you will then see a terminal , enter this code and restart```
unity --reset
```Next, when the login screen comes up select Ubuntu from the session list this time. See the link if want to get the cube running in Unity .  [http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/](http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/)

---

### Post by HUN73R on 2011-06-11
I just tried that but nothing happens. All I can see is the wallpaper and the mouse pointer. I tried to switch to tty1, 2, .. Also but got Black screen.

---

### Post by HUN73R on 2011-06-11
Hey, back in the game!

thanks guys for your quick and precise help!!

I could fix it through the recovery console. Just a detail:
unity --reset instead of --repair.


Thanks!

---

### Post by Frogs Hair on 2011-06-11
> **HUN73R said:**
> Hey, back in the game!

thanks guys for your quick and precise help!!

I could fix it through the recovery console. Just a detail:
unity --reset instead of --repair.


Thanks!

Sorry about that , I will fix that in my document . If you use that , remember it will reset to default , so any settings have made will be gone.

---


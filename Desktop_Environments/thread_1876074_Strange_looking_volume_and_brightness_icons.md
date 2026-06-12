---
title: "Strange looking volume and brightness icons?"
date: 2011-11-05
forum: Desktop Environments
---

### Post by tomek_wap on 2011-11-05
Yet another problem ...

As you can see from the image below, both screen brightness and volume on screen "icons" look different to what was initially in Ubuntu 11.10 ... right after reboot, not only the login window has changed, but also the two icons ...

I guess it has something to do with GNOME/Unity shells etc. But can's seem to get it fixed.

On top of that, the sliders do not move while changing the vol or brightness.

Pls help.
Thnx


[IMG]http://photos.lothom.com/foto/vol.jpg[/IMG]

---

### Post by Copper Bezel on 2011-11-06
Yeah, notifications are weird for me, too, under Shell - I'm sometimes getting the classic center pop-up, sometimes notify-osd in the upper right (which I'd prefer), and sometimes the bottom-bar popup. I haven't had the icon change problem, though, and the slider moves appropriately.

Are you using Unity or Shell? And what changed in the login screen?

---

### Post by tomek_wap on 2011-11-06
Shell.
Even the greeter window changed to GNOME I think, for no reason.

Did an upgrade thinking it would fix it all, but no luck.
Made a fresh install - this time 64bit, and using UNITY as GNOME shell seems to brings lots of problems. Also couldn't delete icons from the systray without the command line.

Anyways, strange things were happening in GNOME :)

---

### Post by Copper Bezel on 2011-11-06
Huh. Weird. I wouldn't know where to look with such seemingly unrelated problems. Well, in any case, I hope Unity works out for you! = )

---

### Post by tomek_wap on 2011-11-06
Getting use to it ;-)
Too bad some apps do not work correctly with Unity, i.e. KADU.

Anyways, case closed for now. If anyone knows the solution would be great is he/she shares it for future problem troubleshooting :)

Thnx all!

---

### Post by tomek_wap on 2011-11-10
Found an answer ... 

1. ive installed GNOME Desktop Environment with extra components.
2. uninstalled it
3. and here you have it, few bits and pieces are being left.

now i need to fully reset/uninstall GNOME

GNOME Desktop Environment with extra components seems to be GNOME 3 ... dont like it.

---

### Post by Copper Bezel on 2011-11-10
I'm not certain that I follow. Unity and Gnome Shell are both shells for the Gnome 3 desktop environment in 11.10. Are you saying that just reinstalling the packages solved your problem, or is there something specific you're trying to get rid of?

Incidentally, I noticed that if you are using Shell, it's a good idea to remove notify-osd. It sorts some of the problems with the notifications.

---

### Post by tomek_wap on 2011-11-10
> **Copper Bezel said:**
> I'm not certain that I follow. Unity and Gnome Shell are both shells for the Gnome 3 desktop environment in 11.10. Are you saying that just reinstalling the packages solved your problem, or is there something specific you're trying to get rid of?

Incidentally, I noticed that if you are using Shell, it's a good idea to remove notify-osd. It sorts some of the problems with the notifications.

the notify-osd as shown in screenshots above are from the package i mentioned.
after uninstalling the package some things were leftover in the system, even after logging into gnome classic.

---

### Post by Copper Bezel on 2011-11-10
What sorts of things? Gnome Classic is still Gnome 3. It just uses the Panel in place of Shell. Which "extra components" are you worried about?

Incidentally, notify-osd is a specific package and it's Ubuntu's modified notification bubble at the top right, not the centered one you're seeing above. The notifications were never *broken* for me, though - it was just unpredictable which notify service would be called - so it's probably unrelated to your problem.

---

### Post by tomek_wap on 2011-11-10
After uninstalling the Gnome with extra components, the above volume and brightness were untouched, as well as classic GNOME login panel (like in Ubuntu 10).

And could not get it all back as it was before.

PS. but nevermind for now, I just know not to install that GNOME with extra components in the future, as it just brought me problems.

---


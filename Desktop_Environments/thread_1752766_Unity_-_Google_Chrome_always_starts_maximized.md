---
title: "Unity - Google Chrome always starts maximized"
date: 2011-05-08
forum: Desktop Environments
---

### Post by kingofpain on 2011-05-08
Hey everyone,
I have the latest Natty installed, with Unity running. I installed Google Chrome, put a shortcut in the launcher but, everytime I start it, it starts maximized, which is very annoying.
From my observations, every-other application starts in normal way (un-maximized) except Chrome. I can't seem to find a solution for this. I even tried to change settings for the "Place Windows" Compiz plugin, but nothing happened.
Anyone else has this problem?

---

### Post by kingofpain on 2011-05-10
OMG, no response. Am I the only one that uses Unity and Google Chrome? :shock:

---

### Post by kingofpain on 2011-05-13
Nevermind, I found the solution. I removed Chrome's configuration folder from the ".config" folder.

---

### Post by sikander3786 on 2011-05-13
> **kingofpain said:**
> OMG, no response. Am I the only one that uses Unity and Google Chrome? :shock:
No, there are many who are using both :-)

Glad you got it sorted out.

---

### Post by lenooh on 2011-05-18
I also find it annoying. The same happens with openoffice.

Removing the ~/.config/google-chrome/ directory did not work for me.

Still waiting for a solution...

---

### Post by Demonkunga on 2011-08-24
I'm also looking for a solution to this problem. :\

---

### Post by gukid on 2011-09-02
I've been having this same problem as well.  At one point I had fixed it (or it was patched?) but I recently updated and it's come back.  I've tried deleting the config folder, manually editing the config files and trying to set the window size and position, disabling maximize for google-chrome in compiz-config... pretty much everything I can think of.  Wish it would just work the way I expect it.

---

### Post by gukid on 2011-09-02
Found it:
[http://askubuntu.com/questions/35011/why-do-firefox-4-and-evolution-always-open-maximized-in-unity](http://askubuntu.com/questions/35011/why-do-firefox-4-and-evolution-always-open-maximized-in-unity)

This is why it happens.  Gotta size your window a little smaller.

---

### Post by jasonhartley on 2012-03-13
[http://askubuntu.com/questions/40571/how-to-keep-programs-from-launching-maximized](http://askubuntu.com/questions/40571/how-to-keep-programs-from-launching-maximized)

In 11.10:

Install ccsm (CompizConfig Settings Manager)
Run ccsm
Click Desktop
Click Ubuntu Unity Plugin
Click Experimental tab
Change Automaximize value from 75 (default) to 100

---


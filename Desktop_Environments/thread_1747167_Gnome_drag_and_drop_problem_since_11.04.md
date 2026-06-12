---
title: "Gnome drag and drop problem since 11.04"
date: 2011-05-02
forum: Desktop Environments
---

### Post by ggdagg on 2011-05-02
Hi, 

I meet a problem with the drag and drop function with Gnome (v.2.32.1) with Ubuntu 11.04. In fact I can't use the drag and drop between windows (such as drag a music and drop it in Totem, drag a file from window and drop it in a other window...)
This is a new installation (no update from last version) and all is updated !

Have you an idea ?
Thanks for your answers !

---

### Post by lucaskatayama on 2011-05-06
Yes... i'm having the same problem.

when i try to drag and drop text to eclipse the windows don't switch.

I need to put windows side by side and then drag and drop.

Solution?

---

### Post by ggdagg on 2011-05-07
Hi, 

I found [this page]("http://ubuntuforums.org/showthread.php?t=1744134") about a same problem and it's a compiz bug.

[inameiname]("http://ubuntuforums.org/member.php?u=949055") say :

> I figured out that if you type in the terminal the following, this gets  fixed. I do not know what it does not do it at default, or why you have  to in the first place. My guess is because the old desktop and compiz is  set to Unity. 

compiz --replace & exit

Seems to work thus far, but every time you restart or log out and log  back in, it is needed once again. I guess if added in a script in  startup applications it will work every time the computer logs in. I  will have to try that.

And of course it's working better without compiz !

---


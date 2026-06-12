---
title: "Computer freezes when updating ?"
date: 2009-08-19
forum: Desktop Environments
---

### Post by vaerer on 2009-08-19
When I update or install new programs my CPU usage goes up to maximum and all my other programs freeze.

Is there a way to stop the update program from using the maximum amount of CPU?

I don't really care if the update or installation takes 5 or 10 times longer.

I just want to be able to do other things while the computer is being updated! :confused:

---

### Post by Penguin Guy on 2009-08-26
There is a handy program available in the repositories called cpulimit, this allows you to limit the cpu usage of a selected program. To install it; click [[COLOR="Blue"]here[/COLOR]]("apt:cpulimit") or run [COLOR="Green"]sudo apt-get install cpulimit[/COLOR]. You can then limit it to 50% CPU by running [COLOR="Green"]cpulimit -e apt -l 50[/COLOR] during the update (if that doesn't work, post back here).

---


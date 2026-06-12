---
title: "Jaunty:  Emerald is not starting automatically but DOES work"
date: 2009-04-27
forum: Desktop Environments
---

### Post by WindowsSurvivor on 2009-04-27
SOLVED!  See solution below :)  Thanks for your help!!
---------------------------------------------------------
Hello folks!

I Upgraded to Jaunty a few days ago and I've only had some small problems, most of which I was able to either resolve or get around by myself... but frankly, this one has me stumped.

OK so Emerald works just fine, but it's not loading automatically! It was working before the Jaunty upgrade, it's in the startup application list (emerald --replace) but it just doesn't load automatically.

So when I start up the computer, I use Alt+F2 and type "emerald --replace" (the exact same thing in the start up application entry) and it loads just fine.

Help!!?

---

### Post by mcduck on 2009-04-27
Instead of adding Emerald to your startup applications you should just configure Compiz to use Emerald as it's decorator by default.

It doesn't really make much sense to first load GWD and then replace it with Emerald when you could just load the correct decorator i the first place. ;)

Open CompizConfig Settings Manager, then go to Window Decoration-plugins settings and change the "Command"-field to "/usr/bin/emerald".

---

### Post by WindowsSurvivor on 2009-04-28
Bingo!!  Thank you :)  *SOLVED*

---


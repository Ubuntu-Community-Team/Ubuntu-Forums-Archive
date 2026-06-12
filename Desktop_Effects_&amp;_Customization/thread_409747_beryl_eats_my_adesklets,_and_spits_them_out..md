---
title: "beryl eats my adesklets, and spits them out."
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by shane2peru on 2007-04-14
Ok, I have Fiesty up-to-date installed.  I upgraded from Edgy (Ubuntu CE).  I have used adesklets for a while.  I later realized that beryl is in the repos, and wanting to give it a try, I installed it.  Works great.  Now however my adesklets display very inconsistently.  Attached is a screen shot of how they are displaying the one in the top right corner looks normal.  The other two are obviously messed up.  I know this is a problem with beryl, because when I disable beryl, my adesklets display correctly.  Does anyone have any ideas about this?  Thanks.

Shane

---

### Post by rollps on 2007-05-24
hi

i have the same problem with adesklets and beryl...
i'm running xubuntu festy, and was the same with edgy

i found this solution :
-create a script to launch beryl AND emerald with a delay, so the command is "sleep 3" (3 seconds)
-make those scripts auto launch on ubuntu or xubuntu
-this way adesklets will launch before beryl and emerald... and the trick is done !

i have a new problem now though !! :(
on festy, adesklets are displayed properly but always stay on top of all other windows...

any ideas why ?

thanks

---

### Post by frodon on 2007-05-24
Use screenlets instead, they are made to work with beryl/compiz ;) :
[http://compiz.org/Desktop_Screenlets](http://compiz.org/Desktop_Screenlets)

---

### Post by rollps on 2007-05-24
i could for sure, but don't do what i want for the moment... (like the volume bar)

and i'm sure it's easy to fix, cause they only stay on top, it's a matter of finding the good option in beryl settings....
and was okay in edgy with same programs

---

### Post by shane2peru on 2007-05-24
> **rollps said:**
> i could for sure, but don't do what i want for the moment... (like the volume bar)

and i'm sure it's easy to fix, cause they only stay on top, it's a matter of finding the good option in beryl settings....
and was okay in edgy with same programs

I too semi found a solution.  I start have a script called .startupscript that sets in my home folder it looks like this:  ```

#!/bin/sh
#beryl-manager
#sleep 4
/usr/bin/gdesklets start
#sleep 2
#/usr/bin/adesklets --nautilus
#sleep 2
#/usr/bin/adesklets --nautilus
#sleep 1
#/usr/bin/adesklets --nautilus
#sleep 1
#/usr/bin/adesklets --nautilus
/usr/local/bin/gyachi
/usr/bin/gaim
#Ok, this is the end of my script.

```
I foudn that starting adesklets various times would eventually get it to look right.  I have commented everything out now, because I quit using Beryl, too many minor problems, and slows the system down.  I use it to show off the desktop, but not on a daily basis.  I also went back to gdesklets.  I don't know how or if it works with beryl correctly.  Thanks for the input though, good idea to start adesklets first then beryl.  There is probably a setting on adesklets that you can change to not be on top of all windows try looking at: ```
gedit /home/**username**/.adesklets
```  You may find a setting in there to tweak.  Maybe you should back that file up before playing with it though.

Shane

---


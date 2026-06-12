---
title: "Yet Another Compiz Help Question"
date: 2006-07-29
forum: Desktop Environments
---

### Post by vangheem on 2006-07-29
ALright, after way too much trouble I still can't get compiz to run.

I have XGL installed and working.  I just can't get compiz to run.

Here is my output when running compiz script 
> cgwd: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

[1]+  Done                    /opt/compiz


Here is what the script looks like.
> #!/bin/sh
cgwd &
compiz --replace gconf &


I've googled forever and haven't found anything that helps...  

Any ideas?

---

### Post by Dr. Nick on 2006-07-29
what script is that? (which howto did you use)

Have you tried running 

cgwd --replace 

command from a terminal

---

### Post by vangheem on 2006-07-29
I got the script from here [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz")

When I try running "cgwd --replace" I get this error,
> ** (cgwd:15091): WARNING **: Cannot open pixmap


---

### Post by vangheem on 2006-07-29
Specs:
AMD Athlon 64 3000+
Nvidia 7600GT
Ubuntu Dapper Drake 32bit version

---

### Post by Dr. Nick on 2006-07-29
never used that method :-/

I got mine working using this thread
[http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+rule](http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+rule)

I use the compiz-start.py script mentioned on
[http://www.compiz.net/viewtopic.php?pid=11734](http://www.compiz.net/viewtopic.php?pid=11734) which is linked in that thread to get mine going. I had a few problems with cgwd yesterday,

If you look in synaptic what version of compiz do you have, plain compiz or something like "compiz vanilla"

---

### Post by vangheem on 2006-07-29
I have regular compiz install not the compiz-vanilla package.

I looked over those threads and tried using the start-compiz.py script but it still won't work.  In fact after tweaking some things and adding: ```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```
to my xorg.conf file the gnome session crashes when trying to start compiz with the python script.

---

### Post by Dr. Nick on 2006-07-29
weird, not sure exactly what causes that, Im not a compiz whiz by any means but I have noticed they are changing alot lately, Ive had to reconfigure mine to keep up as updates messed it up. Maybe it will get more stable soon

Hopefully someone can help you more.

---

### Post by vangheem on 2006-07-29
Alright, I figured it out...  The problem was that I was didn't install the right nvidia drivers.  I installed them myself instead of from the repo.  I didn't think that it would matter.

Anyways, sorry for wasting your time.  I appreciate you trying to help though.

Thanks

---


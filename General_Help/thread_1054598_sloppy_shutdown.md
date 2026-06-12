---
title: "sloppy shutdown"
date: 2009-01-29
forum: General Help
---

### Post by gnomeout on 2009-01-29
So basically, Intrepid has disappointed me. Because, when I was on Hardy, I would click shut down or restart and everything should shut down nice and orderly. However on intrepid, it just kills everything. 

This mostly doesn't affect me, but one thing that gets on my nerves as a result is Amarok. 

Because it never quits properly the exact same playlist appears every time it opens from the last time it was PROPERLY exited. This is annoying when it's not working the way it should. 

So I figured in the true spirit of open source I would take matters into my own hands and write my own shutdown script that exits amarok properly, but this is proving difficult because I thought the appropriate signal to end a program properly is SIGTERM, but this is apparently the same signal that `killall` sends by default, which does NOT shut things down properly. I tried some other signals like STOP and QUIT to no avail. I also tried killall --wait which was not what I wanted either. But according to the internet and friends, most programs "catch" the SIGTERM signal and thats when they do all the stuff to prepare for exit. does amarok not do this(anymore)? The reason I explain all of this is because now I cant tell if the problem is with amarok or the shutdown scripts, or both??? also, killall never ends a program normally, but it sends sigterm which should? I am so confused on this.

SO
I am looking for any solution to my aforementioned problem specifically with amarok.

Even if someone could tell me the proper shell command to end a program smoothly would be a good start. even better if someone could tell me exactly how to write it. even better if someone could tell me how to apply it to all user processes without tonnes of code.

and best of all would be to just make the shutdown go back to the way it was before!(and as mentioned this could all be an amarok problem in which case Id like a fix for that)

---

### Post by blauer-affe on 2009-02-15
same problem... 
i already started a thread before i found this one
([http://ubuntuforums.org/showthread.php?t=1070596](http://ubuntuforums.org/showthread.php?t=1070596))

is this a common problem? i cant believe that this behaviour is intended!

i've also tryed many commands (my target was gedit since it asks weather you want to save when quit and is a gnome program witch should catch term msgs) but none worked it never askes to save when i use a command but always does when i choose file > quit...

plz let me know if you make any progress...
and anyone else plz tell me if your system behaves in the same way!

---

### Post by blauer-affe on 2009-02-15
for amarok i found a command witch seems to work:
```
dcop amarok MainApplication-Interface quit
```

this should work on all kde apps, but i still would like all (gnome) programs to be quit this way on shutdown...

---

### Post by blauer-affe on 2009-02-17
wrote a little script for a shutdown that closes programs more kindly:
[http://ubuntuforums.org/showthread.php?p=6748723#post6748723](http://ubuntuforums.org/showthread.php?p=6748723#post6748723)

---

### Post by gnomeout on 2009-02-23
thanks, this looks very promising. I want to try putting it right into my shutdown scripts, might get a little tricky and take some time though and im just too busy for the next week or 2.

I will post detailed instructions if i can, and if i remember.

---


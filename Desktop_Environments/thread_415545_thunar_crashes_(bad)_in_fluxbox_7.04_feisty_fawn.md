---
title: "thunar crashes (bad) in fluxbox 7.04 feisty fawn"
date: 2007-04-20
forum: Desktop Environments
---

### Post by key on 2007-04-20
Hi All,

Anyone out there running fluxbox in Fiesty fawn? If so, are you using the thunar file manager successfully?
 
When I (try to) run thunar in fluxbox, CPU usage goes through the roof and the machine hangs. I can't even login remotely over ssh and kill the process - it is totally dead.  I wrote a little bash script to run thunar for 10 seconds and then kill it (to try to get some error messages), but even then the machine is totally locked. No error messages or anything. Thunar works great in XFCE4, works fine in KDE. 

I deleted my .fluxbox directory and it still hangs, so it isn't some configuration there. Really weird. 

Anyone else had this issue?

---

### Post by RedSquirrel on 2007-04-20
I've had that issue with Fluxbox and Thunar in edgy from time to time. Not sure if it's an official bug; guess I should check that.

In any case, I just remove the Thunar configuration (after a reboot :( ) and then it's OK again:

```
rm -fr ~/.config/Thunar
```It seems to me that it happened on my box after I was switching themes. Perhaps Thunar got confused by all of that. It might also have been caused by having Fluxbox remember the window size and/or position of the Thunar window.

Hasn't crashed lately...

---

### Post by key on 2007-04-21
Thanks RedSquirrel, 
Deleting the thunar config file  did the trick. 
I am happily fluxboxing with thunar again.

---

### Post by RedSquirrel on 2007-04-21
No problem. Happy fluxboxing! :)

---

### Post by Jmtan on 2007-04-24
Thanks for the tip, it helped me a lot too.
Thunar + fluxbox seems to crash in the same way as the first poster whenever I set location selector to "toolbar style", then restart thunar. Other settings don't seem to have any ill-effects.

I'm sure this issue will get resolved soon :). I only just encountered it after upgrading today.

---

### Post by key on 2007-04-24
I never could track down what was causing the issue - for me it seems that every time I changed from XFCE to fluxbox the crash would happen. Maybe I set the view to "toolbar style" while I am in XFCE. Seems likely. 

It also seems that the ctrl-alt-backspace combo will successfully free the machine. 
In case anyone else encounters this problem, all hope of a safe shutdown is not lost. 

I put an  "rm -rf ~/.config/Thunar" bash script in my ~/.fluxbox/startup . That way there are no crash worries. 
For those foolish enough to do the same, proceed with caution when automatically rm -rf-ing your stuff. You could probably just delete the thunarrc file, haven't tried it.

---

### Post by RedSquirrel on 2007-04-24
> **key said:**
> I never could track down what was causing the issue - for me it seems that every time I changed from XFCE to fluxbox the crash would happen. Maybe I set the view to "toolbar style" while I am in XFCE. Seems likely. 

I have used the "toolbar style" for a while and Thunar has been stable, but this is with edgy's Thunar and Fluxbox 1.0rc3 svn 4855.


> 
It also seems that the ctrl-alt-backspace combo will successfully free the machine. 
In case anyone else encounters this problem, all hope of a safe shutdown is not lost. That's good. On my machine there was a total lockup and only a hardboot would fix it. Hurray for ext3 journal! 


> 
I put an  "rm -rf ~/.config/Thunar" bash script in my ~/.fluxbox/startup . That way there are no crash worries. 
For those foolish enough to do the same, proceed with caution when automatically rm -rf-ing your stuff. That's a neat idea. Another possibility would be to remove it only when you run Thunar (using a script or possibly even an alias). Whatever works. :)

> 
You could probably just delete the thunarrc file, haven't tried it.Neither have I. Post back if you do try that. I've just been removing the whole directory to make things squeeky clean. :lol:

---


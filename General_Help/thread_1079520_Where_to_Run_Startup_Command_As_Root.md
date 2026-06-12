---
title: "Where to Run Startup Command As Root"
date: 2009-02-24
forum: General Help
---

### Post by idrailgag on 2009-02-24
I would like to be able to run a command as root on startup, but only after compiz has already started.  Is this even possible?  I tried putting it in rc.local, no such luck.  Any other ideas?


In case you're curious the command I am trying to use is
   [FONT="Courier New"]pidof compiz.real | xargs renice -5[/FONT]
I recently figured out that if I up the priority of compiz.real, then my interface remain smooth, even when my computer is bogged down.  Some may think this is stupid, but I know what my priorities are ;).

---

### Post by Wayne_V on 2009-02-24
Why not put it in your .profile so it gets executed on login?

---

### Post by idrailgag on 2009-02-24
Haven't tried that yet, but I am guessing that .profile does not run as root.  The command I trying to run has to be sudo

---

### Post by SuperSonic4 on 2009-02-24
Why not make a script and put it in your profile?

```
# !/bin/bash
sudo pidof compiz.real | xargs renice -5
```

---

### Post by Wayne_V on 2009-02-24
I'm not running compiz - but does it even start before someone logs in?   Do a 
"ps -efa | grep compiz" when logged in and see who  owns it.   Put a line in rc.local like

ps -efa | grep compiz > /tmp/compiz.pid

and then check /tmp/compiz.pid after booting to see if it is even there.

---

### Post by idrailgag on 2009-02-24
I just looked at ~/.profile.  That only runs when you start a terminal.  Not the right place for sure.

---

### Post by Wayne_V on 2009-02-24
.profile does get sourced on login -- a login shell is created to fire everything else off.

Add this to your .profile:

echo "HIT! `date`" >> ~/PROFILE

and you will see it.

---


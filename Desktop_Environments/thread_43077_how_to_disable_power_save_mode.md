---
title: "how to disable power save mode?"
date: 2005-06-20
forum: Desktop Environments
---

### Post by blicurse on 2005-06-20
Hi all, new to ubuntu here. 

I installed on an old P2 and so far everthing has gone pretty smooth, except that when i leave the machine it eventually goes into some sort of a hibernate/power save mode.   When i return to the machine i'm unable to revive it without rebooting.  Any tips? can I just disable this feature?

---

### Post by Alexander Kirillov on 2005-06-21
[QUOTE=blicurse]Hi all, new to ubuntu here. 

I installed on an old P2 and so far everthing has gone pretty smooth, except that when i leave the machine it eventually goes into some sort of a hibernate/power save mode.   When i return to the machine i'm unable to revive it without rebooting.  Any tips? can I just disable this feature?[/QUOTE]
 There shouldn't be any hibernation by default. The only "powersave" I am aware of which is on by default is turning the monitor off and it can be overriden by using dpms option in xorg.conf (do not remember precise syntax). 


Anything is system logs? 
/var/log/system

---

### Post by blicurse on 2005-06-21
well hibernate wasn't the right word, since i guess that implies that the machine turns off, which it doesn't.  the monitor just seems to get no signal when the machine is left alone for about 20 minutes or so.  

when i return, i move the mouse around or hit the keyboard and nothing happens.  is there a specific keystroke or combo that i could hit to restore the monitor.  I'd rather not disable to feature entirely, if i don't have to.

---

### Post by Alexander Kirillov on 2005-06-21
[QUOTE=blicurse]well hibernate wasn't the right word, since i guess that implies that the machine turns off, which it doesn't.  the monitor just seems to get no signal when the machine is left alone for about 20 minutes or so.  

when i return, i move the mouse around or hit the keyboard and nothing happens.  is there a specific keystroke or combo that i could hit to restore the monitor.  I'd rather not disable to feature entirely, if i don't have to.[/QUOTE]
 Obviously, it is not supposed to be this way - the monitor should wake up on any key press or mouse movement. So there is no special key I know of. 

Maybe a problem withe videocard/monitor, but I do not think I can help. Try filing a bug in bugzilla.

---

### Post by slow learner on 2005-09-10
[QUOTE=blicurse]Hi all, new to ubuntu here. 

I installed on an old P2 and so far everthing has gone pretty smooth, except that when i leave the machine it eventually goes into some sort of a hibernate/power save mode.   When i return to the machine i'm unable to revive it without rebooting.  Any tips? can I just disable this feature?[/QUOTE]
 I have the same problem with ubuntu not responding after approx 20mins. I have searched the forum for a solution without success.

Does anyone know hot to modify - or where the settings are in ubuntu for hibernation, monitor power, suspend etc?

thanks for any help

---

### Post by sbooth on 2005-10-20
I have the same problem too... on a dual xeon with a MoBo that I know doesn't support powersaving.

Any answers? :-)

---

### Post by AllenGG on 2005-10-20
Both have the same problem !!

This appears to be a BIOS problem, not software.
If you don't know how to set up yopur BIOS take it to a tech, looked at many BIOS systems, no 2 the same.
Allen

---


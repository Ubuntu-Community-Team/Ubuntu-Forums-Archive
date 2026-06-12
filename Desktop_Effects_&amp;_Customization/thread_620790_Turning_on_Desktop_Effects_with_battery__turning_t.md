---
title: "Turning on Desktop Effects with battery / turning them off with power"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by SleepWalkerX on 2007-11-23
I'm on a notebook running gutsy.  I'm trying to set it to where compiz starts when the ac power is plugged in and metacity replaces it when its just running off of the battery.

I made two scripts in /etc/acpi/events.  

/etc/acpi/events/compiz

event=ac_adapter
action="/usr/bin/metacity --replace"

/etc/acpi/events/metacity

event=battery
action="/usr/bin/compiz --replace"

(and of course run /etc/init.d/acpid restart so i'm able to start using them)

It almost works well.  Sometimes it'll just immediately start metacity when I disconnect my power cable, but sometimes it'll just stay in battery mode and sit there if i plug back in the power (and not start compiz).  

I think I might know what the problem is.  If you normally run the command "compiz --replace" in the terminal it'll replace metacity, but the command will sit there in the terminal and not completely end.  Same with "metacity --replace".  

Has anyone accomplished what I'm trying to do or have any suggestions?

---

### Post by RSingh on 2007-11-23
A nice idea, help anyone..

---

### Post by SleepWalkerX on 2007-11-25
Anyone?

---

### Post by FuturePilot on 2007-11-25
Try adding a & to the end like this
```
action="/usr/bin/metacity --replace &"
```
That will basically background the process so that it can continue with the rest.
Same for the Compiz command as well.

---

### Post by SleepWalkerX on 2007-12-01
It still doesn't work well.  I guess I'll just request this through launchpad.

---


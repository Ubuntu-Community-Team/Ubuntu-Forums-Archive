---
title: "internal beeping issue"
date: 2009-04-29
forum: General Help
---

### Post by Dayofswords on 2009-04-29
when every i do something with my key board that the computer cant do, like hit right when theres no right in a text box, the computer makes an internal beep, not from speakers.

this isnt really stopping me from doing things, but it a bit annoying

there is also 3 beeps when the comuter turns off, is that normal?

i have 
2 partions, one xp, one ubuntu 9.04
optiplex ???? computer

---

### Post by spiderbatdad on 2009-04-29
you can turn this off by editting the file /etc/modprobe.b/blacklist.conf and at the end of the file add the line
blacklist pcspkr
the next time you log in it will take effect.

---

### Post by bgs100 on 2009-04-29
> **dayofswords said:**
> when every i do something with my key board that the computer cant do, like hit right when theres no right in a text box, the computer makes an internal beep, not from speakers.

this isnt really stopping me from doing things, but it a bit annoying

there is also 3 beeps when the comuter turns off, is that normal?

i have 
2 partions, one xp, one ubuntu 9.04
optiplex ???? computer

Yes, it is normal for the computer to beep when it shuts down.

This is simply the system beep, and there is a way to turn it off, if you really want

Go to System->Preferences->Sound, go to the "Sound" tab, and uncheck "Play alert sound"

You can also, rather than a beep, make the window (or screen) flash by enabling "Visual Alert"

---

### Post by freonchill on 2009-04-29
there was another thread a couple of days ago regarding the shutdown 2-4 time beep. i tried the 3 options and ended up having to do the modprobe thing, as the other options did not fix it.

---

### Post by spiderbatdad on 2009-04-29
> **freonchill said:**
> there was another thread a couple of days ago regarding the shutdown 2-4 time beep. i tried the 3 options and ended up having to do the modprobe thing, as the other options did not fix it.

seems to be fixed now...after update and works as described by bgs100

EDIT: not at shut apparently.

---


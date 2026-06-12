---
title: "Chnage power management mode from script"
date: 2011-05-21
forum: Desktop Environments
---

### Post by brdmn on 2011-05-21
I use a little script to run vlc:
```

#!/bin/bash
xset -dpms
vlc -f $* vlc://quit
xset +dpms

```

Since the Natty release, I've configured xfce4-power-manager to suspend my system after 20 mins, and unfortunately, this happens even if vlc is currently playing.  Is it possible to add something to my script that would change the mode to "Presentation" in xfce4-power-manager at the beginning of the script, and back to "Normal" after vlc is done?

Many thanks in advance for any suggestions and comments!

---

### Post by brdmn on 2011-05-27
OK, so I've figured out that I can add "pm-suspend" to my script to force a suspend after vlc is done.  But is there a way for me to change the mode to "presentation" in xfce4-power-manager at the beginning of the script?

---

### Post by brdmn on 2011-05-27
OK, I think I've solved my problem.  If you are interested, it's a matter of adding:
```
xfce4-power-manager --quit
```
at the beginning of the script and:
```
xfce4-power-manager
```
without any options at the end of the script.  Straightforward.

---

### Post by brdmn on 2011-05-28
Or so I thought.  After xfce4-power-manager restarts, suspend no longer works, i.e., the computer remains on and does not suspend after the timer.  When I check the settings, though, it still shows the "Put the computer to sleep" option as selected, it just doesn't do it.  Manually suspending does work.

Anyone?

---

### Post by Kognit on 2011-07-25
> **brdmn said:**
> Or so I thought.  After xfce4-power-manager restarts, suspend no longer works, i.e., the computer remains on and does not suspend after the timer.  When I check the settings, though, it still shows the "Put the computer to sleep" option as selected, it just doesn't do it.  Manually suspending does work.

Anyone?

Try:
```
xfce4-power-manager & disown
```

at the end.

---

### Post by brdmn on 2011-07-28
Awesome, that works, and now I've also learned a new bash command, thanks Kognit!

Further update: Nope.  It's inconsistent.  I tried the script again, and this time, it didn't suspend after 20 mins, even though the settings have not changed, and xfce4-power-manager is running under the init process.

---


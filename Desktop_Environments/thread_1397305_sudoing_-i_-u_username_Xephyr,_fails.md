---
title: "sudoing -i -u username Xephyr, fails"
date: 2010-02-03
forum: Desktop Environments
---

### Post by multiple on 2010-02-03
My goal - run another desktop environment as another user in Xephyr,

Everything works fine when i as local user run the command ```
xinit ~/.xinitrc-fvwmtst -- /usr/bin/Xephyr :3
```, but when i want to sudo it to another user ```
 sudo -i -u fvwmusr xinit /home/fvwmusr/.xinitrc-fvwmtst -- /usr/bin/Xephyr :4
``` i got thiws message :
Invalid MIT-MAGIC-COOKIE-1 key
Xephyr cannot open host display. Is DISPLAY set?
giving up.

I have tried login as the user i want to sudo and then run the command locally.
```

peter@multi:~$ sux fvwmusr
Password:
xinit /home/fvwmusr/.xinitrc-fvwmtst -- /usr/bin/Xephyr :5

``` (i use sux because it's an X-app)
then everything works fine.

I have checked the /tnp/.X?-lock and justified the displaynumbers to match unused values.
I have the habit to increase the display-parameter with one just to avoid problem with the lock-files.

/multiple

(i think i put this post in wrong category - maybe i should hqve put it in general help, if so - please move the thread to its right place)

---


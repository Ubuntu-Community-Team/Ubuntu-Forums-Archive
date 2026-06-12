---
title: "Cannot login to KDE4 ... KDE3 ok"
date: 2008-06-27
forum: Desktop Environments
---

### Post by PhilippeP on 2008-06-27
Hi

Currently under KDE4.1b2 but the situation appeared before the upgrade from b1 to b2.

when I choose KDE4 at the session login, things go reallllly slow, the nice
looking background of b2 appears , then in the splashscreen, the HD
icon for about 45secs, then the Settings icon for 3 to 4 minutes ...
then back to the blue kdm backgound, the mouse cursor and that's it ...

I've tried enabling the kdm debug option : the screen goes black, with a blinking cursor on the top left ... freeze

Any idea what's going on ?? how to debug this ?

---

### Post by PhilippeP on 2008-07-02
Ok I found the answer in */home/mylogin/.xsession_errors*

It mentionned a command not found (*run_parts*) from the script */etc/X11/Xsessions.d/30xorg-commons*
It was a typo, the correct command name is *run-parts* ....

I did not touch this file before and it is installed with the *xinit* package ...

I corrected it , and voilà , it works ...

---


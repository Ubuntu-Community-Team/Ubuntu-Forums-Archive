---
title: "Making conky run properly"
date: 2006-02-18
forum: Desktop Environments
---

### Post by daacosta on 2006-02-18
I haven't been able to...

I used this:

System -> Preferences -> Sessions -> Start Up Programs

I then proceeded to Add and then typed the command conky.

There was a 50 in there perhaps indicating when the program is to be started...

Anyway, when I rebooted I saw conky starting but then the rest of the desktop items overwhelmed it and buried it (i.e., conky was running behind my beautifull wall paper...)

What am I doing wrong and how to fix it?

Regards,


-D-

:cry:

---

### Post by taurus on 2006-02-18
The reason you can't see conky running because you are using Gnome with nautilus!!!  Here is a link for you to fix that...

[http://conky.sourceforge.net/gnome.html](http://conky.sourceforge.net/gnome.html)

---

### Post by daacosta on 2006-02-18
[QUOTE=taurus]The reason you can't see conky running because you are using Gnome with nautilus!!!  Here is a link for you to fix that...

[http://conky.sourceforge.net/gnome.html](http://conky.sourceforge.net/gnome.html)[/QUOTE]

Thanks man... Happened just like you told me... conky is working fine now! :mrgreen:

I still need to figure out how to minimize the flickering (tried the option -b but it doesn't like it...)  Perhaps increasing the frequency of sampling to 1 second?  I will try...

My other questions pertain to the conkyrc file so will hold onto this project for a couple of hours before asking...

---

### Post by taurus on 2006-02-19
May want to look at the option for "double_buffer" in ~/.conkyrc regarding flickering...

---


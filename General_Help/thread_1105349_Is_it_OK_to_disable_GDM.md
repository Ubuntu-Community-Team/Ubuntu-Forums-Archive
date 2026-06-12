---
title: "Is it OK to disable GDM?"
date: 2009-03-24
forum: General Help
---

### Post by linuxguy6 on 2009-03-24
I am the only user on my PC, and I really don't mind a terminal login. Will disabling gdm from the "Services" panel mess up anything?

---

### Post by kanikilu on 2009-03-24
I think this applies to what you are trying to do:

[http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/)

---

### Post by linuxguy6 on 2009-03-24
I don't think so. What I want to do is disable the graphical login window and be left with a text based login, which after I log in, it starts x. Is that possible?

---

### Post by kanikilu on 2009-03-24
I'd probably put startx & in my .bashrc file...but for more options, see if this helps:

[http://forums.debian.net/viewtopic.php?t=29333](http://forums.debian.net/viewtopic.php?t=29333)

---

### Post by mb_webguy on 2009-03-24
[Here]("http://ubuntuforums.org/showpost.php?p=6782289&postcount=2")'s the easy way to get a text-only login.  You could then put startx in your .bashrc file if you want.

Doing it this way gives you the option of a text-only or graphical login.

---

### Post by bodhi.zazen on 2009-03-24
It is OK to disable GDM, it will not break anything.

I probably would not put startx in you .bashrc as that will give you errors when you open a terminal within X.

The only reason NOT to disable GDM would be if you wish to use some of it's features such as switch users (not sure what happens with switch users if you start with startx).

kanikilu's link does the same thing from the command line.

---

### Post by linuxguy6 on 2009-03-25
I disabled GDM. It didn't break anything except the user switcher applet. You can't switch users; if you try using the lock screen, it doesn't go through and when you log back in again, it comes up with an error message. Thanks!

---

### Post by Slim Odds on 2009-03-25
You could just uninstall GDM. If you're not going to use it to login then you don't need it.

---


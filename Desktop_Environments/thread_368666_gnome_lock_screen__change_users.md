---
title: "gnome lock screen / change users"
date: 2007-02-23
forum: Desktop Environments
---

### Post by ender42 on 2007-02-23
So running gnome, and it has a panel addition called 'lock screen', which will make my screensaver into a lock-desktop type of functionality.  All well and good, except now that I want to give visitors to the house accounts on the machine....

When you switch users, it then lists all users on the machine.

This is bad security.  I shouldn't be giving out that information to anyone who can walk by and click on my screensaver.

1) Is there a way to disable this 'feature' so that it just asks you for a password without telling you which user is logged into the machine?  

2) And when you switch users, it should ask you for a username/password combo without giving you any hints as to who has an account on the machine.  Can I get that as well?

3) Also, is there a terminal-lock application?  Sometimes I leave one of my ctrl-F1's logged in, and I really should secure that as well...

---

### Post by ender42 on 2007-07-08
Well, no help on any of the above issues.   

New issue with lock-screen/screensaver. I couldn't get my GUI to respond since something was locked up.  I logged into tty1 and killed gnome-screensaver, but I can't restart it now... :\  Tried command-line from tty1, tried from system / screensaver preferences, and from the lock-screen menu (activate screensaver).  No luck.



I guess the solution is to reboot when I've got issues, since very little else works on Ubuntu.



Issues (weren't ever working): 

No sound card recognized - I used to be able to play music CDs, and mouse over MP3s used to play music - I also used to get my beeps and notifications.  
No video software will run (because no configured soundcard kills any video display attempts)

Things which have progressively become problems since ugrading to LTS from Warty:

CD drive is no longer findable, nor mountable (but if I boot off of the LiveCD it works)
USB hardware unrecognized (if I boot off the warty LiveCD I miraculously have USB ports again)
Mouse occassionally locks up (I'm going to try removing and reinstalling modules next time)
Keyboard goes haywire sometimes (I've tried resetting preferences, but no luck there)

Screensaver issues (a wide variety)
Firefox is broken, hard lock when attempting to save pages
Mozilla is crashy/buggy (every couple of days it will crash)

---

### Post by ender42 on 2007-07-09
It appears the issue is that I'm using the default screensaver/screen lock...

And that what's broken.

According to at least one post on the net, I should be using xscreensaver:

[http://www.jwz.org/xscreensaver/faq.html#gnome-screensaver](http://www.jwz.org/xscreensaver/faq.html#gnome-screensaver)

So, I've apt-gotten (heh), that program and removed gnome-screensaver.  We'll see if that fixes the problems I've got.

---


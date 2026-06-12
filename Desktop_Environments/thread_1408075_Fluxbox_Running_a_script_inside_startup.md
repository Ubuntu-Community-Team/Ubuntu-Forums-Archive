---
title: "Fluxbox Running a script inside startup"
date: 2010-02-15
forum: Desktop Environments
---

### Post by jellyxbean on 2010-02-15
I am on a Asus eee, and in my GNOME session I have a script running called tapfix that enable my two finger tap to act as a middle click.

Now I have added this to my fluxbox startup script located in the .fluxbox folder it looks like this
sh /usr/bin/tapfix.sh &

I assumed thats how it works in terminal that is how It SHOULD work on start up.
Now an interesting thing happens in my fluxbox I have the GNOME settings Daemon running for the use of the Fn key and all the F1-9 uses, but when I not run the G.S.D from startup my tapfix works. Run G.S.D tapfix does not work...

I have no idea what to do from this point at all...

---

### Post by jellyxbean on 2010-02-15
I can post my startup file is seeing the entire thing will help anyone out...this is the only thing keeping me from using fluxbox constantly besides an audio issue and the dreaded no flash click problem

---

### Post by jellyxbean on 2010-02-15
I have made an alias for this in terminal that is more easy to type than /usr/bintapfix.sh
I am still hoping that someone can help me out with this problem.

---

### Post by pi/roman on 2010-02-16
does "synclient tapbutton2=2" enable 2 finger tap as middle click for you?

---

### Post by jellyxbean on 2010-02-16
> **pi/roman said:**
> does "synclient tapbutton2=2" enable 2 finger tap as middle click for you?
wait so am I adding that to my flux startup? or just a terminal command?
Cause I know how to do it through terminal I just want to skip that aspect and just have it load up automatically like on my GNOME session

---

### Post by pi/roman on 2010-02-16
well if that works through terminal then you can set it to be persistent through hal configuration.  I have a guide for it here [[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645") and hal configuration is at 4b in my guide. 
You should be able to put it in system / preferences / startup applications and that would be automatic too.

---

### Post by pi/roman on 2010-02-20
Did this work?

---


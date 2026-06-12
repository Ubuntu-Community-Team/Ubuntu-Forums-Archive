---
title: "Gnome random restarts?"
date: 2007-03-15
forum: Desktop Environments
---

### Post by madcowbcs on 2007-03-15
I'm a newbie running Edgy.  My gnome session will quit unexpectantly and bring me back to the login screen.  Sometimes my machine will totally puke out and restart and POST again.  I usually can't get it to run more than 30 minutes.
Last night was my record for uptime.  I ran a list of divx files in VLC from midnight until I woke up around 7:30 :guitar: 

I don't think it is my memory.  my mem test did 8 passes without any errors.

What logs/errors should I look at to track down my problem?  Windows 2000 and XP gave me the same problems only worse.

---

### Post by spin2cool on 2007-03-15
Random restarts are often a sign of overheating, but the random logging out is another problem all together.

---

### Post by tagra123 on 2007-03-15
Using the Menu: System-Administration-System Log

Open the /var/log/messages  

or one of the other logs stored there. It should give you a clue as to what is causing the problem.  Google for the error message -- you'll be suprised how many answers you can find.  If you can't get the solution then post the messages here -- we'll help.

Since you mentioned he computer also just completely rebooting a couple thing to check.

Are you clock speeds set correctly in the bios -- check the manual.

Also as stated above make sure your fans are working and the heat sinks are not real dirty, especially the cpu fan, also look for bulging or leaking capacitors.  [www.badcaps.net](www.badcaps.net).  I've refurbished a few of these old boards and a couple nvidia cards by replacing the caps with better brands.

---

### Post by madcowbcs on 2007-03-17
Thanks.  I'll check my logfiles.  I just reseated my proc with thermal paste recently to try to fix the problem in XP.  I have 3rd party cooling on my nvidia card.  I think it is missing brackets. I'll check my var logs.

---


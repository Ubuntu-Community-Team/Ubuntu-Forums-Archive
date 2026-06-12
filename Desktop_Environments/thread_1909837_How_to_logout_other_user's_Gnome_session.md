---
title: "How to logout other user's Gnome session"
date: 2012-01-16
forum: Desktop Environments
---

### Post by jazzgossen on 2012-01-16
I have a problem in 11.10. My user's unity (I think) crashed, so I can't switch windows, open a gnome-terminal, or anything. So I'd like to log out, but without killing all other users' sessions.

I've tried running "gnome-session-quit --logout --no-prompt --display=:2" from a terminal as well as from another user's Gnome session, but I only get an error message saying "Couldn't connect to session bus...". (Without the --display argument, it says it can't open the display, so I'm pretty sure that :2 at least is my display.)

Now what?

Is there some other way that a sudoer can log me out?

---

### Post by sakishrist on 2012-01-16
I think "pkill -KILL -u username" will do the job **BUT** i am not entirely sure. Try at your own risk or wait until someone else confirms this works, it worked on my pc.

If I am right it kills all processes owned by the user specified ... so it should only kill the session you want it to.

Cheers,
Sakis

---

### Post by jazzgossen on 2012-01-16
Thanks! That's it.

---

### Post by hyperhelium on 2012-08-11
After upgrading ubuntu, I was having problems connecting to the internet in Unity, so I decided to start session in gnome... Big mistake... I was getting a blank screen and when restarting, I was getting to the same point. Couldn't get the welcome screen again. I looked in the internet for a solution and a lot of people was having a similar problem, but none of the other solutions worked. This one did the trick perfectly, getting me back to unity. Thank you very much sakishrist :D!!!

---

### Post by Antronin on 2013-04-14
Just for the records: ```
pkill -u <username>
``` is enough. I would only use **-KILL** if there are processes not stepping out.

---


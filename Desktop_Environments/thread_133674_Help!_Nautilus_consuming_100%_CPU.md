---
title: "Help! Nautilus consuming 100% CPU"
date: 2006-02-20
forum: Desktop Environments
---

### Post by purpleturtle on 2006-02-20
When I log in, 2 Nautilus processes are started which between them consume 100% CPU.. There does not seem to be any Nautilus windows open anywhere, so I'm not sure why the Nautilus processes are there.  I've killed one of the processes, but when I try and kill the other one, a Nautilus window then pops up, and another process has appeared consuming 100% CPU!! .. They do eventually go away (like after about 15 mins), but when I log out / back in again they come back !!

Does anyone have any idea what is going on with my machine? It's unusable like this!!

Thanks!

---

### Post by purpleturtle on 2006-02-22
I take it no-one know then! I must be alone with this problem.. :( 

I will try doing a big grep for every file for the string "nautilus"..  I think my problems started when I did "save setup" when I logged off a while ago.. So I'm wondering if that's what's restarting nautilus when I log in, and I guess it's not happy about something hence the CPU usage (perhaps the directory it is trying to default to has been deleted.. Or something..)

---

### Post by Ramses de Norre on 2006-02-22
Can't you start X with default options then?

---

### Post by purpleturtle on 2006-02-22
I just tried logging in with a failsafe Gnome session, but it made no difference. 

The process in question is this one:

25785     1 82 19:38 ?        00:02:00 nautilus --no-default-window --sm-client-id default2


If I go to System->Preferences->Sessions

nautilus is had an entry under "Current Session"..

Does nautilus perform some other function other than being a file explorer?

---

### Post by purpleturtle on 2006-02-22
By messing around the the "Sessions" applet, I seem to have managed to stop it starting these problematic Nautilus processes on startup....

---


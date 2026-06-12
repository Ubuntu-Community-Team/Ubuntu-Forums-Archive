---
title: "How do I stop firefox autostart"
date: 2009-05-23
forum: General Help
---

### Post by Gryphen on 2009-05-23
Recently firefox has been starting when I login.
how do I stop this?

---

### Post by glotz on 2009-05-23
Remove it from your session. System > prefs > sessions

---

### Post by Gryphen on 2009-05-23
I don't see sessions in the preferences menu

---

### Post by tmj42488 on 2009-05-23
system > preferences > startup applications. 

Sounds like you have it set up to start on login

---

### Post by Gryphen on 2009-05-23
I've looked at that already.
There's no firefox entry

---

### Post by Gryphen on 2009-05-31
Problem solved!
A couple weeks ago I turned "resume programs on login" on and played with it for a while.
As it turns out it's a bug where if you enable it and restart your computer(while you have programs running)and turn it disable it will still remember the programs from when you enabled it. So what you have to do is make sure no programs are open then go to system/preferences/startup applications enable the "resume programs on login" thing again and restart(with the startup applications window still open) then disable it.

---


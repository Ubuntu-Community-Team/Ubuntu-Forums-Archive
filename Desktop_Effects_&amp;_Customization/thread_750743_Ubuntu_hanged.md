---
title: "Ubuntu hanged"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by varunbhatbm on 2008-04-09
Hi,
Y'day while working in ubuntu, it suddenly hanged.
I had almost 10 windows open, I cud access none of them alt+tab, windows+tab :( nothing worked.
I was talking on skype, I cud continue that.. After my call was over, I cud not access any other window, I had to do hard reset.

Has anyone faced this problem. Did the jazzy desktop effects caused this problem? 
My laptop is brand new, with 2GB RAM and nVidia graphics. :(

Regards,
Varun Bhat

---

### Post by my_key on 2008-04-10
Hi, 

there's lot's of things that could have caused this. And I'm not such an expert that I can tell.

But next time instead of a hard reset you could also try to switch to a virtual terminal (CTRL+ALT+F1, you can switch back to X with CTRL+ALT+F7), login and type the command "top" to see which application is using all resources/crashing and remember it's name or PID (process id), exit out of top with "q", and type "killall <applicationName>" or "kill <process id>" .

If that doesn't make X usable again you could type (while in X) CTRL+ALT+BACKSPACE (don't test this command without saving all stuff that's open). This wil restart your X server and give you a new X session (you get a new login screen).

Ciao,

Michael

---


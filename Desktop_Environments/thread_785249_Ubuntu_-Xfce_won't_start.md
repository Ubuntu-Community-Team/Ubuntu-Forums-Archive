---
title: "Ubuntu -Xfce won't start"
date: 2008-05-07
forum: Desktop Environments
---

### Post by tattrat on 2008-05-07
I have installed Xfce on my ubuntu (8.04) system. Afteer the first reboot, it worked fine. It would not subsequently start, although gnome continued to function fine.

I then reinstalled the whole system, and tried again, with exactly the same result. 

How can I diagnose and fix the problem from my gnome environemt? Any help would be much appreciated.

Cheers

---

### Post by songshu on 2008-05-07
did you select xfce in GDM when you login?

---

### Post by tattrat on 2008-05-07
> **songshu said:**
> did you select xfce in GDM when you login?


Yes. If I select Xfce, it takes to the light blue screen, but the system is dead - The caps lock light won't even come on. CTRL+ALT+DEL has no effect.

If I instead select Gnome, everything works just fine.

---

### Post by tattrat on 2008-05-07
The plot thickens...
I decided to create a new user under gnome, and see if that could log on to Xfce....et voila - it could. So I then logged off, to see if the original user could log on to Xfce, and indeed I could. But the difference is that when I log on with my original userid, there is no window decoration on startup. I can restore it from the fusion icon option "restart window manager", but would still like to solve the problem.

Any ideas?

---

### Post by songshu on 2008-05-07
i guess it has something to do with compiz, wich is not default on xfce and causing you troubles.

did you try to enable compiz in xfce?

one solution might be to remove the .config in the /home of the user thats giving you trouble

---

### Post by tattrat on 2008-05-07
Will that affect gnome too?

Is it possible to start the two with different configs?

I have further discovered that, swtching users fails; I tried to do this whilst a web browser was open, with web radio playing. It gave me the login screen, but the sound continued to play. The new login just locked up (but sound continued . Hard reset...

---

### Post by tattrat on 2008-05-08
anybody?

---


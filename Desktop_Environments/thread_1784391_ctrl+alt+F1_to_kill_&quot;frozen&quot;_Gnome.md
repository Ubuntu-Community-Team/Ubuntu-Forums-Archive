---
title: "ctrl+alt+F1 to kill &quot;frozen&quot; Gnome"
date: 2011-06-16
forum: Desktop Environments
---

### Post by hagar54 on 2011-06-16
I have a two part question regarding ctrl+alt+Fl

1)The Gnome Desktop Froze on me and I would like to c+a+F1 then kill GNOME, there are alot of pid associated with gnome, what is the easiest way to kill or reset GNOME
 from tty1

2)Just for kix, is there a way to open a new tty8 session from tty1 or tty8 from tty7

---

### Post by Krytarik on 2011-06-17
To end all running Xsessions, and get a fresh login screen, or autologin, respectively:
```
sudo service gdm restart
```
Otherwise, to just stop GDM, just replace "restart" by "stop". Of course, that would leave you at the CLI, until you "start" it again.

I guess, that also answers your second question.

Greetings.

---

### Post by hagar54 on 2011-06-17
Greetings Kyrtarik,

Thanks for the quick reply, and yes, this solved my issue. I think I was trying to be to tricky, and simple is always the best answer.

And I think you did answer my second question, but let me ask;

what i want to do while in tty1 is open a gdm session with a different user in tty8, but I think from executing your example, if gdm is frozen in tty7, then gdm is frozen "everywhere"?

Thanks again, you did solve my problem, just trying to understand a little better, I will also review the ubuntu beginners link

---

### Post by Krytarik on 2011-06-17
Yep, if GDM is frozen, you can't start another instance of it. And it is per-se not run by a certain user, but is a system-wide service.

---


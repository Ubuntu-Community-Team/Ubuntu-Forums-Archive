---
title: "Quit button causes gnome to freeze for 90 seconds"
date: 2007-10-20
forum: Desktop Environments
---

### Post by scottmuz on 2007-10-20
Upgraded to Gutsy from Feisty.

Only issue is that when I click on the quit button my system
freezes for about 90 seconds then the shutdown window
appears with the restart, shutdown, logoff etc options.

It is very annoying as when you click the quit button you
want to quit not wait 90 seconds and then quit.

If I cancel the shutdown once the window is open, and click
on the quit button again it works fine.

---

### Post by Sendervictorius on 2007-10-21
gnome-power-manager has to be enabled, you change by ticking the Power Manager check box in System -> Preferences -> Sessions. Then log out, and log back in.

See this thread: [http://ubuntuforums.org/showthread.php?t=580982](http://ubuntuforums.org/showthread.php?t=580982)

---

### Post by scottmuz on 2007-10-21
:)

Thanks heaps fixes problem.

Strange I searched the forums for others who'd had the problem 
but didn't find the posts you referenced. Mustn't have entered the
magic combination of keywords.

---

### Post by ktulu1115 on 2007-10-25
Unfortunately that didn't resolve the problem for me.  The only thing I found to fix it was disable compiz.  Anyone else having same issue?

---

### Post by rincewind007 on 2007-10-30
Still have freeze but less :( thanks anyway

---

### Post by carlos1992 on 2007-10-30
thanxs
it doesn't feeze:guitar::guitar::guitar::guitar::guitar:

---

### Post by Humph on 2007-11-07
Yay!

I was having a similar issue: everything would seize up for 30-45 seconds , and the shutdown dialog would be missing the Suspend and Hibernation options the first time I clicked on quit. Subsequent clicks would show Suspend and Hibernate with no long delay.

Enabling power management fixed it.

---

### Post by Bigbird999 on 2007-11-13
I have this issue of "freezing" for about a min after I click the Logout button.  When the logout screen finally appears there is no suspend or hibernate button.  Hitting cancel and retrying the logout does nt produce a normal logout like OP said, but results in another "freeze".  

Everything, including suspend and resume from suspend, was working fine before.  I also am having the dreaded "Failed to initialize HAL"  screen after login.  Both issues appeared at the same time

Per the posts in this thread, gnome power manager is enabled and loging out and back in doesn't help.  I am not running compriz (at least I don't think I am)

Any ideas???

BB

---


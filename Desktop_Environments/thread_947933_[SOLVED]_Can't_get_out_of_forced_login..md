---
title: "[SOLVED] Can't get out of forced login."
date: 2008-10-14
forum: Desktop Environments
---

### Post by PhaeZee5 on 2008-10-14
I used Ubuntu (GNOME) to install my system, but I decided to go ahead and install KDE alongside it. I can use it, but I encountered a problem when I rebooted into kdm, instead of gdm, which I used to try it. My font size on everything was HUGE, and I unistalled KDE crudely.

Now, when I reboot, I get messages saying kdm could not be started, so I tried using a terminal login via control+alt+F2.

This works after I login as root and start gdm, but it is a pain and anybody else using my computer would not understand. How can I make gdm start during boot?

I am currently using Hardy 8.04.1

---

### Post by sumguy231 on 2008-10-14
This may be different in Hardy, but you should be able to do it graphically by going to System -> Administration -> Services and checking (uncheck first if already checked) the box for gdm.

If that doesn't work or you'd just rather use the command line, look in /etc/rc2.d and see if there is a 'KXXgdm' script. If there is, try renaming it to 'S30gdm'.

---

### Post by PhaeZee5 on 2008-10-14
Sadly, both were as you suggested. Thank for answering anyway.

---

### Post by sumguy231 on 2008-10-14
I'm sorry, I thought at least one of those would work. Have you tried reinstalling gdm entirely?

---

### Post by PhaeZee5 on 2008-10-15
Sadly, it was that simple. I really hoping for something complicated, but sadly, no. Maybe I should try Gentoo. :)

Thank you again.

---


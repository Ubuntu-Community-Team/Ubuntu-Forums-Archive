---
title: "[SOLVED] Separate Compiz/KDE Sessions"
date: 2008-02-16
forum: Desktop Effects &amp; Customization
---

### Post by Shampyon on 2008-02-16
I installed Compiz on Kubuntu. When I get to the login page only the failsafe and KDE sessions are available, maning when I choose "KDE" it starts KDE with Compiz by default.

I'd like to create a separate session option which runs plain ol' KDE, without Compiz and with it's own taskbar/panel settings, preferably without having to use a separate user account. I tried figuring this out for myself, going through the /usr/bin/startkde file and whatnot, but I just can't figure it out.

How would I go about this?

Another small problem is that for some reason when i press the shutdown button, the only option it displays is "Logout." I checked in Compiz's Advanced Desktop Effects Settings, and everything's right in there. Worse yet, when I choose "logout" the screen just goes black and the whole thing hangs. It doesn't shut down, it doesn't return to the login screen.

Weird, huh?

---

### Post by Shampyon on 2008-02-17
Using GDM instead of KDM seems to have solved this problem.

---


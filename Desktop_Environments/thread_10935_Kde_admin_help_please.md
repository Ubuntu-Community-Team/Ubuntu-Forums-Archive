---
title: "Kde admin help please"
date: 2005-01-12
forum: Desktop Environments
---

### Post by philip41 on 2005-01-12
Guys i have only been using linux for 1 week, so i am trying lots of various bits and bobs out.

Anyhow i decided to install KDE 3.2.3 using Synaptic manager. Kde installed ok and runs ok, apart from 1 annoying problem.
If i use the terminal i can sudo and when prompted enter the password(eg: password) and have root privalages, but if i say use kde's  Control center, system administration, and just 1 example the Login Manager, there is a button at the bottom ( administration mode ) if i press the button, i am asked " please enter root's password" so if i then add the password (eg: password) a box appears telling me it is the incorrect password.

What am i doing wrong please.

---

### Post by daniels on 2005-01-12
You're not doing anything wrong -- it's just that KDE isn't fully integrated into the Ubuntu system as it's an unsupported component (we use GNOME), and so we haven't fixed it to prompt for your password everywhere, instead of root's.

---

### Post by philip41 on 2005-01-13
[QUOTE=daniels]You're not doing anything wrong -- it's just that KDE isn't fully integrated into the Ubuntu system as it's an unsupported component (we use GNOME), and so we haven't fixed it to prompt for your password everywhere, instead of root's.[/QUOTE]


Thats cool at least i now know.

Thanks for the reply.

---

### Post by JohnQ on 2005-01-13
If you really want to use the KDE admin tools (or really just have a usable, useful root user), you can always create a root password:

#sudo passwd
[enter new pass]
[enter new pass again

---


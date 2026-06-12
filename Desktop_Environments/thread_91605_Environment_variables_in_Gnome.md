---
title: "Environment variables in Gnome"
date: 2005-11-17
forum: Desktop Environments
---

### Post by lisux on 2005-11-17
Hi list.
I have several environment variables that i want to setup for my gnome session.
I have pu my variables in /etc/profiles, but this variables are not ready in the gnome session.
For a gnome terminal the variables are set, but if  launch any program from a shortcut in gnome, or from the gnome menu or from the Run Application applet, the variables are not set.
Anydody knows how to set my environemnt variables fro my gnome session?

Thanks

---

### Post by frodon on 2005-11-17
As far as i know environment variables are known only in terminal not with graphical apps.

---

### Post by lisux on 2005-11-17
No, every time you launch an app, like X for example, it inherits the a environment.
The problem is that i don't what environment is inherit by gnome-session when it is launched from gdm.

---

### Post by frodon on 2005-11-17
it depends of the apps. For exemple i know that you can use environment variables in the konqueror bar and with konqueror in general, but when i write some graphical tools using zenity and need to launch them as root with gksudo the environment variables don't work.
However it can change on the next releases.

Let me know if you learn more about it, i'm also interested.

---

### Post by mempman on 2008-06-01
If you want to set gnome environmental variables, you need to issue
"export VARIABLE=value" in you ~/.profile.  

The problems you were encounter of not having your variables being exported to gnome is because you were setting your variables in /etc/bash.bashrc or ~/.bashrc.

Variables setup in bash rc are only valid in that bash shell session and any sub-child process of that bash shell. Furthermore, .profile is executed and can setup gnome related variables as well.

---


---
title: "Logoff problems due to other users till logged in."
date: 2009-04-23
forum: General Help
---

### Post by keithclark on 2009-04-23
On my laptop, every time I go to shut my computer off, it says I have to type in my password because others are logged into the computer still.  This happens even though I'm the only one using it, and the only one that has used it.

Keith

---

### Post by ChadMMc on 2009-05-02
I have the same problem. And all I am able to determine is what is listed in 'Details'
--
Application:    /usr/bin/gnome-session
Action:        [org.freedesktop.consolekit.system.restart-multiple-users]("http://org.freedesktop.consolekit.system.restart-multiple-users")
Vendor:
--

(No Vendor is listed in the dialog)

I am wondering about this myself as it has not happened before 9.04 :confused:
I am the only one logged in at all during these sessions (There is a 'root' that I cannot take away though and had never created on my own... also according to the system, it does not have any privileges in the system to do anything).

---

### Post by BslBryan on 2009-05-02
Root is the super user, and has more privileges than you do.  Ubuntu doesn't let you log in as root unless you use ```
sudo
``` before a command in a shell, which means "Super User Do this command."  For example, 
```
sudo su
``` means "Super User Do become the Super User (root)."  

Anyway, just wanted to clear that up for you.  I'm looking into your problem, and I'll try to have something for you to try a little later on tonight.

---

### Post by ChadMMc on 2009-05-02
Thank you, I do know of sudo, but my system has a 'root' user listed in my user settings panel.. may or may not mean anything really.

---


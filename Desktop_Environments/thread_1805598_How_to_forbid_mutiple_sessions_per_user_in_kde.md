---
title: "How to forbid mutiple sessions per user in kde"
date: 2011-07-16
forum: Desktop Environments
---

### Post by samuelm on 2011-07-16
How is it possible to configure KDM so as to forbid a user from having two or more sessions on the same computer?

Thank you in advance,
samuelm

---

### Post by samuelm on 2011-07-17
bump

---

### Post by samuelm on 2011-07-22
bump

---

### Post by samuelm on 2011-07-25
Bump. Nobody has any ideas on this?

---

### Post by enimeizoo on 2011-07-25
You mean graphic session, or also forbid console login?

---

### Post by samuelm on 2011-07-25
> **enimeizoo said:**
> You mean graphic session, or also forbid console login?

I mean the graphics session. Here is what I mean in detail:

Suppose you're already logged in and have a session on your computer. If you were to start a new session and login, KDM will create a second session with your account. If you were using GDM, it would redirect you to the session you already have. KDM, however, creates a second session. How do I make KDM behave like GDM in this respect?

---

### Post by enimeizoo on 2011-07-25
Well, it might not be a kdm issue. I'm not sure there is an option for this. If there was one, someone probably would have answered already.

I do have an idea about how to do it, but I'm not sure that is the best way.
The entries you have in kdm to select your session are .desktop files in /usr/share/xsessions. In those files you have an entry exec, which is the command executed by kdm when you choose the session. If you can change the file that is executed.
The idea is to write a script which would detect an existing session (ps could do the job, but there must be a better way), and redirect to that session if it exists. If not, it would launch what it was supposed to launch. Maybe you can see what is run by gnome and see how they do it if it is scripted.

But I might as well be wrong : does gdm redirect you to an already running kde session too? I can't really try that since I uninstalled everything related to gnome recently because somehow it broke my kde config. (I still don't know how, though, but uninstalling solved everything).

---


---
title: "Is Ctrl+Alt+F1 a program?"
date: 2009-03-02
forum: General Help
---

### Post by utnubuuser on 2009-03-02
Hi -- I'm wondering if the ctrl+alt+F1 function to enter terminal mode is an actual program in the file-system somewhere, and if so, how to locate the file?

I'm following a thread from the unanswered threads, trying to find out how to add ctrl+alt+F1 to the program startup list to shut down the x-server on startup.

This is the thread I'm hoping to answer  [http://ubuntuforums.org/showthread.php?t=1084752]("http://ubuntuforums.org/showthread.php?t=1084752")

Thanks

---

### Post by Locutus_of_Borg on 2009-03-02
it's called agetty and is typically /sbin/agetty

it will not, however, kill your X and dump you back to a bash shell

'sudo killall X' however will

you could add that to /etc/sudoers to not require a password, and put it in users startup directory, but it would be easier to stop using gdm to login, then there would be no X to have to kill

---

### Post by utnubuuser on 2009-03-02
Thanks Locutus_of_Borg

The poster of the original thread was looking for a way to avoid starting an x-session for a specific user.  - don't really know why - 
I assume if he were to disable gdm, that would be a system-wide change, and not specific to an individual user?

I guess login in through recovery is not the same thing?

---

### Post by Locutus_of_Borg on 2009-03-02
if you login through GDM then you have started X (as root) before any user logs in, so you'd have to kill X afterwards, but then GDM would probably just restart it

logging in "recovery mode" is simply single user mode e.g. as root in runlevel 1

I think the best way to do this would be, at the log in screen, to switch to another tty (ctrl+alt+F2 for example) and log the specific user in through that, then switch back to GDM (ctrl+alt+F7) for regular users, 

this though, is if the person wants to continue using GDM to login, as opposed to agetty, or even qingy (qingy provides support for graphics if the user does not want to use a "plain" terminal login while allowing users to log-in directly to a shell rather than X)

---

### Post by utnubuuser on 2009-03-02
Alright,  I'll point him/her in this direction.  Seems to me it's just as easy to go through a regular login, then get to a console by using ctrl+alt+F1.

---


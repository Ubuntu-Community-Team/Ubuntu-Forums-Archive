---
title: "Log on and off automatically with GDM on"
date: 2009-10-28
forum: Desktop Environments
---

### Post by Markstar on 2009-10-28
Hi,
I installed 9.10 Server + IceWM. What I would like now is to start IceWM automatically with a certain user and also shut down the computer when I log off. For this, GDM was suggested to me but sadly, since I'm not an Ubuntu expert yet, I can't get it to work. :(

I tried using "gksudo gdmsetup" and the window "Login Screen Settings" appeared, but everything was greyed out. When I clicked on "Unlock", this was displayed in the terminal:
```
markstar@e6700:~$ gksudo gdmsetup
** (gdmsetup:1433): DEBUG: init delay=30
** (gdmsetup:1433): DEBUG: Failed to identify the current session: Unable to loo
kup session information for process '1433'

** (gdmsetup:1433): WARNING **: Error calling GetValue('daemon/TimedLoginDelay')
: Key not found

** (gdmsetup:1433): WARNING **: Unable to find users: no seat-id found
** (gdmsetup:1433): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:1433): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1433): DEBUG: adding monitor for '/home/testuser1/.face'
** (gdmsetup:1433): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1433): DEBUG: adding monitor for '/home/testuser2/.face'
** (gdmsetup:1433): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1433): DEBUG: adding monitor for '/home/testuser3/.face'
** (gdmsetup:1433): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1433): DEBUG: adding monitor for '/home/testuser4/.face'
** (gdmsetup:1433): DEBUG: Getting list of sessions for user 1003
** (gdmsetup:1433): DEBUG: Found 0 sessions for user testuser4
** (gdmsetup:1433): DEBUG: Getting list of sessions for user 1002
** (gdmsetup:1433): DEBUG: Found 0 sessions for user testuser3
** (gdmsetup:1433): DEBUG: Getting list of sessions for user 1001
** (gdmsetup:1433): DEBUG: Found 0 sessions for user testuser2
** (gdmsetup:1433): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:1433): DEBUG: Found 2 sessions for user testuser1
** (gdmsetup:1433): DEBUG: GdmUserManager: not adding session on other seat: /or
g/freedesktop/ConsoleKit/Session2
** (gdmsetup:1433): DEBUG: GdmUserManager: not adding session on other seat: /or
g/freedesktop/ConsoleKit/Session3

```Am I missing something?

Also (maybe I should open another topic for this), I can't get it so IceWM shuts down instead of going back to the GDM login screen. I'm supposed to edit the IceWM preferences and change the ShutdownCommand to "gksudo shutdown -h now" and ConfirmLogout=0. However, these settings have no effect. 

The first problem is more important, but I would really like to get both to work. 

Thank you in advance for your help!

---

### Post by earthpigg on 2009-10-28
hi,

im still exploring solutions to similar problems myself with the new gdm. 

this may interest you:

[http://ubuntuforums.org/showthread.php?t=1299214](http://ubuntuforums.org/showthread.php?t=1299214)

and this may:

[http://packages.ubuntu.com/karmic/gdm-2.20](http://packages.ubuntu.com/karmic/gdm-2.20)

and this:

[http://wiki.archlinux.org/index.php/Gnome_2.28_Changes](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes)

---

### Post by Markstar on 2009-10-29
Thanks for your reply!

Sadly, I am not ready to compile packages and I don't really everything that is being said the gdm manual. 

All I see that I can do for now is that they fix this somehow, right (because you wrote in the other thread that gdm is broken)?

---


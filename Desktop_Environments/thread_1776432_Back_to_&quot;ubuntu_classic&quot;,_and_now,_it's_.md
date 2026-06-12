---
title: "Back to &quot;ubuntu classic&quot;, and now, it's blocked !"
date: 2011-06-06
forum: Desktop Environments
---

### Post by quoidautre on 2011-06-06
Hello there,

 Tired to use Unity (slow, crashes), I wanted to going back to the Ubuntu Classic.

 During reboot to confirm this selection. I have the login screen, and then the pink screen, the hourglass and then nothing. I tried to restart in debug mode, reset in the params, but nothing helped. A "unity --reset" neither.

 How to go back,to Unity, or to repair this?

 thank you
Fabrice

---

### Post by sikander3786 on 2011-06-10
Can you see the desktop? I assume you can but there are no panels etc. So, right click your desktop and choose "Create Launcher..."

Name it whatever and for command, type:

```
gdmsetup
```

Now double click the newly created Launcher and choose 'Ubuntu' as your default session. If 'Ubuntu' was already selected, you probably need to take a look at this one.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by dzidas on 2011-06-15
I have only remote access to Ubuntu desktop machine (I use NX Machine client and server). For that reason I can't use Unity 3D, so I installed Unity-2D, which it is not bad, but still buggy (the headers of all windows disappear).
The problem is, that I can't switch to Classic mode, because Login Screen "Unlock" button doesn't work. I tried sudo gdmsetup:

** (gdmsetup:28479): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:28479): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:28479): DEBUG: init delay=30
** (gdmsetup:28479): DEBUG: "/usr/share/xsessions/gnome-classic-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:28479): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:28479): DEBUG: Init default session found:'unity-2d'
** (gdmsetup:28479): DEBUG: Failed to identify the current session: Unable to lookup session information for process '28479'

** (gdmsetup:28479): WARNING **: Unable to find users: no seat-id found
** (gdmsetup:28479): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:28479): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:28479): DEBUG: adding monitor for '/home/kafka/.face'
** (gdmsetup:28479): DEBUG: GdmUserManager: skipping user with bad shell: ossec
** (gdmsetup:28479): DEBUG: GdmUserManager: skipping user with bad shell: ossecm
** (gdmsetup:28479): DEBUG: GdmUserManager: skipping user with bad shell: ossecr
** (gdmsetup:28479): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:28479): DEBUG: Found 2 sessions for user xxx
** (gdmsetup:28479): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session12
** (gdmsetup:28479): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session13
but it doesn't help.

Any idea how can I get Classic mode?

---


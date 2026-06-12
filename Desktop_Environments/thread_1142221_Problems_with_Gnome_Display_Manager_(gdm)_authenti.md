---
title: "Problems with Gnome Display Manager (gdm) authentication (Jaunty)"
date: 2009-04-29
forum: Desktop Environments
---

### Post by xonev on 2009-04-29
Hi, I just upgraded to 9.04 from 8.10.  Everything appeared to go fine, but when I boot up, before it gets to the login screen, I get a blue background (looks like a xubuntu theme background) and a "busy" cursor that make it appear as though something is causing processing over and over again.

When I dig into the log files, indeed, that is what I find.  For example:
```

#/var/log/syslog

...

Apr 29 09:50:02 sick-laptop gdm[5425]: WARNING: Couldn't authenticate user
Apr 29 09:50:33 sick-laptop last message repeated 25 times

```
```

#/var/log/auth.log

...

Apr 29 09:50:16 sick-laptop gdm[5425]: pam_nologin(gdm:auth): cannot determine username
Apr 29 09:50:47 sick-laptop last message repeated 27 times
Apr 29 09:51:49 sick-laptop last message repeated 51 times

```
```

#/var/log/gdm/:0.log

...

(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 29 09:57:04 2009
(==) Using config file: "/etc/X11/xorg.conf"
f000:4b9a: 01 ILLEGAL EXTENDED X86 OPCODE!

```

So it appears as though gdm is trying to auto-login (even though auto-login should be disabled according to the configuration files).  Anyone have any ideas?

---

### Post by xonev on 2009-04-29
Here are the things I've tried so far:
[LIST]
[*]Stop gdm -> startx
  [LIST]
  [*]I switched to tty1 (ctrl-alt-f1), logged in, and stopped gdm by running /etc/init.d/gdm stop
  [*]I then ran startx - this gave me the "login" sound and my background picture with a cursor, but no icons or "taskbars" or anything useful.
  [/LIST]
[*]Messing with the configuration file.
  [LIST]
  [*]I am rather sure I know which configuration file gdm is using because for the output of ps aux | grep gdm I get a couple of lines with:
```

root ... /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf

```
  [*]I've tried different variations of settings, but none seemed to have done anything (except when I turned debug on I did get some debug information in /var/log/syslog).  I have tried:
  [list]
  [*]Changing AutomaticLoginEnable=true and AutomaticLogin=sajo - nothing changes
  [*]Changing TimedLoginEnable=true TimedLogin=sajo TimedLoginDelay=0 because of something I read here: [http://www.perturb.org/display/entry/812/](http://www.perturb.org/display/entry/812/) (this is in addition to having automatic login enabled).
  [*]Changing ```
UserAuthDir=
``` to ```
UserAuthDir=~/
```
  [*]Changing User and Group to my username and group (still got the same error messages.
  [/list]
  [/LIST]
[/LIST]

---

### Post by xonev on 2009-04-29
Alright, I've even tried running:
```

sudo apt-get remove --purge gdm

```
and then reinstalling it with
```

sudo apt-get install ubuntu-desktop

```
and it is still giving the same problems.  Could it be a problem with PAM possibly?

---

### Post by mark_u23 on 2009-04-29
Hi this is my first post and fairly new to ubunto, dont know if my problem is the same as yours but sounds simliar.
 
Upgraded to ubunto **9.04** from **8.1**. Upgrade asked to reboot, now when i start I only get the command line.
 
Login as me ok, then  run - sudo/etc/init.d/gdm start -  "*Not starting Gnome Display manager (gmd) its not the default display manager"*
 
Startx command logs me into gnome but i want my KDE desktop screen and login back as was using without problems in version 8.1.
 
Is this a similar problem to yours or should I start a new thread?

---

### Post by xonev on 2009-04-29
I believe that is a different problem.  I think what you want to do is run /etc/init.d/kdm start.  kdm is the desktop manager for KDE so that should get you logged into kde.  However, since you're getting a command line instead of kdm starting up, it's possible that kdm wasn't installed into /etc/init.d/ properly.  Then, I'm not sure what to do, but at least you'll have a starting point (you could try reinstalling the kdm package).

Speaking of KDE, I'm pretty sure I have definitely narrowed this problem down to being a gdm problem since I installed the kubuntu-desktop package, set kdm as my default desktop manager and now I can log into the KDE gui no problem.

---

### Post by mark_u23 on 2009-04-29
Ok I will try that.  Thanks 
Its is strange tho because all was working fine before the update.

---

### Post by xonev on 2009-05-06
OK, I believe my problem has been resolved.  I have deduced that the distribution upgrade did not complete successfully even though I did not get any errors stating that anything went wrong.  I went to Update Manager to update my machine today and found that something had apparently gone wrong and that it wanted to do a "partial upgrade."  I allowed it to do so and now I am able to use gdm again and log into the gnome environment without any apparent problems.  Thank you for your help.

---


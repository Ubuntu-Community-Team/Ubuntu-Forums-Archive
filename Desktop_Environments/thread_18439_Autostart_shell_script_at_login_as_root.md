---
title: "Autostart shell script at login as root"
date: 2005-03-06
forum: Desktop Environments
---

### Post by Mlehliw on 2005-03-06
I want to startup a couple commands everytime I login i.e. modprobe and powernowd and I need to be root in order to execute those commands. I don't know where to put the script so that gnome will know to run it at login or how to make sure it gets executed as root without me having to type the password.

I know about the startup options under desktop preferences > sessions but I tried using that a while ago and it didn't do exactly what I wanted since there was no way to specify root access for it. I couldn't tell if it even executed the script at startup. Thanks

---

### Post by cwaldbieser on 2005-03-06
Do you want the programs to run ever time you log into a session, or every time you boot up the machine?  Scripts run when the system boots are going to automatically run as root.  Otherwise, I think you will need a (non-script) program that is setuid root to do what you want, since setuid scripts are not allowed for security reasons.

---

### Post by Mlehliw on 2005-03-06
Now that I think about it I would rather have them run when the machine boots up.

---

### Post by cwaldbieser on 2005-03-07
You can create startup script that gets run when the machine boots.  At the terminal:
```

$ runlevel
N 2

```
This tells me the runlevel I am running at-- in this case, runlevel 2.  That means when my system boots, it looks in /etc/rc2.d and runs the scripts it sees there.  (For a different runlevel, it would be /etc/rc#.d -- most of the time that is irrelevant, since you will normally be booting into the same runlevel all the time).

In the directory, the scripts have names like "S20inetd", where there is the letter S followed by a number.  The number tells what order the scripts are executed in.  Lowest first, highest last.  Ties, I am not 100% sure.

Anyway, all those scripts are probably sym-links pointing to real scripts.  All you need to do is create a script called "S99local" and link it to your local script (I call mine /etc/init.d/rc.local).  Just make sure to give it execute permissions.

---

### Post by Mlehliw on 2005-03-07
Thanks that worked perfectly.

---

### Post by kendo_paul on 2005-03-12
[QUOTE=Mlehliw]I want to startup a couple commands everytime I login i.e. modprobe and powernowd and I need to be root in order to execute those commands. I don't know where to put the script so that gnome will know to run it at login or how to make sure it gets executed as root without me having to type the password.

I know about the startup options under desktop preferences > sessions but I tried using that a while ago and it didn't do exactly what I wanted since there was no way to specify root access for it. I couldn't tell if it even executed the script at startup. Thanks[/QUOTE]
 I have a similar issue:  I'm setting up a computer for my Mother and I'd like to write a script to automatically start an application (Skype) whenever she logs on.  Can anyone enlighten me on how this can be done?  Thanks, Paul

---

### Post by cwaldbieser on 2005-03-15
GNOME:
Computer -> Desktop Settings -> Sessions -> Startup Tab

KDE:
Put shortcuts/links/scripts to run the programs in ~/.kde/Autostart

---

### Post by kendo_paul on 2005-03-15
Thanks for the help.  It's much appreciated.
Paul

---

### Post by emperor on 2005-03-15
[QUOTE=cwaldbieser]You can create startup script that gets run when the machine boots.  At the terminal:
```

$ runlevel
N 2

```
This tells me the runlevel I am running at-- in this case, runlevel 2. That means when my system boots, it looks in /etc/rc2.d and runs the scripts it sees there. (For a different runlevel, it would be /etc/rc#.d -- most of the time that is irrelevant, since you will normally be booting into the same runlevel all the time).

In the directory, the scripts have names like "S20inetd", where there is the letter S followed by a number. The number tells what order the scripts are executed in. Lowest first, highest last. Ties, I am not 100% sure.

Anyway, all those scripts are probably sym-links pointing to real scripts. All you need to do is create a script called "S99local" and link it to your local script (I call mine /etc/init.d/rc.local). Just make sure to give it execute permissions.[/QUOTE]

Thanks! I found this most helpful. I have missed the rc.local as in RH/FCx.

---

### Post by NTolerance on 2005-04-12
[QUOTE=cwaldbieser]You can create startup script that gets run when the machine boots.  At the terminal:
```

$ runlevel
N 2

```
This tells me the runlevel I am running at-- in this case, runlevel 2.  That means when my system boots, it looks in /etc/rc2.d and runs the scripts it sees there.  (For a different runlevel, it would be /etc/rc#.d -- most of the time that is irrelevant, since you will normally be booting into the same runlevel all the time).

In the directory, the scripts have names like "S20inetd", where there is the letter S followed by a number.  The number tells what order the scripts are executed in.  Lowest first, highest last.  Ties, I am not 100% sure.

Anyway, all those scripts are probably sym-links pointing to real scripts.  All you need to do is create a script called "S99local" and link it to your local script (I call mine /etc/init.d/rc.local).  Just make sure to give it execute permissions.[/QUOTE]

I'm following all of this right up to the part where you mention the rc.local file.  My Kubuntu Hoary installation does not have this file.  Do I need to create this file?  If so, how does it get executed?

---

### Post by emperor on 2005-04-12
[QUOTE=NTolerance]I'm following all of this right up to the part where you mention the rc.local file. My Kubuntu Hoary installation does not have this file. Do I need to create this file? If so, how does it get executed?[/QUOTE]

Yes, you have to create the file. 

The rc.local script file should be put in "/etc/init.d". To cause the rc.local script to be executed. you must make a symlink in one of the runlevel directories. For runlevel 2 it would be rc2.d. 

See my post in this thread concerning contents/structure of rc.local  here:
[http://www.ubuntuforums.org/showthread.php?t=19851&highlight=rc.local](http://www.ubuntuforums.org/showthread.php?t=19851&highlight=rc.local)

---

### Post by NTolerance on 2005-04-12
[QUOTE=emperor]Yes, you have to create the file. 

The rc.local script file should be put in "/etc/init.d". To cause the rc.local script to be executed. you must make a symlink in one of the runlevel directories. For runlevel 2 it would be rc2.d. 

See my post in this thread concerning contents/structure of rc.local  here:
[http://www.ubuntuforums.org/showthread.php?t=19851&highlight=rc.local](http://www.ubuntuforums.org/showthread.php?t=19851&highlight=rc.local)[/QUOTE]

Just tried it and it works great.  I was a bit confused by the rc.local filename, but now I see that a particular name is not necessary.  I copied my snespad script (loads modules for an SNES controller on a parallel port) to the init.d directory and then made a link to it in the rc2.d directory.

Thanks for the help.

---

### Post by emperor on 2005-04-12
if you just need to load a module at boot, you can put those in "/etc/modules", no need for "rc.locol" entry.

---


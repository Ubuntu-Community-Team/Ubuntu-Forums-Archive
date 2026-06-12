---
title: "Gnome Shell does not start"
date: 2013-03-19
forum: Desktop Environments
---

### Post by RMed on 2013-03-19
Hello, I'm using Ubuntu 12.10 with Gnome Shell 3.6. Today, after logging in, Gnome Shell is not starting, and the only thing I can see is the wallpaper, although I am able to open a terminal, so the window manager is working. I have tried to start the shell from the command line, but this was the output I received:

```
[FONT=arial](process:3264): GLib-CRITICAL (recursed) **: g_str_has_prefi[/FONT][FONT=arial]x: assertion `str != NULL' failedAbort (generated `core')[/FONT]
```

Also, having a look at the running processes with *top*, gnome-settings-daemon is using over 80% of my 4GB RAM. Everything was working correctly a couple of days ago, and I don't recall doing anything that may have caused this.

Any help on this would be highly appreciated :D

[HR][/HR]

**SOLUTION UPDATE:** I decided to investigate more in depth, so I went to gdm's session log in *~./cache/gdm/session.log* and turns out that gnome-settings-daemon was trying to access file *~/.cache/dconf/user*, but returned an error saying it didn't have permissions to do so. After checking the permissions of the file with:
 
```
**~/.cache/dconf$** ls -a -l

drwx------  2 rmed rmed 4096 mar 19 19:17 .
drwx------ 46 rmed rmed 4096 mar 19 19:14 ..
-rw-------  1 root root    2 mar 19 19:27 user

```

Therefore, user file was corrupted and gnome-settings-daemon was in an infinite loop suffering from resource starvation (unable to continue its execution).

**The solution** was as simple as renaming (in case something went wrong) the file:

```
**~/.cache/dconf$** sudo mv user user.old
```

And then simply restarting the machine and logging in as usual. Everything seems to be working perfectly now!

Hope this helps anyone that encounters this problem.

---


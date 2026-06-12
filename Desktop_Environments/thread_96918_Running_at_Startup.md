---
title: "Running at Startup"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Dagonus on 2005-11-29
I was under the impression that the appropriate way to run a few commands at startup was to write them in init.d and then symlink to them in rc*.d. When I try this, it says that it doesn't have permission to perform the actions in them.  Should I be going about this a whole different way, or am I just missing a few things?

---

### Post by Brent Dax on 2005-11-29
[QUOTE=Dagonus]I was under the impression that the appropriate way to run a few commands at startup was to write them in init.d and then symlink to them in rc*.d.[/QUOTE]
As with many things, It Depends(tm).

init.d scripts are run during boot-up--they're what cause all the "ok"s and "fail"s when you're booting.  If that's when you want your program to run, then you want to use init.d and rc*.d, but you'll need root access to do anything in these directories.  If you're using a command line, just prefix your commands with "sudo"; if you're doing this with the GUI, press Alt-F2 and type "gksudo nautilus" to start a file browser as root.

If you just want to start something when you log in, you should probably look at System, Preferences, Sessions.  The "Startup Programs" tab is what you're looking for.

---

### Post by Dagonus on 2005-11-29
Hmmm, see I dont' need it to give me "ok's" and "fails" persay. Mostly, I'm trying to run some setserials at start up and run ```
 xmodmap .xmodmaprc0
``` at start.

---

### Post by dcstar on 2005-11-29
[QUOTE=Dagonus]I was under the impression that the appropriate way to run a few commands at startup was to write them in init.d and then symlink to them in rc*.d. When I try this, it says that it doesn't have permission to perform the actions in them.  Should I be going about this a whole different way, or am I just missing a few things?[/QUOTE]
The sysv-rc-conf package gives you a tool to automatically turn on or off all the init.d packages during boot, it does all the symlinking for you! (beware though, you can bugger up your system quite royally too..........)

Also check the permissions on your new scripts, they should be the same as the existing ones.

---


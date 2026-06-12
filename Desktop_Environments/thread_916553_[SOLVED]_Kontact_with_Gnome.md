---
title: "[SOLVED] Kontact with Gnome?"
date: 2008-09-11
forum: Desktop Environments
---

### Post by grashdur on 2008-09-11
I use the Gnome desktop, but of all the calendar programs, I find Kontact by far the best -- for example, the Journal, the possibility of specifying where a calendar file is stored, templates, successful importing of files, ease of reading month view on screen, etc.

But I'm vaguely aware the Kontact is intended to work best with KDE. Am I inviting too much trouble by using Kontact with Gnome?

I have one gripe about Kontact, which might be because I'm not on KDE: 

Event reminders that I have not "dismissed" don't pop up on subsequent restarts of the program or of the computer. I have set reminders to be enabled at login. (Actually, in Evolution too, event reminders do not last after a program session.)

---

### Post by ad_267 on 2008-09-11
There shouldn't really be any issues. The only real problems are having to install kde libraries and having to load them to run the application. And the applications don't use the gtk themes applied to all other gnome applications. There shouldn't be any issues with the functionality of the programs.

---

### Post by Whiffle on 2008-09-11
I don't see any reason not to use it, it might slow things down a bit by having to load the extra kde libs, but thats about it.

AS far as the reminders, you might need to add these things to the startup programs:
> 
kded
kdeinit
klauncher
knotify
korgac
[http://ubuntuforums.org/showthread.php?t=429116](http://ubuntuforums.org/showthread.php?t=429116)

---

### Post by grashdur on 2008-09-11
That was helpful. By setting those little things to run automatically at login, I've enabled the reminders to work without my having to manually open the Kontact program. 

Reminders still get forgotten at next startup, but that seems to be a shortcoming in the program's design, rather than a setting that I can alter. I'll just have to jot down any undone tasks on my (paper) task chart whenever I shut down.

By the way, for anyone out there as ignorant as I am: You can set any program or applet to start up automatically every time at login with System > Preferences > Sessions > Startup Programs tab, and then "Add" the program. Also on this dialog box you can enable/disable things to auto-start. You'll need to know the path and filename of the program you want to add. FYI these applets listed above are all located in usr/bin, except for knotify, which is located in usr/share/services.

---


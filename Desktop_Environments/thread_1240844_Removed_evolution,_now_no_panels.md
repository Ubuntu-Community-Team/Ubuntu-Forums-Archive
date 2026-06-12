---
title: "Removed evolution, now no panels"
date: 2009-08-15
forum: Desktop Environments
---

### Post by RWise on 2009-08-15
I removed evolution as it was email jacking and not sending email, its now gone. So are the panels (tool bars, menu bars whatever) alt + F2 does nothing.

So I turned to the forum and searched for my problem and found matching results. One post said to remove the following files: .gconfd .gconf .gnome2 .gnome2-private .config I found a way into konquerer(sp) and removed these files

I got this error on restart:
Nautilus can't be used now, due to an unexpected error.
Details:
Nautilus can't be used now, due to an unexpected error.From Bonodo when attempting to locate the factory. Killing Bonodo-activation-server and restarting Nautilus may help fix the problem.

Now things are disappearing from the desktop

Help please! LOL

---

### Post by RWise on 2009-08-15
Another thread said to reinstall evolution, but I cant do that either,,,

---

### Post by RWise on 2009-08-15
> **idealflame said:**
> I had exactly the same problem (read: symptoms) as you last night/this morning, but that was because I was trying to draw FF3 kicking and screaming onto my Lenny (Debian) system, so I don't know if my solution will help you :)

Either way, you can at least get to *try* to start the gnome-panel by creating an empty file on your desktop, right-clicking (right-click still works, right?) and then selecting "Open with Other Application". In "Use a custom command", type gnome-terminal
If you type gnome-panel from there (the terminal), you'll at least get an explanation as to *why* it's not working...mine was because of a GTK2 problem. I don't know what you'll get, but at least we'll have something to go on!

Good luck


Ok this opened a terminal, cool, I typed *gnome-panel*

The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found

OK I did this and am about to reboot, hope this works,,,

---

### Post by RWise on 2009-08-15
That did get the panels back however files are still gone are they gone forever? AndI gotthese errors:

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".


Each had dont delete and delete as options, for now I chose dont delete,,,,
I would really like to recover the missing files as there was a lot of time involved

---

### Post by wojox on 2009-08-15
What files are gone?

---

### Post by RWise on 2009-08-15
at least 2 folders with pics and other data

---

### Post by RWise on 2009-08-18
Not much for help here!
Thanx anyway,,,,,,,,,,

---

### Post by mcduck on 2009-08-18
I'd recommend simply re-installing the "ubuntu-desktop"-metapackage, that should definitely get you back to a working setup.

After that you may try removing Evolution again, if you want, but this time be more careful when removing the evolution-related packages as some other Gnome components depend on them (which is why removing Evolution messed your desktop). However, if I were you, I'd leave Evolution as it is.

What comes to missing files, you'll have to tell more about that? Were the files on your desktop? In that case they should still be in the ~/Desktop-directory, it's just that you've broken Gnome and it's not showing the contents on that directory on your desktop. You should still be able to navigate to that directory with the fle manager, or from command line. That particular problem was most likely caused by removing your most important configuration files (all the dotfiles/directories you said you deleted).

---


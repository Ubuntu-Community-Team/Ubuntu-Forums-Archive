---
title: "Thrown out of Gnome!"
date: 2007-09-13
forum: Desktop Environments
---

### Post by Maqz447 on 2007-09-13
What did I do? lol. I have been running Ubuntu Feisty for a while, recently I decided to try out the Kubuntu desktop as well. For a while I could use both, however yesterday when I tried to log in to Gnome I got a black screen (of death?) immediately after the desktop loaded and had to reboot manually. Tried it again today, and what happens now is that I'm immediately thrown back to the GDM. The desktop loads, the screen goes black, and I get the GDM login screen. 

This happens whether I choose "Xclient script" or "Failsafe Gnome" for my session. However yesterday, when I got the black screen of death for the first time, I had chosen "Gnome". Previously I have always chosen to run the Xclient script and haven't had any problems (I have no idea what the Xclient script actually is, though).

KDE works fine. 

Does anyone have any idea what's wrong and how to fix it? I've come to prefer KDE and I can run all my Gnome apps in Kubuntu, but I'd like to be able to load Gnome if I want to.

---

### Post by Happy_Man on 2007-09-13
Try deleting all your GNOME settings folders in your home folder. It will delete any customizations, but at least I think you will be able to log in.

---

### Post by Maqz447 on 2007-09-13
Thanks, In my home folder I have folders named .gnome, .gnome2, and .gnome2_private. Should I delete those?

---

### Post by tipiglen on 2007-09-13
Try just renaming them to filename_BAK, then you can recover them.  remember they've got a dot at the start.

I can't even get gnome to start at login.  I think it's an x problem:

Xsession errors:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ed"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/4548

Good luck

ed

---

### Post by Maqz447 on 2007-09-13
So I moved those folders to the trashcan and tried starting Gnome, but the same thing happened. Oddly, my wallpaper and toolbar settings were unchanged (I could see them for about a second).

---


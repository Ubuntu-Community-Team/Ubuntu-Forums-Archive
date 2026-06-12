---
title: "Strange sound icon in gnome-shell 3.6, ubuntu 12.10"
date: 2012-10-25
forum: Desktop Environments
---

### Post by AshenShugar on 2012-10-25
A strange sort of icon mashup has appeared in my gnome-shell panel. It's one icon composed of the applet icons for sound, network, and battery. The icons show what the individual ones do e.g. if the system volume were muted, the icon in the mashup would reflect this. They act as a singled panel icon. It's weird. I've attached a screenshot. Clicking on it is like clicking on the sound icon, but without the option to open sound settings. The issue is a bit intermittent. Don't know if this is a gnome problem or an ubuntu problem. Anyone else noticed this?

EDIT: This is definitely a gnome-shell specific issue, as restarting the shell from the ALT+F2 dialogue fixes the problem temporarily, but it inevitably returns.

---

### Post by Mr.JJ on 2012-10-25
Thats the new icon that is supposed to be seen only in the lock screen. All other icons gets hidden in lock screen.  You are getting it in normal desktop defenitely look like a bug to me. Please create an issue in bugzilla against gnome shell.

Or you could add your comment here (which is a different bug but may be related): [https://bugzilla.gnome.org/show_bug.cgi?id=686763](https://bugzilla.gnome.org/show_bug.cgi?id=686763)

---

### Post by Lemagex on 2012-10-25
After coming out of the lock screen, try Alt + F2 type only "r" and press enter, this will restart shell and rule out a possible cause of it. I have lock disabled and I don't have the issue.

---

### Post by AshenShugar on 2012-10-25
Thanks for the info. I decided to just switch to lightDM

---


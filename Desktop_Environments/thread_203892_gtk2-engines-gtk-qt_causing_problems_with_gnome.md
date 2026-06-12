---
title: "gtk2-engines-gtk-qt causing problems with gnome"
date: 2006-06-26
forum: Desktop Environments
---

### Post by lastexyle on 2006-06-26
I like to switch back and forth between GNOME and KDE (still can't decide which one I prefer) but doing so seems to be causing me some problems. I installed gtk-qt since I like to use some GTK apps in KDE (Firefox in particuar). However, when I go back into GNOME, I'm forced to use whatever control/widget style I set in KDE and I have to log into KDE to change it again. I want to use different GTK widget styles in KDE and GNOME if possible, is there any work around for this?

Thanks!

---

### Post by aysiu on 2006-06-26
In the KDE Control Center, under appearances, select the blank selection for the Gtk theme... and don't put the black circle in it--put the black circle in the option above ("Use my KDE style").

---

### Post by lastexyle on 2006-06-26
Doesn't work. Doing that just makes the control theme locked as the QT one while in GNOME.

---

### Post by aysiu on 2006-06-26
[QUOTE=lastexyle]Doesn't work. Doing that just makes the control theme locked as the QT one while in GNOME.[/QUOTE]
This is how it should look.

For more details, look at [this thread](http://www.ubuntuforums.org/showthread.php?t=161434).

---

### Post by lastexyle on 2006-06-27
That's what I tried, when I log into GNOME, all my GTK apps are locked with the QT look-alike widget style instead of the one I've chose with the theme manager. Doing that just seems to change the theme setting in .gtkrc-2.0 to "Qt" for me.

---

### Post by aysiu on 2006-06-27
I'm not sure what else to suggest...

---

### Post by jpmorelli on 2006-07-18
Im having exactly the same problem, have kubuntu installed and install ubuntu-desktop , and i can't switch the option to GTK style.
At work i have ubuntu installed and I install kubuntu-desktop and it works well.
What library or option should I need to change ?

---

### Post by aysiu on 2006-07-18
> **jmorelli said:**
> Im having exactly the same problem, have kubuntu installed and install ubuntu-desktop , and i can't switch the option to GTK style.
At work i have ubuntu installed and I install kubuntu-desktop and it works well.
What library or option should I need to change ?
Post #4 doesn't help?

---

### Post by jpmorelli on 2006-07-18
YESSSSS !!!

It is working again, thank you ! I come back to this post to put the link to that post saying that there is the solution, thank's you all, a great comunity, I LOVE UBUNTU !!! :mrgreen: 

Sory about my english, I'm from Argentina

---

### Post by lastexyle on 2006-07-23
I wish someone could explain why using that option doesn't modify .gtkrc-2.0 for some people but does for me.

---


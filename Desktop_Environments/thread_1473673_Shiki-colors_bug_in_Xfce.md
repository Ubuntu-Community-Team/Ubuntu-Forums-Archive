---
title: "Shiki-colors bug in Xfce"
date: 2010-05-05
forum: Desktop Environments
---

### Post by fredbird67 on 2010-05-05
I've got a weird bug here.  It's nothing more than a minor annoyance, but to me, it's still pretty annoying, nonetheless.

I'm running PC/OS, which is based on Xubuntu.  I've got all of the Shiki-Colors GTK themes, the GNOME-Colors icon themes, and the Arc-Colors themes installed.  Everything's going great, but I've got one little annoyance going on.

What's happening is the Arc-Colors (both the list and non-list version) showing up in my GTK themes list, and that's obviously not where they belong -- these, of course, are supposed to be GDM themes.  What's more, I see nothing in the /usr/share/themes directory to indicate that they're in there by mistake, and in fact, I distinctly remember putting them in /usr/share/gdm/themes, which is where they belong.

I first tried this downloading and installing them from the repos, and when they acted up there, I tried the manual installs from GNOME-Look and got the same thing, too.

Anyone know what's up with this and how to correct it?

Thanx in advance,
Fred in St. Louis

---

### Post by fredbird67 on 2010-05-06
This wasn't really the way I wanted to do it, but I moved the themes into my .themes directory, and that solved the problem.  However, it also meant I had to copy those themes over to the .themes directory for each user on there, which I think sucks since it uses up that much more hard drive space, but hey, at least it solved the problem.

---


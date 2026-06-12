---
title: "Disabling Windows Minimization Animation May Cause Issues"
date: 2007-02-23
forum: Desktop Environments
---

### Post by SuSUntu on 2007-02-23
Just a heads-up.

Applying the often discussed two-part Metacity windows-animation disabling tweak:

> 
1. gconf-editor 

Apps > Metacity > General > Select / Enable Reduced Resources

2. System > Preferences > Assistive Technology Preferences > Enable Assistive Technologies
 

may result in conflicts with applications that either "autohide" or can be hidden away when not in use.

In my experience, it's actually the Assistive Technology part of the tweak that caused major issues when AT was enabled contemporaneously with use of [Tilda]("http://tilda.sourceforge.net") (a terminal application that hides out of the way when not in use).

The most extreme issues were no Gnome desktop other than the background image, or if the desktop was successfully drawn, no icons would work and CTL-ALT-Backspace would have to be used to get back to the login screen.

If the problem was not initially as severe as described above (meaning icons and menus appeared to work), other weirdness was presented:

1. System generally slower and at times unresponsive;
1. Nautilus would launch multiple windows with just one click of a launcher icon; 
2. Nautilus would hang indefinitely when attempting to open a directory;
3. Tilda itself would revert its preferences to default and present its configuration interface as if it was being run for the first time;
4. Wine applications' icons which should show in the notification area would open as tiny icon-sized windows on the desktop while non-wine icons would load in the notification area; 
5. Running an archive process from inside Nautilus (if I could get that far) would cause file-roller to launch multiple instances of itself (as confirmed via System Monitor), and the desktop archive progress bar would continue back and forth in a never-ending loop (as much as 900MB of ram [not cache] would be consumed by those processes until I killed them);
6. Other assorted weirdness.

Disabling AssistiveTechnology again returned the system to normal. 

The problem was a little difficult to trace to enabling Assistive Technology because I didn't notice the major weirdness until after I restarted X via CTL-ALT-Backspace for an unrelated reason quite some time after I had enabled Assistive Technology.

Anyway, I initially thought I would opt to get rid of Tilda because I really, really, REALLY hate the Metacity windows animations / wireframes, but after thinking more about it and living with Assistive Technology enabled  for a while, I disabled it again and re-installed Tilda. Here are a couple of the reasons:

1. As much as I hate the animations (or no animations but with wireframes), I'm not clear on what else might be impacted by Assistive Technology because I don't fully understand what the underlying changes are when it is enabled. Aside from the weirdness it caused with Tilda running, I also noticed that when you launch a GUI application from the command-line, this message pops up:

> 
user@computer:~$ gedit


(gedit:12815): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized


If you install libgail-gnome-module, then you get this error-free message:

> 
user@computer:~$ gedit
Bonobo accessibility support initialized
GTK Accessibility Module initialized


As much as I hate the animations / wireframes, I dislike Assistive Technology as a solution just as badly since it appears to be pervasively invasive.

2. I like Tilda. :)

Again, this is really just an FYI for those that may encounter some unexplained strange behavior if you have Assistive Technology enabled. By the way, I read through 11 threads on the gconf-editor / Assistive Technology hack dating back to June 20, 2005 and no one else mentioned any issues in those threads.

And of course, if you actually need Assistive Technology enabled for reasons other than as a hack to get rid of the wireframes when animation is turned off (via limited resources in gconf-editor), your evaluation of which trade-offs are important will be quite different than mine.    

Thanks.

-----
Issues discussed appeared on a fresh installation of Edgy with default (non-proprietary) video drivers in place.

---


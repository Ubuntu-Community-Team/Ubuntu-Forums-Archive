---
title: "[SOLVED] Desktop links in gnome always open new firefox 3 window"
date: 2008-11-12
forum: Desktop Environments
---

### Post by HDave on 2008-11-12
Whenever I click on a URL in Thunderbird or Tomboy when Firefox is open, it opens up a new window rather than opening a tab in the existing window.

I am not sure if this is the intended behavior or not, but I would really like to have it open a new tab instead.

Any ideas are welcome!

---

### Post by aged hippy on 2008-11-12
If you go to  ->Firefox ->Preferences ->Tabs you can tell it to open it in a new window or a new tab. :)

---

### Post by HDave on 2008-11-12
Thanks for your quick reponse, I already have it set to open in a new tab.  

I should have mentioned -- Whenever I click on a link inside firefox it always does the right thing and opens a new tab.  It just when I click on a link outside Firefox it opens a new window.

---

### Post by aged hippy on 2008-11-12
That's odd, Thunderbird always opens it in a new Firefox tab here....

I don't know what to suggest, to be honest. :confused:

---

### Post by HDave on 2008-11-12
I know its a problem with Gnome.  If I do a 

firefox [www.google.com](www.google.com)

from the command line it opens up a new tab.  Gnome must be using a different command line to launch firefox...perhaps it has -no-remote on it.

---

### Post by HDave on 2008-11-12
Found where Gnome stores the command to launch firefox.  Used gconf-editor and went to desktop->gnome->url-handlers->http  and also https.

Took out the -new-window argument from the command line and viola...just works.

Too bad I can't thank myself!

---

### Post by aged hippy on 2008-11-12
Here you go. :popcorn:

---

### Post by bopomofo on 2008-12-30
I'm having a similar problem, although I want the opposite behavior as the first poster. And the proposed solution does not help.

What I've found on my system (8.10, FF3.0.5) is that NO MATTER HOW I SET GCONF or System > Preferences > Preferred Applications, opening an instance of Firefox from an external program ALWAYS follows my settings in Firefox (either new window or new tab), and completely ignores gconf/Preferred Applications.

What gives? :confused:

I know that my system used to behave as expected, i.e. external apps would follow System > Preferences > Preferred Applications.

---

### Post by bopomofo on 2009-01-12
I really can't get to the bottom of this. Certain application seem to follow the gconf settings (Pidgin for instance, or Firefox launchers I create) while others seem to always follow Firefox's internal settings (Twhirl, Nautilus).

What's going on? I would think that all applications should respect the settings in Preferred Applicatins. :confused:

---

### Post by Kheops_74 on 2009-01-17
Same here Twhirl always call Firefox. I change http and https in gconf-editor. Didn't work.

---


---
title: "Gtk Error When Menu Item Selected"
date: 2006-04-18
forum: Desktop Environments
---

### Post by OldSeaDog on 2006-04-18
Hi all,
I am a newbie trying to find my way through the darkness, and have run into a problem with my laptop (which I won in a raffle and switched to Hoary muy pronto).  It start fine and brings up the Gnome Dispaly all right, but none of the apps load when I click on them, whether it is from a menu, from the panel, or evn from a desktop launcher.  In fact in the last case, nothing happens when I click on the desktop with any mouse button, on an icon or otherwise.  I can't even open up the file broswer..

The apps I had open the last time It ran right still load when it starts up; fortunately one of them is a terminal window.  When I try and run them from the command line, it also fails.  The speific error message is:

Gtk-WARNING **: cannot open display:

From my limited knowledge of Linux, it appears that it has lost the display (0:0), but I have insufficient knowledge to find out where it lost it.  ](*,) 

The laptop is an Acer Aspire 3003, with an 80 GB hard drive (37GB for Hoary and the rest being reserved for future use).  It has 1GB of RAM (I even have trouble writing that - my first network server was put up in the mid-80's with a 286 processor and duplexed 40 MB hard drives.)  It is plain vanilla otherwise.  It has a wide screen which gets screwed up in text mode, due to the odd geometry and I am having wireless "issues", but that is beside the point.  Just part of the challenge...

Is there someone out there who can take pity upon me and suggest a path to the light so I can actually use it for something?

---

### Post by OldSeaDog on 2006-04-19
I have continued to explore the problem as best I can with my limited Linux knowledge.  If I try and run a KDE app rather than a Gnome one, I get a different error, as follows:
{appname}: cannot connect to X server :0.0
I opened up the .xsession-errors file to see what light it could shed on the saga and its last several entries are as follows:
** (gnome-cups-icon:7828 ):  WARNING **: IPP request failed with status 1030.
  If this helps anyone in finding out what is going on, I would certainly be grateful...

OldSeaDog

---


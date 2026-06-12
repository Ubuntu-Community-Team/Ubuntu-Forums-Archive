---
title: "gnome-pilot applet icon disappeard uon upgrade to Jaunty"
date: 2009-04-29
forum: General Help
---

### Post by DJ_Peng on 2009-04-29
I'm having the weirdest issue after upgrading my comp to Jaunty. For some odd reason the icon for my gnome-pilot applet has disappeared in Jaunty, although I see that the pixmaps for sync status are still there. It's become pretty impossible to send a file to my PDA since I can't drop the file onto the icon any longer.

Just for completeness of information, I first did a dist-upgrade to get 9.04, but after getting some major issues with MPD I was advised to do a clean install of 9.04, and I created a new profile to use with the new install. This, of course, only adds insult to injury that I'm unable to see anything beyond a dot where the applet resides on my panel.

---

### Post by greenjumper on 2009-06-15
The very same thing has happened to me. I can sync my Palm as normal but I can't install new programs which is rather annoying. I tried the advice here: 
[http://nancib.wordpress.com/2009/05/19/installing-files-on-a-pda-in-ubuntu-9-04/]("http://nancib.wordpress.com/2009/05/19/installing-files-on-a-pda-in-ubuntu-9-04/")

but that didn't have any effect. Does anyone have any idea how this can be solved? It is the only thing that is broken after my upgrade to Jaunty.

---

### Post by greenjumper on 2009-06-15
If however you use the terminal version from the above link you can install programs without any problems!

---

### Post by greenjumper on 2009-06-15
Just done a restart and the icon has appeared! So try what the link says with the two .deb files!

---

### Post by greenjumper on 2009-06-16
Now though, every time I start the computer new, it appears about ten times!
Anyone got any ideas how this can be fixed? Have tried removing it completely from the panel, and then doing a new start, but it keeps happening!

---

### Post by DJ_Peng on 2009-06-16
I'm glad my tutorial helped you. [OT]I'm working on a similar one for people who use AvantGo, which is shutting down at the end of the month, so they'll be able to keep getting content like AG currently provides.[/OT]

Try removing them all, and then do a restart (rather than just a relog). Not sure if that will help but it might. Otherwise you many need to do a search for where the panel settings are stored and remove the extras manually.

---

### Post by greenjumper on 2009-06-17
Basically every time you remove one, one less appears at the next restart. So you have to remove one, restart, remove one, restart etc etc until only one is left!
I think it's because of all the attempts to get the applet to appear before I used you fix. Although they didn't appear they were still there somehow and appeared after the fix.
All sorted now though - thanks again.

---


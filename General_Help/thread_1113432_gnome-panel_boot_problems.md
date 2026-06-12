---
title: "gnome-panel boot problems"
date: 2009-04-01
forum: General Help
---

### Post by mikedmor on 2009-04-01
I have been running ubuntu 9.04 for a good 3 months now with really no problems but just today i booted up and when the gnome-panel showed up it is missing the time & login/off components. 

Yes i know i can add them back but the problem is the whole panel is frozen except for my system monitor applet running in the panel. I found a fix by killing the gnome-panel processes, then it restarts and works just fine. But its kinda annoying that i have to do that every time i boot now.

Any fix? if you need more information just let me know how to get it!

Thanks

-Mike

---

### Post by James_Lochhead on 2009-04-01
My suggestion is submit a bug report to launchpad. The developers there can help you and get the problem fixed for everyone else at the same time.

---

### Post by mikedmor on 2009-04-01
wells thats usually my first attempt. but it seems launchpad is down. so i figured i would see if anyone here knew.

Thanks for the quick reply!

---

### Post by Aenima99x on 2009-04-01
Just wanted to add that I'm also experiencing the issue. I can say the update came today at some point.

---

### Post by mikedmor on 2009-04-01
great. so its not just me. that makes me feel much better now.

---

### Post by techno-mole on 2009-04-04
me too, you could try running the kill panel command at start up,its not too much of a problem for me as i dont really use the panel (using awn)

in theory running the kill panel command at start up should stop the panel (  thus solving the panel being frozen issue ) and the panels should then restart ?

im about to try it.

PS - running 9.04 (jaunty) beta (32 bit not 64 bit)

---

### Post by mikedmor on 2009-04-04
well it seems to be fixed after i updated last night. so i think they got to it.

---

### Post by jfvb1225 on 2009-06-26
This same thing or something similar seems to happen to me every time an update completes. So far I have solved the problem temporarily by simply creating a new user name. After today's update though, it happened again and I somehow got the panels back.
After googling around, I've found several posts by people who's panels disappeared after making some changes to their systems, or after applying updates.
I'm making my way (slowly) from Windows to Linux and have found Xubuntu to be the best distro so far, but this is a nagging problem I want to see permanently fixed.
Is this a known bug with 9.04 and if so what is the best workaround or solution for it at this time?
Thanks in advance.

---

### Post by jfvb1225 on 2009-06-27
Well, my post has fallen 14 pages behind other issues reported in the last 24 hours without a response. I'll assume there are many other issues going on besides this one with Xubuntu 9.04 and I will just live with it I suppose. ;)

---

### Post by Devi 710 on 2009-07-09
I have the same panel problem. It used to be every once in a while. Now it is every time I startup. I have to logout and login again to fix it :mad:

It also doesn't load the image I have set for the panel.

Screenshot of the error - no weather, network manager, volume control, date, logout menu:
[IMG]http://files.getdropbox.com/u/1483214/panel_issueB.jpg[/IMG]

How it should look:
[IMG]http://files.getdropbox.com/u/1483214/panel_normalB.jpg[/IMG]

I've never filed a bug report before. Is there a way to tell if it has been filed already?

Thanks,

Devi

---

### Post by jfvb1225 on 2009-07-14
All I can tell you is creating a new session fixes it for me. Until it breaks again. :mad:

Edited to add:

[http://ubuntuforums.org/showthread.php?p=7614385#post7614385](http://ubuntuforums.org/showthread.php?p=7614385#post7614385)

Try this thread it worked for me!

---

### Post by Devi 710 on 2009-07-14
OK, I tried "gnome-panel --replace" as mentioned in a few forums and this was the output:

```
** (gnome-panel:3610): DEBUG: Adding applet 0.
** (gnome-panel:3610): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3610): DEBUG: Adding applet 1.
** (gnome-panel:3610): DEBUG: Adding applet 2.
** (gnome-panel:3610): DEBUG: Adding applet 3.
** (gnome-panel:3610): DEBUG: Adding applet 4.
** (gnome-panel:3610): DEBUG: Adding applet 5.

(gnome-panel:3610): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 23
** (gnome-panel:3610): DEBUG: Adding applet 6.
** (gnome-panel:3610): DEBUG: Adding applet 7.
** (gnome-panel:3610): DEBUG: Adding applet 8.
** (gnome-panel:3610): DEBUG: Adding applet 9.
** (gnome-panel:3610): DEBUG: Adding applet 10.
** (gnome-panel:3610): DEBUG: Adding applet 11.
** (gnome-panel:3610): DEBUG: Adding applet 12.
** (gnome-panel:3610): DEBUG: Adding applet 13.
** (gnome-panel:3610): DEBUG: Adding applet 14.
** (gnome-panel:3610): DEBUG: Adding applet 15.
** (gnome-panel:3610): DEBUG: Adding applet 16.
** (gnome-panel:3610): DEBUG: Adding applet 17.

(gnome-panel:3610): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3610): DEBUG: Adding applet 18.


```

Anyone understand what it means? Do I have some issue with "glade" that is affecting my panel?

Thanks,

Devi

---


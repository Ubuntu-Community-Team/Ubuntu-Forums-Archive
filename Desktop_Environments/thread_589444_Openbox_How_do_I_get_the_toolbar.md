---
title: "Openbox: How do I get the toolbar?"
date: 2007-10-24
forum: Desktop Environments
---

### Post by oldcpu on 2007-10-24
Currently using Fluxbox.  Trying out Openbox to see what the commotion is all about.  One physical thing missing is the toolbar (the one on the bottom).  I have looked through all the options in Openbox and can not find it.  How do I get one?

---

### Post by urukrama on 2007-10-24
You'll have to add one. Openbox is very minimalistic, and doesn't come with a panel or task list. You can use pypanel, fbpanel, lxpanel, perlpanel, tint (just a task list) or visibility (an icon box/list) or even xfce4-panel, gnome-panel or kicker. Just add them to your autostart file (/home/USERNAME/.config/openbox/autostart.sh), before it mentions openbox (at the end) as
> *nameofthepanel* &

Make sure the & is there at the end, or Openbox won't load properly. For more about the autostart file, see [this page]("http://icculus.org/openbox/index.php/Help:Autostart") (you'll probably only need the first part of that page). Hope this helps.

---

### Post by oldcpu on 2007-10-24
Thanks.  But does the *panel need to be in parathesis like in the example?

Also, by default, how would an Openbox user know what windows are open or obscured by other windows if they do not rely on the toolbar?

---

### Post by urukrama on 2007-10-24
No parenthesis are needed.

I used Openbox for a long time without a panel, and still do so now at times. The alt-tab dialog helps me to keep track of what is open, minimized, etc. Make sure you installed the [latest]("http://icculus.org/openbox/index.php/Openbox:Download") version of Openbox to have this option, though. The repos version is outdated, and doesn't have that cool alt-tab dialog (among many other things).

If I want to know what is running on other desktops, I use the client-list-menu (middle click on desktop, or bind it to a key combination). I've also used [skippy]("http://thegraveyard.org/skippy.php") in the past, though this only allows you to see what is not minimized.

It takes a little while to get used to it, but I found not having a panel or task bar very useful and productive (less distractions).

---


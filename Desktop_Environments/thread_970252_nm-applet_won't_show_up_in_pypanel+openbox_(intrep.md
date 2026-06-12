---
title: "nm-applet won't show up in pypanel+openbox (intrepid)"
date: 2008-11-04
forum: Desktop Environments
---

### Post by crazybilly on 2008-11-04
I use openbox a lot, and when I do, I usually run pypanel.  After my Intrepid upgrade, though, I have a strange problem: nm-applet won't show up in my notification area.

In Gnome, it's just fine, no issues at all.  And if I remove the notification area from my gnome-panel and run pypanel in Gnome, the Network Mananger applet shows up just fine.

But in Openbox, I can't get it to show up in pypanel.  There, if I run gnome-panel, it shows up. And if, then, again remove the notification area and run pypanel, I get it.  

Obviously, running gnome-panel and then killing it is not the optimum solution here. 

I never had this problem in Hardy--I'm assuming it's due to a change somehow in Network Manager (which overall, looks really great). Anybody got any ideas?

Huh.  here's something else I just noticed (possible related, but not necessarily so): I have an icon as a program launcher in pypanel, and it's not showing up initially (until after I start gnome-panel) either.  No clue what that means--anybody got an ideas?

---

### Post by crazybilly on 2008-11-13
Anybody figure anything out with this?

I did a bit of poking around with it today...looks like Network Manager is running just fine, and like usual, crashes when you close pypanel.  

Also, what I described earlier as 'my icons and launcher disappearing in pypanel' looks more like the nm-applet icon is displaying wrong--like the icons shows up, but writes a bunch of blank space to the left of where the icon ought to show up, in essence pushing everything else off the screen.

If I close NetworkManager, that bank space disappears and everything else 'comes back'.

I'm assuming this is a bug in the new version of Network Manager, but could go for some straighter answers from people who actually know (cause I sure don't). ;)

---


---
title: "Displaying printer queues on startup."
date: 2008-03-31
forum: Desktop Environments
---

### Post by sigmason on 2008-03-31
I am using CUPS as a printer server.  I have a box running Ubuntu and when I start it up I created a user with very few security rights, but one of them is being able the manage the print queues.

Now this computer looses power frequently, even with a UPS.

I'm prepared for the computer to shut down when the UPS runs low.

Now the problem I have is on startup I want the print queues displayed like I had them when the system shut down.

I want this to happen, not so much because of something like a hibernate, but because of some form of scripting.

How can I get the printer queues to open and be positioned at certain places when the system boots?

I figure DevilsPie or Xnee could help, but I'm not sure that's a great solution, is there a way to call those queue windows and manipulate them with a script?

Sigmason

---

### Post by sigmason on 2008-04-01
[http://www.penguin-soft.com/penguin/man/1/gnome-cups-manager.html](http://www.penguin-soft.com/penguin/man/1/gnome-cups-manager.html)

The command to open the queue for the printer directly is:

gnome-cups-manager --v {printer name}

So with this and devilspie I should have what I need.

Sigmason

---


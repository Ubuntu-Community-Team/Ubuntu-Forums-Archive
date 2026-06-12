---
title: "After idle, sudo fails"
date: 2008-03-21
forum: Dell  Ubuntu Support
---

### Post by rpglover64 on 2008-03-21
I use wicd instead of Network manager.  This may or may not be related.  Also, I have a Dell 1420 running a clean install of gutsy.  Anyway, after my computer has been left on for some time (about a day on average), I notice my wireless is down and wicd does not see any networks.  At this point, if I try to shutdown using graphical methods, I can't.  If I open a terminal, the terminal freezes and stops responding after any "sudo" command.  The only way I've found to restart my computer in this state is holding the power button.  Has anyone else experienced this or knows what's going on?

---

### Post by natehall on 2008-03-22
I have a similar problem. Here's one of my workarounds.

 System>Preferences>Power Management>General>Always display an icon . 

  You should get a little plug icon in the upper right hand corner. I've noticed on mine it does not matter if its plugged in or not, but if you don't see that icon you will have problems shutting down. Before  you shut down go through some of these steps to see that plug icon pop up. 

  Another workaround I have for when I forget to "pop up the plug" is "Control Alt F1" to bring up a terminal, log in, then "sudo halt". If that does not work, other then yanking out the battery, the power down button is all that's left.

  There has been alot of posts on this forum about this very problem , I have no doubt they actually have figured out how to end this problem but I figure I'll just live with it until I switch over to Hardy after Dell comes out with its own version. ( July? who  knows!)

---

### Post by sdennie on 2008-03-22
It could be related to the wireless driver you are using.  I would try the instructions from at: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues) and see if they help.  I had a lot of stability issues with an XPS m1330 until I followed these instructions.

---

### Post by natehall on 2008-03-22
I remember trying that wiki a few months back. Afterwards I could not get my network to work so I undid it.

    I don't think its related to the network anyways because I didn't have any problems shutting down until I messed with the power settings (Which is another workaround, log on as a different user, Of course then you have a problem with getting to your files and have to mess around with a bunch of permissions using chmod)

---


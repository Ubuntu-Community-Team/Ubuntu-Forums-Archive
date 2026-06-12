---
title: "Lost motification area"
date: 2009-05-24
forum: Desktop Environments
---

### Post by smartroad on 2009-05-24
Sorry me again :oops: It seems I have somehoe managed to loose the notification area on the top right of the netbook remix desktop (9.04). Not sure how I done it, probably clicked on something I shouldn't have! I have lost my wifi meter, the battery and something else I can't remember what was running on it.

Have checked around and have found similar problems, but they seem to apply to the normal desktop and not the remix one. There doesn't seem to be an area on the remix version where you can right click (as many of the suggestiong posted say) and get a menu for the panel itself, only for the areas running on it (ie volume or time/date, as they are still running). I can't find anything in the system programs that will re-enable what I have shut off.

Anyone know how I get it back :(

---

### Post by gettinoriginal on 2009-05-25
I do not use UNR, but found this, hope it helps   :P
[https://answers.launchpad.net/netbook-remix/+question/52637]("https://answers.launchpad.net/netbook-remix/+question/52637")

---

### Post by smartroad on 2009-05-27
Although that didn't work directly for me, I found if I UnLocked a couple from the panel and moved them around it opened up some blank space where I could right click and add again to the panel.

Cheers for the assist! :D

---

### Post by raymondh on 2009-05-28
Now that you have it back and if you are content with what you have in the panel and it's positioning, you may want to lock it down.  Try:

Alt + F2 > gconf-editor > apps > panel > global ... scroll on the right pane to **Locked Down** and tick > exit and enjoy a panel that is locked down.  :)

Best,

---

### Post by smartroad on 2009-05-28
Great thanks :D

---

### Post by RandyNose on 2009-06-22
I just was given an HP Mini, and I had the issues with sound, got those fixed, and switched to the standard desktop environment and only had the desktop background to go on. -  I added a desktop launcher to launch the gnome-terminal, and at the moment I'm doing an 

```
 sudo apt-get install gnome-desktop-environment 
```

I'm hoping when I restart the desktop I'll have some panels etc... I don't know what the command line (s) are to bring the menu, and other items up from the terminal.  

Crossing fingers...

---


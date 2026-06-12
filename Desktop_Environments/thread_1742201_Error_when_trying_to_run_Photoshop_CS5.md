---
title: "Error when trying to run Photoshop CS5"
date: 2011-04-28
forum: Desktop Environments
---

### Post by dctrsatan on 2011-04-28
I am running Ubuntu 10.10 and get the following error after installing Photoshop CS5 Extended.

I uploaded a video of my problem.  I have the latest version of Wine installed if that makes a difference. 

[http://www.youtube.com/watch?v=bYtvUCIohBU](http://www.youtube.com/watch?v=bYtvUCIohBU)

---

### Post by Flash858 on 2011-04-28
CS5 is not going to run under Wine. No possible way. Ever. Period.

 It barely runs under Windows ;)

Your best bet is to install Virtual Box, Set up a Windows VM, and install CS5 there.

I assume you are a relatively new user, so I would encourage you to instead try Gimp to edit photos. I am a professional photographer, and frankly, I do all of my editing there, and only use CS5 for Dreamweaver anymore, as I have gotten so familiar with Gimp that Photoshop is no longer intuitive.

You can install Gimp in the Software Center, or by typing "sudo apt-get install gimp" (without the quotes) in a terminal.

If you have an older version of Photoshop, you could try Codeweavers.com - they have an interface for WINE called Crossover Linux, and I noticed PS7 and CS2 were running fairly well. If you go that route, save early and often. I installed PS7 once to try it, and it ran, but often crashed.

---

### Post by dctrsatan on 2011-04-28
How do you explain this video then?

[http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

That video is the one that i was following.  Please watch it and get back to me.

---

### Post by Tomdarkness on 2011-04-28
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)

It has a Gold rating in WineDB so not sure how you can claim that there is "No possible way."

To the OP: If you check on the howto on the WineDB is suggests that the best way to run PS CS5 in wine is to copy over a installation from Windows as described.

> **Flash858 said:**
> CS5 is not going to run under Wine. No possible way. Ever. Period.

 It barely runs under Windows ;)

Your best bet is to install Virtual Box, Set up a Windows VM, and install CS5 there.

I assume you are a relatively new user, so I would encourage you to instead try Gimp to edit photos. I am a professional photographer, and frankly, I do all of my editing there, and only use CS5 for Dreamweaver anymore, as I have gotten so familiar with Gimp that Photoshop is no longer intuitive.

You can install Gimp in the Software Center, or by typing "sudo apt-get install gimp" (without the quotes) in a terminal.

If you have an older version of Photoshop, you could try Codeweavers.com - they have an interface for WINE called Crossover Linux, and I noticed PS7 and CS2 were running fairly well. If you go that route, save early and often. I installed PS7 once to try it, and it ran, but often crashed.

---

### Post by jcolyn on 2011-04-28
CS5 can run in the latest version of wine. However individual computer hardware can be a determining factor whether or not it will run on your particular computer.

I prefer Gimp myself and since it is native to Linux it will work better and at native speed whereas CS5 in wine may be somewhat slower..

---

### Post by dctrsatan on 2011-04-29
I have fixed this issue.  What i did was downgrade to wine 1.2.1 and it ran perfectly.  I do not know why that person to first reply to my post would say it wouldn't ever run in Ubuntu he must be new.

---


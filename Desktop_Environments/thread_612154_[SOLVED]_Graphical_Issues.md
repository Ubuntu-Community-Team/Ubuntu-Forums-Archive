---
title: "[SOLVED] Graphical Issues"
date: 2007-11-13
forum: Desktop Environments
---

### Post by more14 on 2007-11-13
Hello,

I've been using Ubuntu for almost three months, and I have had quite a few graphical issues since then, but nothing as terrible as what I'm suffering since I upgraded to Gutsy.


I guess it all started with Feisty. The very first days after doing the dual-boot installation, everything went smooth and looked great, but it didn't last long... one day I tried to change the screen's resolution and everything just messed up and crashed. My LCD screen stopped showing output from Linux, though Windows worked as usual. Even the Live CD had trouble to start!

I figured it was a driver issue, and tried lots of different fixes around the net, but finally I was forced to reinstall Feisty, and it partially fixed the issues.

Then Gutsy came around, and my computer has become extremly slow and unusable. This is a brief list of what I have noticed:

[LIST]
[*]Both Firefox and Opera scroll terribly slow
[*]There's a small period between logon and splash screen in which xserver seems to "fail" (cursor becomes an X)
[*]GDM takes more time to load my appearence settings (I can even see the default dark grey bar before switching to ubuntu look)
[*]Some weird horizontal lines appear after opening/closing/moving menus or windows... interestingly, they do show in screenshots
[*]Compiz-fusion animations are very slow... they worked way better in Feisty
[*]The new display manager app fails or crashes xserver after changing resolution.. "Test" button never works
[*]Gtk-dependant applications have ugly scrollbars and irresponsive forms (not related?)
[/LIST]

I hope you may find an answer and a fix for this, because I really think Ubuntu is a great OS, and Gutsy seems a nice improvement except for all this graphical thing. I'm currently considering a full uninstall/reinstall.

---

### Post by Chymera on 2007-11-14
did you downgrade to gutsy or install from scratch?

---

### Post by more14 on 2007-11-14
I upgraded my Feisty install to Gutsy when i was promted to do so. Do you think that might be related?

---

### Post by Chymera on 2007-11-15
yes, it most certainly is, try installing gutsy from scratch (you don't need to delete your current installation) and see if you get the same problems

---

### Post by more14 on 2007-11-15
Ok, at this time I don't have any Gutsy CDs or ISOs, but I'll make an attempt this weekend.

Thanks for your help.

---

### Post by soelk on 2007-11-15
My Gutsy installation has exactly the same symptoms as yours, but it has a different history. Mine is a Gutsy beta install, later updated to final. It worked great until I (successfully) installed the proprietary ATI driver and then uninstalled it (apparently messing something up). 

All I have managed to conclude so far is that it most likely has nothing to do with the xorg.conf file. I'm using an old backup of that. Something else is messed up in the system, somewhere. I bet if you install it from scratch on your computer it will work just fine... 

But I did not do that many changes to my system. I suppose that there must be a simpler way to fix the problem.

---

### Post by more14 on 2007-11-18
Well, I can also ensure it's not a xorg.conf problem. I tried everything I read on the internet about that file, but it didn't fix anything.

Today I've finally decided to reinstall Gutsy. I was thinking of simply overwriting my current installation, but the installer forced me to reformat; so I'm currently using a clean install, and I'm proud to say that all the issues have gone!

Compiz is running smooth and looking cool, and those annoying lines have dissapeared. Firefox scrolls faster than ever, and my qt3-based apps work as they did in Feisty.
I don't know what was wrong with my previous setup, but I agree with soelk that there must be an easier way of fixing this.

EDIT: Found a small glitch, that didn't happen before... My screen is unable to display Ubuntu's boot screen, as it's "Out of range: 43 Hz". Any ideas? I guess it may be related to xorg.conf...
EDIT2: Fixed. It's a known bug. [http://ubuntuforums.org/showthread.php?t=581075]("http://ubuntuforums.org/showthread.php?t=581075")

---


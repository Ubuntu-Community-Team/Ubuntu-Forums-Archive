---
title: "[SOLVED] Apps open, but GUI's are blank."
date: 2007-12-22
forum: Desktop Environments
---

### Post by zyberwoof on 2007-12-22
Ok, my problem is a little hard to describe, but here it goes...

When I open new windows/apps, sometimes they are just the main title bar (with x and minimize and etc.) and then a black box where the normal app GUI should be.  If I click around, the application responds appropriately, so it is not a problem with the apps themselves.  However, often if I reduce the size of the window a certain amount, then the GUI appears.  And then if I enlarge it by either dragging the corner or maximizing then it goes black again.

I noticed that with only a command line window and pidgin open, I was able to maximize Firefox just fine.  Then I opened Amarok and I could not get anything but the blank GUI.  Next, I reduced Firefox to only half the horizontal width of my monitor and reopened Amarok.  This time, Amarok opened just fine.  

It seems like the more windows I have open, the smaller I have to make new windows and the more likely the next application I open won't be show able.

I don't mind providing any more info that would help diagnose this problem.

EDIT:  Also, recently I rebooted my laptop and the Desktop background remained blank.  I'm guessing since several Applications automatically opened since my session was saved.


Ubuntu 7.10
Dell Latitude D800 (Laptop)
nVidia GeForce 4 Ti 4200 Go AGP 8x (64MB) w/ restricted drivers.
1 GB RAM
Centrino 1.7 ghz

---

### Post by zyberwoof on 2007-12-23
Ok, I have sorta found out the problem and a solution.  If I enable the "normal" Compiz Visual Effects, then I have this problem.  However, if I set the Visual Effects to "None", then it works fine.  (To change this setting, go to System -> Preferences -> Appearance -> Visual Effects Tab.)

So, I'm guessing that I should go to Compiz looking for help.  I'll post back if I find a better solution besides disabling all of the eye candy.  If anyone already knows a better solution, feel free to post it on this thread.

---


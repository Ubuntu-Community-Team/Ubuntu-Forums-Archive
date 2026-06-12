---
title: "Menu bar and application launcher disappear"
date: 2011-04-16
forum: Desktop Environments
---

### Post by wnfaulkner on 2011-04-16
I am running 11.04.

My application launcher on the left side and the main menu bar at the top of the screen have disappeared.  When I boot up, all I see is my desktop background and "Computer" icon.

I was messing around with the compiz settings and enabled and then disabled the cube effects.  When I did so I disabled some plugins but can't remember which ones.  

Help!

---

### Post by Frogs Hair on 2011-04-16
I would look at the 11.04 testing forum. [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by wnfaulkner on 2011-04-16
Problem solved.

In terminal:

unity --reset

---

### Post by lgarcias on 2011-05-23
Hi
I have kind of same problem, and the unity --reset solve the problem. But when i switch off and on the pc again, i have same problem and have to write again unity --reset comand. 
How can i make appear the unity laucher for good without using that comand. 

Thanks

---

### Post by Copper Bezel on 2011-05-24
Is the Unity plugin enabled in CompizConfig? (If "CompizConfig" doesn't ring any bells, run [font="Courier New"]sudo apt-get install compizconfig-settings-manager[/font], then search in the Dash for CompizConfig.)

Check if the Unity plugin is enabled. If it is already, then check out this [troubleshooting guide]("http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html").

---

### Post by lgarcias on 2011-05-24
Thanks very much, the compiz thing was ok, so i followed the troubleshooting steps and now it seems to work fine.

---

### Post by djpurity on 2011-05-24
> **lgarcias said:**
> Hi
I have kind of same problem, and the unity --reset solve the problem. But when i switch off and on the pc again, i have same problem and have to write again unity --reset comand. 
How can i make appear the unity laucher for good without using that comand. 

Thanks

How did you get the Terminal to appear? I can't seem to figure that part out without the LAUNCHER on the side to make it appear or something like the PLACES on the top bar.... both are missing. Is there a hot-key for it, or a short-cut for getting the Terminal open to enter the reset for Unity? Thanks!

:KS

---

### Post by djpurity on 2011-05-24
Oh nevermind I got it. Ctrl+Alt+F1 gets you into a terminal, and Ctrl+Alt+F7 gets you back to the main screen. This involves  Unity and Compiz. Okay I am getting it now! Nervermind!

I FIXED IT TOO! I had to go through the troubleshooter in the Ubuntu for Beginners link [http://bit.ly/j8nOtD](http://bit.ly/j8nOtD) which led me through the whole process to get the Unity plug-in working and the wall and all that, and not the cube! :-V

---

### Post by sikander3786 on 2011-05-25
> **djpurity said:**
> Oh nevermind I got it. Ctrl+Alt+F1 gets you into a terminal, and Ctrl+Alt+F7 gets you back to the main screen. This involves  Unity and Compiz. Okay I am getting it now! Nervermind!

I FIXED IT TOO! I had to go through the troubleshooter in the Ubuntu for Beginners link [http://bit.ly/j8nOtD](http://bit.ly/j8nOtD) which led me through the whole process to get the Unity plug-in working and the wall and all that, and not the cube! :-V

You couldn't get the cube working? Did you check out the steps in this post?

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---


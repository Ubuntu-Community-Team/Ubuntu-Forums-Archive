---
title: "Beryl Manager"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by kyldere on 2007-04-27
Well, I updated to 7.04 and got Beryl working. My problem is as such: I have the Beryl icon (the red gem) in my applets panel, but when I right-click on it, there is no Beryl Settings manager (I think that is what it was called). It was right next to the Emerald Theme Manager, but now it does not show up. Without this option I cannot change my Beryl settings (minimize/maximize animations, number of cube sides, images for cube top/bottom, etc) without going in and manually setting the config file. Is anyone else having this issue or know of a workaround? Thanks in advance for the help.

---

### Post by stinkypudding on 2007-04-27
Try clicking Applications-System Tools.....Beryl Manager should be there.

---

### Post by kyldere on 2007-04-27
It is there. However, the options are the same as the one in the applet tray. Unless I am missing something obvious (it wouldn't be the first time), I cannot see any way to configure the Beryl settings. There used to be an option right above or below the "Emerald Theme Manager" (I can't remember which) for Beryl Settings. That is now gone. That is the problem.

---

### Post by kyldere on 2007-04-27
Here is a screen capture of my Beryl Manager. Where has the Beryl Settings option gone?

---

### Post by Guns90 on 2007-04-27
Hi Kyldere,  I just got beryl working on my system.   I'm sure you must have installed the emerald-themes.  Did you add the beryl-manager to  System > Preferences > Sessions?

---

### Post by andremichi on 2007-04-27
Kyldere, do you have solved this problem ? 

I have the same trouble with beryl-manager.

Sorry my poor english.. 

[]'s

---

### Post by andremichi on 2007-04-27
Solved.

sudo  apt-get install beryl-settings

I think this package is installed by default when i do: apt-get install beryl beryl-manager.

regards

---

### Post by kyldere on 2007-04-30
CONFIRMED SOLUTION

You were correct.
sudo aptitude install beryl-settings beryl-manager

And a reboot fixed the issue, although it might have been fixed with a simple restart of X. Thanks again for the help.

---


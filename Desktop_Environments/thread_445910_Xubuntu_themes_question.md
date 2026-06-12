---
title: "Xubuntu themes question"
date: 2007-05-16
forum: Desktop Environments
---

### Post by icarus128 on 2007-05-16
Hi all, I couldn't find a dedicated Xubuntu forum so sorry if this is in the wrong place.  
I recently installed Xubuntu feisty on my laptop and have been playing around with different themes trying to find what I like.  I have run into a couple themes (the most popular one is the OS X Aqua theme and icon set) that do not work properly.  In the case of the OS X theme I have the option in "user interface settings"  to use them, and that changes the way windows look internally and the icons that are used, but I do not have the option in "window manager settings" to select this theme, so window borders and the menus along the top are not consistent with the rest of the theme.  But the theme is supposed to handle this as well.  

Can anyone tell me what is going on?  I've been able to find a fair number of people with this problem but no working fix.  Thanks in advance :)

---

### Post by LuisGMarine on 2007-05-16
Sounds like the metacy theme didn't get installed properly.  Try re-downloading the package and reinstalling the themes, just grab the tared up file and drop it on the Theme Manager window.

Another thing you can do is just download the similar Metacy theme by itself.  Just head over to [gnome-look.org]("http://www.gnome-look.org") and under metacy, search for something that looks like the one provided in the screen shots for the Aqua theme.  I'm sure if you click on the " most downloaded " or " highest rated " you will find a MacOSX type of window border.

---

### Post by Ptero-4 on 2007-05-16
The problem for the OP is that he is using XFCE (xfwm4 and not metacity). To have consistant theme in the WM the OP needs to install the xfwm4-themes package and select the apropiate ¨Aguamelon¨ WM theme from the two in the list (the first emulates OSX10.2 and earlier, the second emulates OSX10.3 and later).

---

### Post by icarus128 on 2007-05-16
yup, got it working.  Thanks all!

---


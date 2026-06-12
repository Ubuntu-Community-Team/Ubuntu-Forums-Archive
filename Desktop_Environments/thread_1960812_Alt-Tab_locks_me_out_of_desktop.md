---
title: "Alt-Tab locks me out of desktop"
date: 2012-04-18
forum: Desktop Environments
---

### Post by Riklurt on 2012-04-18
So, I just recently switched to Ubuntu 11.10, and I've run into a really strange issue. Everything works fine, but if I have multiple windows open and try to use Alt-Tab to switch between them, I lose access to the desktop. The bar containing applications (appeared to the left in the default installation, and I haven't changed it) disappeared, and I can't reach the menu to shut down the computer up top. Near as I know, I haven't changed anything from the default installation yet - I've only been using the computer for one day.

I've tried a few things, and keyboard shortcuts do seem to work - I can log out and log back in, in which case the menus re-appear - but I can't click anything that isn't in the window I currently have open. What's wrong, and how do I fix it?

(I've previously used Ubuntu 10 in various versions, but this is the first time I try 11)

---

### Post by Abhix555 on 2012-04-18
From what I gather, I guess there is a problem with Unity... Open a terminal and type in 'unity --reset' and reset your Unity interface. This should solve the problem. Note that all the changes you have done using compiz will be wiped out.

---

### Post by Riklurt on 2012-04-19
I tried this, and got the error message "Segmentation Fault". Despite this - perhaps for unrelated reasons, I'm not sure - the problem disappeared for a little while, but it returned when I rebooted the computer.

I'm at a total loss as to what's going on here, any idea? I've done a bit of testing, and it seems the problem only occurs when I'm trying to switch between windows that are currently in full screen, apparently.

---

### Post by jba3 on 2012-04-19
Using Unity or gnome? I've seen this happen with Compiz. If you're using Compiz, it's conflicts with the app switcher plugins.

---

### Post by Riklurt on 2012-04-21
Using Unity. Some sort of conflict with app switcher plugins seems pretty reasonable; I've done some experimenting and the problem seems to arise with certain applications only (or at least, more than others).

---

### Post by jba3 on 2012-04-29
Try disabling the regular 'App Switcher', and enable the 'Static App Switcher' in CompizConfig.

---


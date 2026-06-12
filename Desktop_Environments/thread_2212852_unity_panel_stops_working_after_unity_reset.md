---
title: "unity panel stops working after unity reset"
date: 2014-03-23
forum: Desktop Environments
---

### Post by 6QXLBpz on 2014-03-23
I just upgraded from 12.04 to 13.10.  Since I did so, every so often (actually, more than once per day--it's pretty annoying) unity/compiz will lock up and I have to reset it by switching to a terminal (i.e. ctrl+alt+f1) and running unity --replace.  This gets my desktop back, but unity panel doesn't work anymore; it displays the name of the program that's active, but when I mouseover the top bar, I don't get any menus.  The unity panel icons like the system monitor, volume control, clock, the ststem menu that lets you log out/shut down are all missing; the bar is empty except for the application name.  Killing/restarting unity-panel-service will make the menus appear temporarily in their respective windows, but once it's finished restarting, they disappear again and I'm left in the same state.  The only solutions I have so far are to reboot, or to run unity --reset-icons, (which destroys the customizations I've made to the task bar).  Are there any other approaches to resetting unity panel service without resetting my customizations?

---

### Post by deadflowr on 2014-03-23
I don't think unity --replace is an actual command.
And also, the methods to reset unity changed and differs from the methods done in 12.04.
Here's how to do it in 13.10
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---


---
title: "lose window borders?"
date: 2009-11-07
forum: Desktop Environments
---

### Post by windowsfree on 2009-11-07
Why is it I lose my window borders when I change my desktop effects from none to advanced?  I lose the ability to minimize open windows when I have that on.  I noticed also, my compiz settings don't always save.  I was showing some one the rotating cube effect and when I powered on my computer at a later time, my desktop cube and all the settings were unchecked.  I have attached a screenshot of the open window with the border missing.  I do have the window decorations box checked in the compiz settings.
Thanks to all that respond

---

### Post by Abhijit Navale on 2010-02-01
Hey, You mark this thread as SOLVED.
But where is the solution?

I also have the very same problem.
Please let me know if you have any solution?

---

### Post by Leshrac on 2010-02-01
> **Abhijit Navale said:**
> Hey, You mark this thread as SOLVED.
But where is the solution?

I also have the very same problem.
Please let me know if you have any solution?I don't know if this will solve your problem but the desktop effects FAQ states:

> **Where did my window borders go? - cc7gir**

    This is a common mistake caused by disabling some plugins in CompizConfig Settings Manager. To fix, open the manager (System > Preferences > CompizConfig Settings Manager) and find the "Window Decorations" plugin. Check the box and you're all set.

---

### Post by Linux God on 2010-02-01
The problem is you are not using compiz, you are probably using metacity.
To fix this, open a terminal and type gconf-editor. then navigate to 
apps > general > Metacity > general. then unclick the compositing_manager box. pm me if this doesent work. or just post in the forum here.

---

### Post by Abhijit Navale on 2010-02-05
I am not using metacity.
I am using compiz

---

### Post by Linux God on 2010-02-05
Did you install anythng that might change the graphics? such as Mac4Lin?
If not install Compiz fusion icon. run it by going into applications > system tools > compiz fusion icon, then it will appear in the top-right of the your upper panel(by default) then right click the icon, then hit compositing manager and switch between compiz and metacity and see which works

---

### Post by Abhijit Navale on 2010-02-05
> **Linux God said:**
> Did you install anythng that might change the graphics? such as Mac4Lin?
NO
Not Mac4Lin
But some windows borders, icon themes, wallpapers using "Art Manager"
...and also some more softwares but (I think) they are not directly related to graphics. (e.g. Istanbul Desktop Session Recorder, etc.)
> **Linux God said:**
>  If not install Compiz fusion icon. run it by going into applications > system tools > compiz fusion icon, then it will appear in the top-right of the your upper panel(by default) then right click the icon, then hit compositing manager and switch between compiz and metacity and see which works
After doing this, by default compiz was selected, so I selected metacity, but the problem remains as it is - i.e. not opening "Computer"

And thnx [Leshrac]("http://ubuntuforums.org/member.php?u=47687"), it was my one of many problems and It solved :) , but other are still there :| .

---


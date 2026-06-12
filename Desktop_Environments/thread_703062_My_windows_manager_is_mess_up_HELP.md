---
title: "My windows manager is mess up HELP"
date: 2008-02-20
forum: Desktop Environments
---

### Post by sparq on 2008-02-20
My windows manager has been totally ruined. I just tryed installing compiz xgl on my set up but then tryed getting rid of it by un-installing the packages. but I guess it also messed up my windows manager idk what to do.

I followed this tutorial btw after attempting to uninstall
[http://ubuntuforums.org/showthread.php?t=488385]("thread 488385")

---

### Post by MCrittenden on 2008-02-21
We're going to need a little more information. What happens when you log in? What are your computer's specs, especially the video card?

---

### Post by sparq on 2008-02-21
it was working at one time, its not a hardware thing. I had a windows manager (compiz xgl) then I deleted it so now I cant move windows around. When I start up (after the login screen) everything seems normal but when I open a window the top bar is gone and the windows just stay where ever they open. Its really hard to navigate, you can't have two things open on the same place and access both of them without closing one or the other. I don't know what to do I tryed installing an alternative WM (windows manager) but it won't open just like compiz wasn't opening which is why I uninstalled.

---

### Post by MCrittenden on 2008-02-22
After you log in, open a terminal and type:

metacity --replace

And hit enter. That will hopefully run the default window manager (i.e., metacity) again.  If so, all we need to do is make it run that command at startup, which is really easy.

---


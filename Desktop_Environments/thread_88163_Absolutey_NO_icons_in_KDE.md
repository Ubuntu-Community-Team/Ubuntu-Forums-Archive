---
title: "Absolutey NO icons in KDE"
date: 2005-11-09
forum: Desktop Environments
---

### Post by flipkick on 2005-11-09
I'm sorry folks, there it comes again.
Today I switched to the KDE Desktop environment at my workplace. I tried the same at home an installed the "Kubuntu-desktop" package.

Unfortunately KDE is displaying no single icons anywhere. I'm using GNOME at the moment and everything works fine.

So i looked through the forums around here and google. I came to something that has to do with "ONLYShowIn=KDE" , "gdm.conf" and "kdm.conf" or maybe the desktop.conf is not set right. Might be that KDE is trying to read the icons from "/usr/share/icons/ where only root has rights....

I just don't know where to begin and where to stop. I guess its a more serious problem as i updated from hoary to breezy and alsways used gnome.
before the update it somehow worked someday, but i didn't like KDE at that time. I even like it less with no single icon displayed.

I'm sorry to annoy you with a problem, that might be minor to the whole thing, but for me it is of importance, cause i don't want to install Ubuntu or Kubuntu from the very beginning.

Can someone please post his genious ideas ?

Thanks a lot !


[COLOR="Red"]Edit:[/COLOR] "sudo chmod 755 /usr/share/icons/" solved the problem.

---

### Post by daller on 2005-11-23
Please don't just edit your post, when it's solved!

Add a new post to it, so that the system can see it has been answered...

I'm trying to keep the number of unanswered kubuntu threads at a minimum.

Seaching the forum for unanswered threads, also find posts like these...

---

### Post by flipkick on 2005-11-23
Alright, good to know ;) 

So guys, this one has been solved. Checkout the Edit in my first post :rolleyes:

---


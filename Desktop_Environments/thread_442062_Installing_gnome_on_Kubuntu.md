---
title: "Installing gnome on Kubuntu?"
date: 2007-05-13
forum: Desktop Environments
---

### Post by happysmileman on 2007-05-13
I'm using Kubuntu and liking it, but I would also like to know if I could use Gnome as well, without having to install a new OS.

I've looked through the package manager and found gnome, which install a lot of other important looking stuff, takes 128MB download and 533MB install.

So it appears to be the right size and all, so my question is, how does it work? Is their an option at login or does it try to integrate with KDE at same time?

Oh, and is their any problems I should look out for, or stability issues?

---

### Post by mthakur2006 on 2007-05-13
hi,
i don't know about the package gnome, but the package ubuntu-desktop should install gnome with all the programs for you.
At the login screen, under the menu 'options', there will be an option for you to allow you to switch to gnome.
No stability issues are known to me at this point about it, but when you install ubuntu-desktop, all the gnome programs start to appear in you KDE menu and vice versa. You can edit it by using the Kmenu editor though.

The code for ubuntu-desktop is ```
 sudo aptitude install ubuntu-desktop 
```
thanks.

---

### Post by happysmileman on 2007-05-13
It works... But I can't change the theme on Gnome now... The theme manager just doesn't respond to anything you do

---


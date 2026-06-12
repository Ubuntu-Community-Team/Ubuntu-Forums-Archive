---
title: "flux on ubuntu"
date: 2009-01-28
forum: Desktop Environments
---

### Post by josephcohen on 2009-01-28
My machine is very old and slow so I want to put fluxbox on it.
How do I do this? Does it work the same way as if i was putting xcfe onto ubuntu? And does it delete or change any of my files or programs or settings?

---

### Post by icanfly0307 on 2009-01-28
*sudo apt-get install fluxbox* should do the trick. However, you'll positively freak out when you first login to fluxbox. It's got no icons, background, etc. Just an ugly panel with the time on the bottom. My recommendation would be to install Fluxbuntu. It looks more professional and it uses the same repos as Ubuntu.

[http://www.fluxbuntu.org/](http://www.fluxbuntu.org/)

Hope this helps...

---

### Post by josephcohen on 2009-01-28
> **icanfly0307 said:**
> *sudo apt-get install fluxbox* should do the trick. However, you'll positively freak out when you first login to fluxbox. It's got no icons, background, etc. Just an ugly panel with the time on the bottom. My recommendation would be to install Fluxbuntu. It looks more professional and it uses the same repos as Ubuntu.

[http://www.fluxbuntu.org/](http://www.fluxbuntu.org/)

Hope this helps...

The problem is I can only get my internet to work in ubuntu and I dont want to try in fluxbuntu. I have tried it before.
If i right clcik the desktop in flux will it show all the programs I already have? And can I add a background?

---

### Post by Flotter on 2009-01-29
> **josephcohen said:**
> The problem is I can only get my internet to work in ubuntu and I dont want to try in fluxbuntu. I have tried it before.
If i right clcik the desktop in flux will it show all the programs I already have? And can I add a background?

Correct to the first.  Right-Click in the desktop brings up the main window.  The default menu has a bunch of default applications listed on it, but not everything you have.

Fortunately, editing a new menu is a piece of cake.  Just put the new menu into ~/.fluxbox/menu after editing it with your favorite tool.

---

### Post by snowpine on 2009-01-29
If you have problems with the application menus not updating in fluxbox/fluxbuntu:

```
sudo update-menus
```

There are several ways to set the background in Fluxbox. Fluxbuntu uses the Rox file manager for this task (which I personally find awkward). I recommend using the fbsetbg command in your fluxbox startup file, ~/.fluxbox/startup I believe (I'm on a different computer at the moment).

---

### Post by snowpine on 2009-01-29
ps Network connections in Fluxbox are exactly the same as in "regular" Ubuntu. Try nm-applet (assuming network-manager is installed) or wicd, for example.

---


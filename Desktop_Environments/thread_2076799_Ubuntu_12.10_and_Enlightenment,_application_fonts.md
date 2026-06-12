---
title: "Ubuntu 12.10 and Enlightenment, application fonts"
date: 2012-10-27
forum: Desktop Environments
---

### Post by tomns on 2012-10-27
I upgraded to 12.10, amd64, on a lenovo ThinkCentre M91p.  In 12.04 I had no problem, but now the fonts in applications like synaptic and empathy do not honor the font selections I specify in gnome-tweak-tool.  If I set the fonts, nothing changes in enlightenment, though if I log into unity the fonts are as I set them.  I do have gnome-settings-daemon running.  I tried removing and reinstalling the e17 packages but nothing changed.  What else can I try?  Thanks.

---

### Post by 2F4U on 2012-10-27
I am no expert in Enlightenment, but I would guess that Enlightenment and Gnome do have seperate configuration files. So, configuring Gnome with gnome-tweak-tool has most likely no effect on Enlightenment, since it is a different desktop environment. It would most likely be the same with KDE.

---

### Post by tomns on 2012-10-27
I've been using enlightenment exclusively for several years, and I have been able to adjust the fonts using gnome tools.  I don't really understand how that works, but I know that in the past, gnome-settings-daemon did need to be running for it to work.

---

### Post by Frogs Hair on 2012-10-27
The E17 core packages in the repository are limited and outdated. If you would like have the ability to add modules I  would suggest an svn  PPA.   

[http://www.itworld.com/software/307124/install-enlightenment-e17-ubuntu-1210](http://www.itworld.com/software/307124/install-enlightenment-e17-ubuntu-1210)

**Caution:**  Remove all E17 packages installed from the Ubuntu repository before adding this PPA or you will have broken packages!  The PPA packages are much more up to date . 

I would suggest removing  the .e folder in home/ hidden folders and  create a new profile if you install the PPA . A new folder will be created during installation.

Install the synaptic package manager for adding modules you want such as weather and so on.

---

### Post by tomns on 2012-10-27
I had found that page and did re-install it based on the instructions (and you are right about the broken packages - it took me a couple of go-arounds to clean that up).  But I had not deleted my old configuration directory.  So I tried that.  The interface has more eye-candy now and there are more features available than I had before, but the fonts are still too large in synaptic and eclipse.

Does enlightenment have its own font-setting app?  I couldn't find one.

---

### Post by tomns on 2012-10-27
Found it in the settings panel.  Everything is good.

---

### Post by vaskark on 2013-03-14
> **tomns said:**
> Found it in the settings panel.  Everything is good.
Can you be more specific? i just install E17 svn on ubuntu raring and have the same trouble with fonts in gnome apps. This used to be solved by having gnome-settings-daemon running, which I do. But gtk apps still look terrible.

---

### Post by carl.davis on 2013-03-27
> **tomns said:**
> Found it in the settings panel.  Everything is good.

Any possibility of more specificity here because I would really like to fix this as well.

---


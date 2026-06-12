---
title: "Gnome Shell Broken"
date: 2013-05-10
forum: Desktop Environments
---

### Post by jim_deadlock on 2013-05-10
I was previously using Gnome Shell 3.8 from the gnome3 repository but I wanted to go back to 3.6 so I removed the repository and reinstalled gnome-shell but when logged in it doesn't display any panel or launcher or anything, just desktop pattern. I've completely reinstalled the system and kept my /home partition but still the same problem, so I'm assuming I need to delete a config folder to get it working again. I've tried deleting ~/.gnome but still no joy. Any suggestions?

---

### Post by Frogs Hair on 2013-05-10
I see a gnome session folder in .config, but it is empty on my installation and appears to be for saved sessions. Not having used a separate home partition I am not sure what is saved from the previous installation, is it  home folders and hidden only or are there folders from the root file system as well ?

---

### Post by jim_deadlock on 2013-05-11
My root filesystem is completely fresh, and I've also tried installing the system with a new /home - in which case it works fine. So I'm 100% sure that something in my original /home is causing the problems, if I could just find out what to remove I would be fine. If nobody knows then I suppose I'll have to use a new /home and manually copy the folders over one by one, but I'd rather avoid that if possible because I have a not of stuff!

---

### Post by kurt18947 on 2013-05-11
I'd guess the problem resides in some hidden config file, the question is which one?  Did you start with a standard Ubuntu install then added gnome-shell?  Have you tried removing gnome-shell then rebooting?  After the restart reinstall gnome-shell.

---

### Post by jim_deadlock on 2013-05-11
Yes I did originally add gnome-shell to the standard unity system and then I upgraded it to 3.8 from the gnome3 repository so it's all a bit of a mess really. I have tried removing it, rebooting, reinstalling several times but unfortunately the installation doesn't overwrite any existing config files in /home so the problems persist whatever I do. Anyway, I'm now moving my old /home to make room for a new one and then I'll gradually copy stuff over so by process of elimination I should eventually find out which folder was breaking it. The partition move is taking 7.5 hours on my 2Tb drive! Should have done it overnight bah!

---

### Post by Frogs Hair on 2013-05-11
I just gave 3.8 a try again and after using the ppa purge I found zenity, nautilus and a number packages were still 3.7 or 3.8 and I have been sorting it out for an hour or so with synaptic . You may have used a different ppa, but check you package versions.

---

### Post by jim_deadlock on 2013-05-12
What I did in the end was a complete Ubuntu reinstall (minimal) with a fresh /home as well, then installed lightdm and gnome-shell as usual. Lo and behold, I got the same thing as before - desktop wallpaper + mouse cursor and nothing else, no panel and no launcher. I wasn't expecting this with a fresh install. So I checked .xsession-errors and noticed that it was complaining about gnome-screensaver missing, so I installed that and it fixed the problem finally.

I have no idea whether this was the same problem I had originally with the old /home partition, it may have been something completely different, but hopefully this may help somebody reading this in future.

---

### Post by markbl on 2013-05-12
> **jim_deadlock said:**
> What I did in the end was a complete Ubuntu reinstall (minimal) with a fresh /home as well, then installed lightdm and gnome-shell as usual. 
Something is odd in your recollection here though because clearly lightdm is already included in a normal Ubuntu install?

---

### Post by jim_deadlock on 2013-05-13
No, it's not included in minimal install: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---


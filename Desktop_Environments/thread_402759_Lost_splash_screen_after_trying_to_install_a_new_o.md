---
title: "Lost splash screen after trying to install a new one"
date: 2007-04-06
forum: Desktop Environments
---

### Post by rvbhute on 2007-04-06
I tried to install a custom splash screen from [http://gnome-look.org/content/show.php/Sleek+Dragon+for+Usplash?content=51556](http://gnome-look.org/content/show.php/Sleek+Dragon+for+Usplash?content=51556)

However, now I neither get the default Ubuntu splash screen nor the new one. I just see the text in the startup/shutdown screen.

At this step 
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
I get the follow error
```
Searching for splash image ... none found, skipping ...
```
which I think is the root of my problem. How do I install the new splash screen or atleast get the default back?

Just to clarify, by splash screen, I mean the one after grub menu and before login screen.

---

### Post by johnny_b_good on 2007-04-06
i've the same problem...i tried to uninstall usplash and reinstall it but nothing changed

---

### Post by rvbhute on 2007-04-06
Problem solved - mostly. Try [http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

I've decided the default theme is very good - uh-huh, yup! No more fiddling around.

---


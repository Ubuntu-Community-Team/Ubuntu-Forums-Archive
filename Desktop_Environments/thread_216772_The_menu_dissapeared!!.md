---
title: "The menu dissapeared!!"
date: 2006-07-16
forum: Desktop Environments
---

### Post by german640 on 2006-07-16
I'm using Xubuntu, and when I wanted to edit the menu with the option "Edit Menu" under settings, nothing happened and now I don't have menu, I press the "Applications" button and nothing happen, and also if I do right-click on the desktop. 

¿Any ideas of what's going on?

---

### Post by skatta on 2006-07-16
I just had the same thing happen to me - it's apparently a bug in xfce and is listed in the release notes for xubuntu.

I found advice as to how to solve the problem here :

[http://www.harecoded.com/2006/06/13/xubuntu-ive-lost-the-menu](http://www.harecoded.com/2006/06/13/xubuntu-ive-lost-the-menu)

However in order to be able to carry the advice out out I had to add the verve command line to the panel and then use that to open the default file manager Thunar.

I could then navigate to the locations in the advice at the above page using the 'open location' option on the go menu in Thunar. 

I deleted the corrupted file 'menu.xml' at 

~/.config/xfce4/desktop/menu.xml

and copied over the replacement file 'menu.xml' at

/etc/xdg/xfce4/desktop/menu.xml

to replace it. I then exited xfce, restarted it and the menu was back.

---

### Post by dolby on 2006-07-16
u need to update your distro as soon as u login for the 1st time. the menu thing was a bug that got fixed

---

### Post by german640 on 2006-07-16
Thank you! it worked perfectly! :cool: 

And I don't have internet access so I can't update the distro, I found that if you don't have internet access the use of Ubuntu is REALLY ANNOYING in the case of installing software because you can't use the repositories.
Is Ubuntu slave of the internet? [-(

---


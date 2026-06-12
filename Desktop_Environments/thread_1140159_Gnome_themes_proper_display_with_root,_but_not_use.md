---
title: "Gnome themes: proper display with root, but not user accounts?"
date: 2009-04-27
forum: Desktop Environments
---

### Post by imstr8trippin on 2009-04-27
This seems to be the opposite of what most people experience. I'm trying to use the dust theme. I have .themes/Dust installed in both root and my user home directories. But, the theme only displays correctly for the root user. Namely, the menu bar font color, toolbar background and font colors, and scrollbar colors are not showing up correctly. When running apps as root, all is fine.

Any thoughts?

---

### Post by imstr8trippin on 2009-04-27
just realized that the .themes directory in /root is a link. Now, I'm even more stumped. :S

I also did:
chmod +x -R ~/.themes/Dust
sudo chmod +x -R /usr/share/themes/Dust

and still...nothing. wtf?

** UPDATE **
Also did: 
chmod +w -R /usr/share/themes/Dust
rm -fR ~/.themes/*

Same crap. :S

---

### Post by imstr8trippin on 2009-04-27
I think it was clearing out ~/.themes that solved the problem. I noticed that after that was done, some apps were showing properly. Just needed a reboot to fix the desktop environment. Maybe some kind of bug? I don't know. Maybe I'll try to figure out what was wrong sometime.

---


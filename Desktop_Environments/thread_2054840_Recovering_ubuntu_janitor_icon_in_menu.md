---
title: "Recovering ubuntu janitor icon in menu"
date: 2012-09-08
forum: Desktop Environments
---

### Post by claracc on 2012-09-08
Recently upgraded my hp compaq 6720s laptop from 10.04 to 12.04.

After trying to get used to unity, I didn't like, and now using gnome fallback very comfortable.

One of the problems I have is, however, I have lost the icon for ubuntu-janitor in the ubuntu menu, under system tools, administration.

How can I recover the icon in the menu?, where is this icon , in order to attach it in the launcher?

Thanks in advance

---

### Post by deadflowr on 2012-09-08
Do you mean computer janitor?
That package was removed from the default installation because it was causing too many people to inadvertently delete packages, and subsequently bork their systems. However, I believe it is still in the repos.

---

### Post by claracc on 2012-09-08
Yes, computer-janitor, sorry. As I upgraded from 10.04 and it was installed, for this reason, I suppose it remains in my system.

This program have bee  working very well for me, the only problem now is I have lost its icon in menu (in the upgrading process). Where can I look for it in order to add it to the ubuntu menu?

---

### Post by claracc on 2012-09-08
Well, it is solved.

Thanks deadflowr, you gave me the key to recover the icon.

Efectively, I have the package computer-janitor-gtk installed. In synaptic, I have looked for the propertie of the package, and see the installed files. I see I have two images for this package: 

/usr/share/computer-janitor/computerjanitor-24x24.png
/usr/share/computer-janitor/computerjanitor-256x256.png

I have openned the launcher in the menu, I have double cklicked on the icon and I have selected one of the images: 

/usr/share/computer-janitor/computerjanitor-256x256.png

Now I have recovered the icon for computer janitor in the ubuntu menu.

---


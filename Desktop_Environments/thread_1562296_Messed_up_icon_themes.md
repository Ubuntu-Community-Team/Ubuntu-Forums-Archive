---
title: "Messed up icon themes"
date: 2010-08-27
forum: Desktop Environments
---

### Post by sikander3786 on 2010-08-27
I have got no experience whatsoever with gnome. All the icons got messed up on my friends computer when he installed "gnome-art" and downloaded a few themes through it. How to fix?

---

### Post by quixote on 2010-08-29
Have the icons been lost no matter which theme he selects?  In other words, it looks like he's selected "Radiance, dark" or something similar, selected "customize" and clicked the icon tab.  But if he selects, say, "Clearlooks" and does the same thing, are all the icons blanked out like that?

I've never had this problem, and I don't know what is the "right" way to fix it.  But what I would do is boot from the liveCD using "try" NOT "install" ubuntu (:D), and mount his hard drive system partition.  On the CD, navigate to /usr/share/icons/and-whichever-subset-you-want, and then copy all the icons there into the same directory in his system partition.  Or, if he just wants all the default icons, copy them all.

---

### Post by sikander3786 on 2010-08-31
Yes the icons look the same no matter which icon or gtk theme is selected.

I thought of downloading the Ubuntu's default icon themes from the gnome-look and replace the one's in /usr/share/icons and forgot that the live cd has got those icons.

Thanks for the tip. **It worked.**

---

### Post by quixote on 2010-08-31
Good to hear! :D

---

### Post by LuniTux on 2010-09-22
YAY!!!! This worked for me too

---


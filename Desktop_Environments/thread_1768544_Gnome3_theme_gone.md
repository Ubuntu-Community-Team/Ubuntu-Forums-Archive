---
title: "Gnome3 theme gone"
date: 2011-05-26
forum: Desktop Environments
---

### Post by higashi on 2011-05-26
My update manager popped up today and requested that I do a partial upgrade, so I did.

After this partial upgrade I noticed some changes in Gnome 3:

-my touch pad disables while typing, which i usually like, but it disables for way too long afterward (so i disabled this feature)

-the Gnome 3 theme is gone. I first noticed this when my background was just blue, and then noticed more when all my programs looked hideous. I went to Desktop Background settings in an attempt to set it back to the default background, but it wasn't even there. As for the theme, I don't even know how to go about fixing that.

-everything was slower. this, however, may just be because it was my first boot after the update (or maybe my imagination). this isn't a big issue.

My main problem is with the theme. How can I get the default Gnome 3 theme back? I tried searching google for the default theme, figuring that i would just download and install it, but I couldn't find it.

Also, how can I get my touch pad to disable while I'm typing, but for a reasonable amount of time?

TIA

---

### Post by maverick280857 on 2011-05-27
> **higashi said:**
> -the Gnome 3 theme is gone. I first noticed this when my background was just blue, and then noticed more when all my programs looked hideous. I went to Desktop Background settings in an attempt to set it back to the default background, but it wasn't even there. As for the theme, I don't even know how to go about fixing that.

If you were using user theme extensions, then this post might help

[http://ubuntuforums.org/showpost.php?p=10865905&postcount=84](http://ubuntuforums.org/showpost.php?p=10865905&postcount=84)

Basically you have to update the shell-version attribute of each extension you wish to use with the new gnome shell version 3.0.2 (which the partial upgrade seems to have gotten us to).

---

### Post by higashi on 2011-05-27
Thanks, but I don't understand any of this lol.

Can someone please provide me with the exact steps to take please?

---

### Post by higashi on 2011-05-28
solved using [this page]("http://nirajsk.wordpress.com/2011/04/27/upgrading-to-gnome3-ppa-on-natty-resolved/")

one thing it didnt mention is to change the "current theme" in the Windows section of gnome tweak to Adwaita

---


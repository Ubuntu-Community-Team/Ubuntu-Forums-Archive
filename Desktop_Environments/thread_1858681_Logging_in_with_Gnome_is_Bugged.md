---
title: "Logging in with Gnome is Bugged"
date: 2011-10-12
forum: Desktop Environments
---

### Post by Jdogzz on 2011-10-12
I have Ubuntu 11.10 right now and so far it's been working great. However, when I started to try out the other environments besides Unity, when I logged in with Gnome the screen would flicker and looked generally broken, as in the attached picture. Is there anything I can do to fix this?

---

### Post by Alwimo on 2011-10-12
Well, the pink top bar may be an issue with the gnome shell config files but I'm not sure where you can find the originals to put into the gnome-shell folder.
 
The window theme can be fixed by installing gnome-tweak-tool and changing the window theme. You may need to log out and back in to see the changes.

---

### Post by Jdogzz on 2011-10-12
The theme is the one I set myself, so I have that much under control:) And I installed that tool yesterday so I mess with it sometimes:)

Could I do something like
> sudo apt-remove gnome-shell
followed by
> sudo apt-get gnome-shell?

---

### Post by Alwimo on 2011-10-12
I would try sudo apt-get autoremove gnome-shell as I think that would remove the config files as well, but I'm not sure if that's what I'm thinking of.

---

### Post by Jdogzz on 2011-10-12
I tried that command, it removed gnome-shell and the tweak tool. I rebooted and then installed them again via synaptic. I rebooted again and I still have the flickering screen and messed up bar, except now it's blue:) It's in the attached picture. Any other ideas on how to fix this?

---

### Post by Alwimo on 2011-10-12
Perhaps you could install another Gnome Shell theme you like and see how it looks after restarting.
 
[http://gnome-look.org/index.php?xcontentmode=191&PHPSESSID=34c38311237d7f34d35c78f87e37888b](http://gnome-look.org/index.php?xcontentmode=191&PHPSESSID=34c38311237d7f34d35c78f87e37888b)

---

### Post by Jdogzz on 2011-10-13
I tried installing the theme here:
[http://0rax0.deviantart.com/art/GNOME-Shell-Nord-214295138](http://0rax0.deviantart.com/art/GNOME-Shell-Nord-214295138)
using this method:
[http://www.techdrivein.com/2011/09/top-10-gnome-shell-themes.html](http://www.techdrivein.com/2011/09/top-10-gnome-shell-themes.html)
and I got the new theme but also the same broken looking bars and menus as before, and the flickering screen, shown in the attached picture:(

---

### Post by sogasg on 2011-10-13
I have the same problem :'(

---

### Post by Jdogzz on 2011-12-11
Finally figured out what's causing this. If you activate the ATI driver in Additional Hardware it causes Gnome to break. Deactivating it should fix whatever problems you have.

---


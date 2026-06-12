---
title: "Gnome shell disappears after first logout - login cycle"
date: 2011-10-18
forum: Desktop Environments
---

### Post by Alaak on 2011-10-18
Hi,

I updated my old Ubuntu 11.04 to 11.10 and installed Gnome 3 but after I logged out the first time and back in again the Gnome Shell is missing. I can get it back by removing all .* folders and files in my home folder but after I log out and back in again the shell disappears again.

I assume that the system resets to some default settings left over by Ubuntu 11.04, but I don't know where to find them and change this behaviour. Any ideas?

---

### Post by paulisdead on 2011-10-18
You didn't install the alternate status menu extension, did you?  There's a bugged version going around that causes that on login.  There's a fixed version in the webupd8 ppa

If you move your ~/.config/dconf folder to somewhere else, it should get regenerated on next login, so gnome-shell starts.  At least then, you're not redoing everything, just the gnome settings.

---

### Post by Alaak on 2011-10-18
Actually ... I did. But it works fine on my other laptop. Weird. I'll try your solution and will tell if it has worked later.

---

### Post by paulisdead on 2011-10-18
The bug only happens if you don't have a picture set, supposedly.  It's also possible you got a different version on one system.

---

### Post by Alaak on 2011-10-18
Yep. That works. Thanks for your help.

---


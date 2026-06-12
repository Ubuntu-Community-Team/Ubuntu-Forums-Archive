---
title: "Login Screen Stuck as Desktop Background After Sign On"
date: 2013-02-24
forum: Desktop Environments
---

### Post by pmwalk on 2013-02-24
So I have a very strange problem. Running 12.10, after I log in, everything that was present on the login screen is now my desktop background. What's more, it covers my desktop, meaning no selection box, right click menu, or desktop icons. However, everything else works fine. I can still open windows and do everything I normally would within them.

I've attached a screenshot to make this more clear.

This started happening after I changed some settings in ubuntu-tweak. I switched everything back to default (and even uninstalled ubuntu-tweak), but nothing seems to fix it. Everytime I reboot and log in, everything on the log in screen freezes and covers the desktop.

Any help would be appreciated. Thanks!

---

### Post by pmwalk on 2013-02-25
I found a solution, although I still have no idea what the problem was.

I followed the directions I found here:

[http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values](http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values)

Specifically the second answer, which involves moving  
~/.config/compiz-1
~/.config/dconf

and restarting Xorg. This resets all of the Gnome/Unity settings, and fixes the stuck login background. After this, you'll just have to redo all your settings, and then the problem is fixed.

Still, if anyone has any idea what may have caused this in the first place, I'd love to know. In any event, I've removed ubuntu-tweak for now.

---

### Post by swimmingly on 2013-05-24
[INDENT] 		The problem is the setting "Icons on Desktop", under the page "Desktop Icons". When this is turned off you get the login screen stuck as your background.

Not to sure what causes it though. 	
[/INDENT]

---

### Post by pmwalk on 2013-05-24
> **swimmingly said:**
> [INDENT]         The problem is the setting "Icons on Desktop", under the page "Desktop Icons". When this is turned off you get the login screen stuck as your background.

Not to sure what causes it though.     
[/INDENT]


Thanks for finding that out! That likely was what I had set wrong. Still curious why that happens...

---

### Post by Andre_Fernando on 2013-09-10
Thank You!!

---

### Post by ilhamfarobi on 2014-06-16
> **swimmingly said:**
> [INDENT]         The problem is the setting "Icons on Desktop", under the page "Desktop Icons". When this is turned off you get the login screen stuck as your background.

Not to sure what causes it though.     
[/INDENT]

can someone tell me what does it means?

---


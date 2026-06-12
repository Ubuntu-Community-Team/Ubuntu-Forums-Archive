---
title: "Disable visual effects for other user"
date: 2009-02-12
forum: General Help
---

### Post by Aardobard on 2009-02-12
I just swapped most of my wife's computer hardware out.  The problem is, the onboard video will not handle the visual effects setting and causes very slow response times, half-screen artifacts and makes the menus inaccessible.  It does not respond when I right-click on the desktop to try to disable the visual effects that way.

I can log on as a different (admin) user where visual effects are disabled and everything runs smoothly.

I think I need to change her visual effects setting from the command line under a different user.  I am using Ubuntu 8.1 with current updates.
A. Can this be done?  
B. How do I do it? 
C. Other options?

Thanks for your help in advance.

---

### Post by UbuntuNerd on 2009-02-12
try going to System > Preferences > Appearance > Visual Effects and click none

---

### Post by UbuntuNerd on 2009-02-12
you can also type this in a terminal 
```
metacity --replace
```
it will replace compiz with the regular window manager.

---

### Post by Aardobard on 2009-02-12
This is what finally worked for me in the terminal:

logged in as user2
su "user1" 
sudo metacity --replace

After that I switched users through the menu and was able to change the visual preferences via right=click on the desktop.

Thanks for the help!

---


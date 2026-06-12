---
title: "Can't change system theme, stuck with gnome default?"
date: 2010-07-21
forum: Desktop Environments
---

### Post by Akeru on 2010-07-21
Hey, I'm having a bit of a problem. Recently I noticed my system theme changed itself to a grey blocky look that I can only assume is the gnome default. I cannot change it back to anything else, like Ambiance or Dust through the appearance window.

I run Compiz and Emerald for effects and themes. Compiz effects and Emerald's window borders work fine, I have my Emerald theme but the icons, menus and buttons are all this ugly old look and I cannot change it. I have tried reloading the window manager, rebooting, switching Compiz and Emerald off and using Metacity and GTK Window Decorator, but the theme doesn't change. I can't change buttons, menus, colors or icons.

When I open System > Prefs > Appearance, I can choose a theme and oddly enough it changes the theme for the appearance window, but only the appearance window and nothing else. 

How can I fix this and get my old theme back?

I've attached a screenshot that should illustrate my problem.

---

### Post by negativ on 2010-07-21
If you have gconf editor installed, navigate to /desktop/gnome/interface and look at the gtk_theme key.  Try changing it to "Default" or "Clearlooks" or something, and see if you can change it that way.  Not that this is a solution, but might accidentally lead to other clues.

Also, you might experiment by adding another user, then logging in as the test user and see if you can change the themes for that user.  Hopefully it's something to do with your account, rather than a system-wide problem.

---

### Post by Akeru on 2010-07-22
> **negativ said:**
> If you have gconf editor installed, navigate to /desktop/gnome/interface and look at the gtk_theme key.  Try changing it to "Default" or "Clearlooks" or something, and see if you can change it that way.  Not that this is a solution, but might accidentally lead to other clues.

Also, you might experiment by adding another user, then logging in as the test user and see if you can change the themes for that user.  Hopefully it's something to do with your account, rather than a system-wide problem.
Thanks for the reply. I tried a new user, and the problem remains the same. It's apparently stuck system-wide. Following that, I fired up gconf editor and when I looked at the gtk_theme key, it was set to the theme I selected in the appearance dialog before. I changed it to Clearlooks to see if that did anthing, but that didn't change anything either. My icon key was also set to Humanity, but that's obviously not what I'm getting.

I appreciate your help though. Any other ideas?

Edit: Is there a way I could re-install GTK or whatever it is that actually controls the system theme? Maybe that'd fix it.

---

### Post by Joshua on 2010-11-03
I'm having the same problem.  I've attached two screen-shots where I've selected the Ambiance Theme in one and the Clearlooks Theme in the other.  The window borders change, but the icons do not.  Does anyone have any idea what's going on.

This all seems to have happened after a crash of some sort.  I came back to my computer and it was repeatedly trying to load Gnome, but I'd hear login drumbeat and then it would crash and try again.  tty1 said something about a gpu crash, but I assume the theme issue is related to a corrupted file that resulted from the crash.

---

### Post by Lektorvis on 2011-09-12
I had a similar problem recently. I found this script: 
[http://gnome-look.org/content/show.php/Mono+Icons+for+any+Icon+theme?content=134567]("http://gnome-look.org/content/show.php/Mono+Icons+for+any+Icon+theme?content=134567") 
I followed the "Read Me" instruction and after system restart I had my Mono Icons back.

---

### Post by Frogs Hair on 2011-09-12
Take a look at the link . [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---


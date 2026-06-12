---
title: "e17 not showing apps in menu for one user but does in other"
date: 2007-09-20
forum: Desktop Environments
---

### Post by TremerePuck on 2007-09-20
I've had e17 installed before so I  guess it has some settings file somewhere that I can't find.  I've tried deleting the .e folder in hopes of it generating the menus automatically. 

I've tried copying the .e folder from the other user. I've tried purging all of the e17 packages (yet it doesn't delete my settings at all, upon reinstall everything was like it was before, themes and all).

 I can't find anywhere that says where the file for the applications menu is so I can edit it manually. I've found documentation to show how to edit it, which is annoying and useless to me if I don't know what file to edit. 

Everywhere I look says to click on the button to regenerate the application menu, but it's not where they say it is.

Could someone tell me where the file is that defines the application menu for a user? Or something similar.

Any help is appreciated.

---

### Post by kellemes on 2007-09-20
e17 is in development so a lot of stuff is not working at all..

---

### Post by TremerePuck on 2007-09-20
> **kellemes said:**
> e17 is in development so a lot of stuff is not working at all..

I know that. That's like saying the same about Gutsy if I had a problem with it. Not helpful at all.

As I said before the menus are full on a different user. One that I created after this attempt at using e17. Just not on the one I use, which I had a long time ago when trying e 17

---

### Post by the yawner on 2007-09-20
1. How did you installed E17? On top of another DE or a lean install (using alternative installer/s?

2. What apps are in the menus on the other user? Are the menu items user created or automatically generated upon installation?

---

### Post by TremerePuck on 2007-09-21
1: Using the repositories and aptitude. Running it alone and not over another desktop environment. I just select it from the menu in kdm.

2: All the applications that are in the kde menus are in the other user's application menus. They were just there when I made the new user name so they're auto generated.

If it helps: I had to delete my home/.e/ folder in order for it to reset what modules were loaded as it only had the ones that existed months ago loaded. The other user had all the defaults loaded.

I just wish I knew how to call upon it to generate them or at least where the file that defines the menu is located so I can copy and paste the file from the other user over it.

---

### Post by JackTrust on 2008-06-20
I know this is slightly out-dated though, I found a solution to the problem as I encountered it as well.

I read this guide;

[http://wiki.enlightenment.org/index.php/E17_and_Efreet](http://wiki.enlightenment.org/index.php/E17_and_Efreet)

and it solved my problem.

I'm a Gentoo user, but it has instructions for other distros as well.

After I emerged gnome-menus, it automatically created the applications file and the enlightenment menu instantly refreshed with all of my apps.

Hope this helps someone in the future.

Thanks for reading and enjoy. ):P

---


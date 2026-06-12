---
title: "Can't change desktop background (wallpaper)"
date: 2007-10-12
forum: Desktop Environments
---

### Post by Ghazgkull on 2007-10-12
On Ubuntu 7.04 (Feisty), the "Change Desktop Background" dialog is having absolutely no effect for me. No matter what image I choose, the default background continues to be shown.

What am I missing?

---

### Post by eurgain on 2007-10-12
Since you have been around for a while (member for a year), I assume that you did not previously have this problem, but it has now appeared.

So, what have you done recently that might have caused problems?

A

---

### Post by Ghazgkull on 2007-10-12
I got a new machine and installed Feisty. :)

Previously, I was running Dapper on another box.

---

### Post by eurgain on 2007-10-12
There is nothing that I know of that is fundamentally broken, so there is something up with what you have done.

If you have made a new install, and then copied allyour users' home directories into place, things like this will probably not work, because there are lots of detailled changes in the Gnome/KDE dotfiles that *will*be broken.

Maybe, delete your user directories in the new system, and re-create them as empty directories.  Copy into each of them the files from /etc/skel (remember, the hidden files under /etc/skel are vital)!  Then copy all if the users' visible files into their new directories. Each user should then have all of their personal data (which is inherently valuable) but not their settings (which can be re-created, with your help).

Of course, you may be able to figure out a save set of dotfiles that a user can carry over that does not trouble the new system, but which makes the user's life easier.

HTH
A

---

### Post by Ghazgkull on 2007-10-12
Thanks for your replies, eurgain, but I didn't copy over my user directory from the previous install.

I just had to reboot my machine (I need to bump up my open file limits in limits.conf) and after rebooting, it seems that my wallpaper choice in now in effect.

If I go back into the desktop background dialog and choose a new background, it has no effect again, though...

Do I actually have to reboot (or probably just log out) every time I want to change my background in Feisty?

---


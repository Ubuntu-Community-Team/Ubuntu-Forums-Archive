---
title: "GNOME with docky on 18.04"
date: 2019-03-14
forum: Desktop Environments
---

### Post by toad007toad007 on 2019-03-14
Hello all,
I am running 18.04 and recently installed docky. I have it all setup to my liking for the most part with one annoying exception. Whenever I open a nautilus instance, it displays the trash icon in the dock instead of the correct one. In /usr/share/applications I have multiple entries for Files. I don't know if that helps or not. Any ideas on how to remedy this issue? Also, when I hit the super key, my previous gnome dock appears on the left side of the screen, is there a way in dconf editor to remove this characteristic? It's just annoying to see... Thanks in advance!

---

### Post by deadflowr on 2019-03-14
To turn off the dock (as much as you can) in dconf editor go to
org > gnome > shell > enabled-extensions and then you need to delete the entry for 'ubuntu-dock@ubuntu.com'

Unfortunately this only removes it from ever appearing on the desktop.
It'll still show whenever you open the activities overview.

---


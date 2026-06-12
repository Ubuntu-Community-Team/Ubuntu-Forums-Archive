---
title: "Missing items from Main Menu"
date: 2007-04-14
forum: Desktop Environments
---

### Post by jimpop on 2007-04-14
Today I noticed that 95% of the Applications, that should be listed in Gnome Main Menu, are now missing.  The applications themselves are still installed, but the menu entries are gone.   Thinking this might be a user account issue, I created a new user and the items are missing from it's main menu.  For instance, under Applications -> Internet, I only now show BitTorrent.    What could have happened and what can be done to restore this missing items?

---

### Post by amohanty on 2007-04-14
Can you check to make sure that the appropriate *.desktop files are still in /usr/share/applications?

AM

---

### Post by jimpop on 2007-04-14
Yes, they are.  There are 151 files in /usr/share/applications and they are all group+world readable.

---

### Post by amohanty on 2007-04-14
hmm. can you add another main application menu item to your panel and see if that has it all?

AM

---

### Post by jimpop on 2007-04-14
I've already tried removing and re-adding Menu Bar and both of the Main Menus.  All three show the same lack of applications.  The only applications listed are File Browser, OpenOffice.org Drawing, BitTorrent, and Configuration Editor.

---

### Post by amohanty on 2007-04-15
First check to see if you have sufficient disk space.
Second in System->Preferences->Session see if you have any saved sessions and remove them, uncheck automatically save session if its checked, logout and log back in again.

also post the output of:

ls -al 

find -user root

in your home folder.

AM

---

### Post by jimpop on 2007-04-15
Plenty of disk space, no saved sessions, auto-save-session has been off since day one.  I've Been logging in and out all day, rebooting too, even tried creating new users... still no luck.   Thanks for trying to help however.

---

### Post by jimpop on 2007-04-15
What are you looking for in the ls -al output?  also, find -user root produces nothing.

---

### Post by jimpop on 2007-04-15
Resolved.

/etc/xdg/menus/applications.menu was zero sized.  I restored from backup and all is good now.  I'm not 100% sure, but I believe a recent install and uninstall of MG-SOFT's MibBrowser is responsible for this.   Thanks amohanty for your help in trying to sort this out.

---

### Post by amohanty on 2007-04-16
> What are you looking for in the ls -al output? also, find -user root produces nothing.
Reply With Quote

Sometimes due to some bad operations, certain xsession related file permissions/ownership change, thus makig certain specific things unusable. That was a good find though, will keep it in mind the next time someone runs into something like this.

Out here you learn something new everyday :)

AM

---

### Post by jimpop on 2007-05-15
"I'm not 100% sure, but I believe a recent install and uninstall of MG-SOFT's MibBrowser is responsible for this. Thanks amohanty for your help in trying to sort this out."

Regarding the above comment made by me.... I have tested and retested this and have been unable to reproduce this.  So, I think it is safe to say that MG-SOFT's new Linux version of MibBrowser did NOT cause this problem.

---


---
title: "Cannot change default desktop background"
date: 2005-12-17
forum: General Help
---

### Post by akniss on 2005-12-17
hi all... i used to have a nice desktop background that would show up everytime I logged in.  I started playing around with some other desktop environments and window managers, and at some point I lost my background.  I can still go to System>Preferences>Desktop background to change it, but the next time I reboot it defaults back to the ubuntu brown.  Also missing from the desktop is an icon for my file storage partition that used to be there.

If I change the session to GNOME failsafe at the login screen, my nice blue background is there, as well as my FileStore icon.  Any ideas on what I need to do to get my desktop background to stay with me like it did before?

---

### Post by NotJustANewbie on 2005-12-17
When logging out, click "save current setup"

---

### Post by akniss on 2005-12-17
[QUOTE=NotJustANewbie]When logging out, click "save current setup"[/QUOTE]

That doesn't work.  I log in again, and have the brown background with no Filestore icon.  It happens whether I reboot or log out, regardless of whether I check 'save current setup' or not.

---

### Post by akniss on 2005-12-17
Bump...

Anyone have any ideas on what to look for?

---

### Post by duminas on 2005-12-18
If this is not the same program, [see here](http://www.ubuntuforums.org/showpost.php?p=584312&postcount=2) (I use Openbox, so I do not have the Gnome menus to test). Also, I'm not sure if this would help anything, but check if you have a .xinitrc or .Xsession file in your home directory? Something in there might be messing it up.

---


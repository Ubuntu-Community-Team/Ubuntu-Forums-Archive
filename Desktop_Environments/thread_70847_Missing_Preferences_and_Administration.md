---
title: "Missing Preferences and Administration"
date: 2005-10-01
forum: Desktop Environments
---

### Post by petrol on 2005-10-01
All,
I have a new install of 5.04. I have used the Preferences and Administration menus under System. I think it might have been after the install of the Citrix ICA client that the Preferences and Administration menus are missing. It shows two empty folders in their place when you click on system. I tried rebooting etc. 
Petrol

---

### Post by aysiu on 2005-10-01
Have you tried right-clicking the panel and selecting "Add to Panel"?

---

### Post by petrol on 2005-10-01
[QUOTE=aysiu]Have you tried right-clicking the panel and selecting "Add to Panel"?[/QUOTE]
The items in there do not include the needed menu items under System. I was trying to check the gnome pannel files but I am not sure where the locations of these selections are specified.

---

### Post by petrol on 2005-10-01
[QUOTE=petrol]The items in there do not include the needed menu items under System. I was trying to check the gnome pannel files but I am not sure where the locations of these selections are specified.[/QUOTE]

I actualy found the "Main Menu" addition. When I add it "Preferences" and "Administration" are still missing.

---

### Post by Ruddigger on 2005-10-01
Hey tou can allways do update-menus, I don't know if you need to do this as root, but doesn't hurt to try

---

### Post by petrol on 2005-10-01
[QUOTE=Ruddigger]Hey tou can allways do update-menus, I don't know if you need to do this as root, but doesn't hurt to try[/QUOTE]

sudo: update-menus: command not found

---

### Post by petrol on 2005-10-01
I was looking around and it seems that the file defining these menues is:
/etc/xdg/menues/preferences.menu
I am not sure if this is the right place to look.

---

### Post by petrol on 2005-10-01
i ended up deleting the user and starting over with the profile.

---


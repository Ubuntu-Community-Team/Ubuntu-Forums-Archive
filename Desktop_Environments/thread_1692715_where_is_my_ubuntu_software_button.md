---
title: "where is my ubuntu software button?"
date: 2011-02-21
forum: Desktop Environments
---

### Post by wilander on 2011-02-21
I managed to delete my ubuntu software center button, and now I can't figure out how to get it back! Anybody who can help me? :)

---

### Post by Tamlynmac on 2011-02-21
Right click on your (apps or main menu) menu ion the panel and select "Edit Menus". When the edit menus window opens left click on "Applications" on the left side list, then on the right side of the window left click on the "New Item" button. This will open a create launcher window.

Type: Application
Name: Ubuntu Software Center
Command: /usr/bin/software-center
Comment: Unnecessary

If no icon is displayed on the top left of the launcher window. Left click on where the icon should be and select the Ubuntu Software Center icon or one of your choice. Upon completion select "OK" at the bottom of the create launcher window and close the edit menu window. This should add the software center to your menu.

The actual command is located here:
file system/user/bin/software-center

Good Luck & hope this helps.

---

### Post by Krytarik on 2011-02-23
In those very dialog you may still find the "Ubuntu Software Center" item, you may have disabled it inadvertedly. I suppose you didn't delete the respective .desktop-file in "/usr/share/applications".

---


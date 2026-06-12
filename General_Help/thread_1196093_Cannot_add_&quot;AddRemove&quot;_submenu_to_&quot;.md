---
title: "Cannot add &quot;Add/Remove&quot; submenu to &quot;Applications&quot; menu"
date: 2009-06-24
forum: General Help
---

### Post by kkruecke on 2009-06-24
I am trying to add "Add/Remove" submenu item to the "Applications" menu. 

So I went to System->Preferences->Main Menu. But when I clicked on "Add/Remove" or "System Tools" (in the right pane), the check mark appears only momentarily, but then disappears about two seconds later.

What is up?

---

### Post by Tamlynmac on 2009-06-24
This is probably caused by the fact that nothing in that menu is selected to appear "Show".

When editing the menu you need to assure that something is selected in the section you wish to see in the menu. For example:

Once you've opened edit menu (Main Menu) go down the left side and select the section the Item is located in, then on the right side make sure the Item has a check mark in front of it. The column "Show" on the right side has a box that needs to be checked if you want the Item to appear in the menu. Chances are none of the Items in the menu are checked.

I hope I understood your question correctly and that this helps.

---

### Post by kkruecke on 2009-06-24
Thanks for your reply. What you said also explains why "Add/Remove" and "System Tools" are in italics in the right-hand Items pane. Italics obviously must mean that no submenu items have yet been made show-able.

But here's the thing. "Add/Remove" is not listed in the left pane, the Menus pane of Main Menu, although "System Tools" is. I thought that in Intrepid--I am now running Jaunty--"Add/Remove" displayed by default under Applications.

---

### Post by Tamlynmac on 2009-06-25
After installing any new release of Ubuntu, the first thing I do is change to the single "Main Menu" (Add To Panel) and delete the default panel menus.

If I recall correctly the Add/Remove was turned on by default in that menu.

Sorry, I can't be of more help. It sounds like if the Add / Remove is in italics and can't be turned on, that you may have an additional problem.

One thought:
If you right click on the "Add / Remove" in the edit menu "Applications" and select properties. The Command should read.
/usr/bin/gnome-app-install

If it does you may wish to check your system files "user/bin/gnome-app-install" to assure the file is actually there.

Good Luck and let me know what you find.

---

### Post by kkruecke on 2009-06-25
I do have /usr/bin/gnome-app-install.

And the fact that "Add/Remove" is in italics, whenn listed under the list of Items that are available for "Applications" (in the right-hand pane of Main Menu, when "Applications" is selected in the left pane), should not matter. Italics only means that there are no submenu items. Italics doesn't, however, means that that item can't be enabled. Take, for example, the "Volume Control" under System->Preferences. It is in italics (meaning it has no submenu items). But if I click it, the italics go away, and, unlike "Add/Remove", is stays enabled, the check mark doesn't suddenly disappear.

---

### Post by Tamlynmac on 2009-06-25
No, I agree that simply because it's in italics doesn't mean it can't be turned on. Some selections in the menu may not have sub-menus and simply by checking the box should then enable that app.

As I said, I have no idea why (if you have both the command and the file) it doesn't stay activated in the menu. Even in the gnome configuration editor I don't see anything that would turn it off.

Can you run it from the file browser by double clicking on the file and selecting "run"?
"system files/user/bin/gnome-app-install"

If so, then it must be a problem with the link in the menu. If that's the case you may wish to create a new item "Add/Remove" under the Applications menu and try it. Perhaps a problem in the initial menu item creation.

Good Luck.

---

### Post by kkruecke on 2009-06-26
I did what you suggested: deleted "Add/Remove.." and then manually insert it again. That worked. Thanks!

---

### Post by Tamlynmac on 2009-06-26
Glad it worked, take care and enjoy.

---


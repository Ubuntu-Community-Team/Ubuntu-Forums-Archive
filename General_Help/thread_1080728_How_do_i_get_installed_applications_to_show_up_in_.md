---
title: "How do i get installed applications to show up in my main menu?"
date: 2009-02-25
forum: General Help
---

### Post by Macfunky on 2009-02-25
I have a few applications that i installed on my system but i have to open them with alt + F2. Is there a way that i can add these to my main menu as they don't show up there? Thanks

---

### Post by mb_webguy on 2009-02-25
Right-click on the menu and select Edit Menus.  Navigate to the menu you where you want to add the launcher.  Click the New Item button.  Add the appropriate information for the Name and Command, and change the icon if you want, then click Ok.

---

### Post by ibuclaw on 2009-02-25
Right-Click the "Applications" bar and select "**Edit Menus**".

Then go into a sub section that would suit the category of the application you want to add and click "New Item"

Name: (is the Name you want to give it in the menu)
Command: (is the command you use when you press Alt+F2 to run it)
Comment: (is a small description of the program ... not needed really, unless you forget :D )

And then click the **Icon** and good luck finding the icon of the application :evil:

but, just to help make the search easier, look in the
```
/usr/share/**appname**
/usr/lib/**appname**

/usr/share/pixmaps

```
directories, as that's where they are usually hiding.

Regards
Iain

---


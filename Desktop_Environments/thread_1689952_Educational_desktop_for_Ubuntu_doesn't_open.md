---
title: "Educational desktop for Ubuntu doesn't open"
date: 2011-02-17
forum: Desktop Environments
---

### Post by spacefrog on 2011-02-17
I have just downloaded the educational desktop for Ubuntu but have no idea how to get it running. When I click on the menu item nothing seems to happen. Thanks

---

### Post by 3Miro on 2011-02-17
I don't have much experience with Edubuntu, but here is something that you can try. 

1. Right-click on the Application menu and select: edit menu.
2. Don't actually edit anything, just find the Edubuntu entry and select Properties.
3. Look for the "command" section, it will look something like:
```
firefox %u
```
you need the first part.
4. Open a terminal. Apps -> Accessories -> Terminal and copy paste the command before the percent sign.
5. Hit enter and you should see an error message, post the message here.

With out an error message of some sort, we would be just shooting in the dark here.

---

### Post by spacefrog on 2011-02-19
The only thing that I find on the menus is Edubuntu menu editor under System tools, and following your directions there is no % sign, just menueditor, which doesn't give an error message in the terminal.

---


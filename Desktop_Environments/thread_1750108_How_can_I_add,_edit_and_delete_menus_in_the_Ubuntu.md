---
title: "How can I add, edit and delete menus in the Ubuntu 11.04 main menu?"
date: 2011-05-05
forum: Desktop Environments
---

### Post by Uewd on 2011-05-05
When I was using Ubuntu 10.10 I was able to **add menus, edit and delete them from the main menu by right clicking on the menu and selecting Edit menus** ( [http://www.watchingthenet.com/wp-content/uploads/image/ubuntugnomemenu1.png](http://www.watchingthenet.com/wp-content/uploads/image/ubuntugnomemenu1.png) ). After installing Ubuntu 11.04, I found that I can't add, edit or delete any menu. Any one knows how to add, edit and delete menus from the main menu?

Please help.
Thanks.
Uewd

---

### Post by haydnc on 2011-05-08
It appears that you can edit menus using the gnome-control-center (which you have to install). It definitely has an entry in there under Personal which looks like it'll let you edit the Main Menu.

I'm not 100% sure that it works because Unity seems to control its menus in some other way. I managed to edit a couple of items in the menu by accessing their .desktop entry which is located either under ~/.local/share/applications or under /usr/share/applications.

I'm not entirely certain yet just how those .desktop entries work, but editing them using something like vim definitely lets you alter how they run, such as adding parameters to the command line. 

I'm not sure if that makes much sense, but if you open up one of those files for editing you should be able to make some sense of the contents and that might help you create your own for editing your menus.

Sorry if that's a little vague. I'm still trying to work out the details myself.
:(

---

### Post by malleus74 on 2011-05-15
I just posted this:

[http://ubuntuforums.org/showthread.php?p=10820654#post10820654](http://ubuntuforums.org/showthread.php?p=10820654#post10820654)

---


---
title: "xine installed a menu item I can't change"
date: 2005-11-26
forum: Desktop Environments
---

### Post by ryan76 on 2005-11-26
When I installed xine it put a folder called 'Multimedia' in my Applications menu with one item called xine in it. Smeg can't see it so I can't remove it.

Has anyone else had this problem? Is there any way I can remove it or make Smeg see it?

Thanks

---

### Post by akiro.yamamoto on 2005-11-26
Hi ryan76,
I assume that your using Gnome....not KDE
Have you tried using
Applications >> System Tools >> Applications Menu Editor
And then changing the menu entries there. You should be able to drag xine form that folder to the Sound and Video folder.
Then you can delete or hide that Multimedia Folder.

I hope that helps...

:smile:


EDIT
If that didn't work you can edit the desktop file manually.
Try this:
CODE:
sudo gedit /usr/share/applications/xine.desktop
And ensure at the bottom of the file under categories it looks like this:

Type=Application
Categories=Application;AudioVideo;

Anyway...
I hope that helps...
:smile:

---

### Post by ryan76 on 2005-11-27
Hi,  thanks for your reply.

Yes it's Gnome, sorry, but...

I don't have Applications Menu Editor at all that I can find.

Also there isn't a file called xine.desktop in the /usr/share/applications folder.

---


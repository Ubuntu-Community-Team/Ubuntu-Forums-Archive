---
title: "Gnome panel configuration is a mystery to me!"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by Midahed on 2007-07-23
I'm using the default installation of Feisty 7.04 desktop.  Can anyone point me towards something that tells me how to put additional buttons on panels and entries in menus?

I can find my way round the basics, but there are apparent inconsistencies that I don't understand.

For instance, ideally I want to add the Terminal Server Client applet to a menu.  If I click the 'Applications' menu at the top-left of the screen and then 'add/remove' I get the 'Add/Remove Applications' window.  However, I cannot find the terminal server client anywhere in the list of installed applications or even in the list of Ubuntu supported applications.  I've searched the list using the words terminal, server, client, RDP and tsclient.  There are other remote desktop clients listed, but not the one that is already available on the system!

If I take a different tack and elect to put an icon for Terminal Server Client directly on the top panel, rather than in a menu, I right-click on the top panel and select 'add to panel'.  This opens the 'Add to Panel' window which does  show the Terminal Server Client Applet icon in the System and Hardware section.

So why is it there and not in the Add/Remove Applications menu?

Anyway, I can drag a copy of the icon onto the panel and it works fine - I can now establish a remote desktop session to my Windows machine.

Sometime later I managed to delete all the entries from my top panel.  The panel itself was still there, but all the menus and icons had gone.  I got it back by renaming ~/.gconf/apps/panel to ~/.gconf/apps/panel.old but my Terminal Server Client icon was missing.

I put the icon back onto the panel OK, but now it seems to have a sort of sub-menu.  Whereas before I had to re-create it, I just clicked the icon and was taken straight to the Terminal Server Client window, but now when I click the icon is shows a small menu with 'new connection' as the only entry.  Clicking that takes me to the Terminal Server Client window.

OK, it works, but it's irritating when it doesn't really work as it should.

In summary, I have three question.....

First, why doesn't the application appear in the list for adding to a menu.  Is it because it is an 'applet' rather than an application?

Second, I could get round that by creating a launcher and adding that to a menu, but I cannot find the terminal server client icon.  There's obviously one on the system somewhere, because it appears in the 'add to panel' window, but where is it?

Third,  I could put up with the icon just being on the panel, rather than in a menu, but how do I change the system behaviour so that it no longer displays the 'new connection' entry.  Losing the panel icons and re-creating the one for the terminal server client seems to have made the system create this extra sub-menu off the icon, but I can't see how to put it back as it was.

Thanks,

Mike

---

### Post by alex_anthony on 2007-07-23
Add/Remove Applications is not the menu editor. It is a program installer (frontend to apt-get/aptitude)
System>Preferneces>Main Menu will allow you to move things between menus

When you added Terminal Server client the second time, you took the applet out of the add to panel... menu, so it is an applet in your panel, so you get that menu. first time you dragged it from your menus, so it was a launcher to the program. Basically, applet>menu, launcher>launches program

---

### Post by JAPrufrock on 2007-07-23
Two ways to add applets/files and arrange stuff on the desktop are the following:  The most useful is right clicking on an empty space on a panel for adding applets.  The other is for adding and hiding stuff for menus:   system > preferences > main menu.  Hope this helps.

---

### Post by Midahed on 2007-07-23
Ah thanks, that makes sense.

I've got rid of the applet and created a launcher instead - I even managed to find the icon as well.  I've dragged the launcher onto the panel and it's all back as it was.

Thanks,

Mike

---


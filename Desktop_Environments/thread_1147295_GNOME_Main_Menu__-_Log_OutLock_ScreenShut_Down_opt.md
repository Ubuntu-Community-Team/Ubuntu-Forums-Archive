---
title: "GNOME Main Menu  - Log Out/Lock Screen/Shut Down options"
date: 2009-05-03
forum: Desktop Environments
---

### Post by peterswinkels on 2009-05-03
I've two computers running Ubuntu 9.04 with GNOME. On one computer the GNOME Main Menu looks like this:
[IMG]http://www.euronet.nl/users/swinkels/laptop1.gif[/IMG]

On the other one it looks like this:
[IMG]http://www.euronet.nl/users/swinkels/pc.gif[/IMG]

I've no idea how I got the Log Out/Lock Screen/Shut Down options in the menu displayed in the first screenshot, and I have no idea how to remove them. Can any one tell me how to add/remove these options from the GNOME Main Menu?

I have looked at the Menu Editor, Configuration Editor, User Switcher applet, Shut Down applet, and several other places. I can't figure it out.

---

### Post by id10twork on 2009-05-03
right click on ur little ubuntu menu, choose "edit menus", move things to where you'd like them to be... when i tried, i could do it. i'm not sure if that's what you meant by Menu Editor. hope it works.

---

### Post by jacksonpollack on 2009-05-04
You can't just right click and edit the menus for those options.

Hit Alt+F2, type: gconf-editor
Then navigate to: apps/panel/global
On the right there'll be options to disable the "lock screen" option, and the "log out option" (which also controls shut down, they are linked together it seems).

---

### Post by peterswinkels on 2009-05-04
> **jacksonpollack said:**
> You can't just right click and edit the menus for those options.

Hit Alt+F2, type: gconf-editor
Then navigate to: apps/panel/global
On the right there'll be options to disable the "lock screen" option, and the "log out option" (which also controls shut down, they are linked together it seems).

Okay, but that doesn't answer my question about how to remove/add these options to the GNOME Main Menu applet...

---

### Post by peterswinkels on 2009-05-09
I did some more experimenting to try to solve this issue but haven't solved it yet. I have found out though that the Log Out/Lock Screen/Shut Down options not only appear in the Main Menu applet but also in the "Menu Bar" applet. The "System" menu to be specific: [IMG]http://www.euronet.nl/users/swinkels/laptop2.gif[/IMG]

I've examined the files in the "/etc/xdg" and "~/.config/menus" directories and found nothing that could explain the presence/lack of the menu options in question.

It seems that Alacarte (the menu editor) doesn't allow you to edit everything in the menus. I couldn't find an option that would unhide/hide anything in Alacarte using the GNOME Configuration Editor though.

So, how do I add/remove the options displayed at the bottom level of the "System" menu?

---

### Post by peterswinkels on 2009-05-13
I figured it out, it turns out that adding the User Switcher applet to any panel makes the shut down, log out, and lock screen options disappear from the Menu Bar/Gnome Main Menu applets... This doesn't appear to be well documented or obvious.

I've removed the User Switcher applet and now have the options in question appearing in the menu. Only question now is: how do I start a guest session or use the hibernate option?

---

### Post by simptechmike on 2009-06-01
> **peterswinkels said:**
> I figured it out, it turns out that adding the User Switcher applet to any panel makes the shut down, log out, and lock screen options disappear from the Menu Bar/Gnome Main Menu applets... This doesn't appear to be well documented or obvious.

I've removed the User Switcher applet and now have the options in question appearing in the menu. Only question now is: how do I start a guest session or use the hibernate option?

Hibernate is listed when you select Shut Down, either from the Main Menu or using the Menu Bar (System > Shutdown).

For a Guest Session, you could create a launcher on the desktop (right click desktop and choose **Create Launcher...**)

**Name:** Guest Session
**Command:** /usr/share/gdm/guest-session/guest-session-launch
**Comment:** Launches a Guest Session

Click **OK**.

A launcher could also be added to the menu.

**_Main Menu (everything under one item)_**

Right click menu and choose **Edit Menus**. Click **New Item**. Make sure Application is selected for type and use the items above. Click **OK** when finished. Drag the item to the bottom of the list and it will appear below Add/Remove.. in the Menu (or last on Applications menu)

**_Menu Bar (Applications, Places, System)_**

Right click menu and choose **Edit Menus**. Select system in the left and then click **New Item**. Follow the rest of the step above. This would result in the guest session launcher being available under the System menu along with the other options (shutdown/logout).

---

### Post by peterswinkels on 2009-06-02
Okay, thanks for the information. The command for launching a guest session is especially useful.

---

### Post by toallpointswest on 2009-06-10
Is there a way to add these option under the mouse's right click menu?

---

### Post by simptechmike on 2009-07-08
> **toallpointswest said:**
> Is there a way to add these option under the mouse's right click menu?

The tutorial here is a little dated, but you should be able to figure things out:

[http://www.foogazi.com/2007/11/05/adding-shortcuts-to-the-right-click-menu-in-ubuntu/](http://www.foogazi.com/2007/11/05/adding-shortcuts-to-the-right-click-menu-in-ubuntu/)

I have figured out the following commands to use:

Logout (without prompt)
/usr/bin/gnome-session-save --logout

Logout (with prompt to logout or switch users)
/usr/bin/gnome-session-save --logout-dialog

Shutdown/Restart (Displays an option for shutdown/restart)
/usr/bin/gnome-session-save --shutdown-dialog

Guest Session
/usr/share/gdm/guest-session/guest-session-launch

---

### Post by fjrichman on 2009-11-02
This post is old and dead but I found another way to do this is just add the 
indicator-applet-session to a panel and it removes it from the list AND it has all the options already included. 

The reason I'm pointing this out is because I came across this post when trying to figure out how to remove those from my main menu :)

---

### Post by androloog on 2011-05-12
> **simptechmike said:**
> The tutorial here is a little dated, but you should be able to figure things out:

[http://www.foogazi.com/2007/11/05/adding-shortcuts-to-the-right-click-menu-in-ubuntu/](http://www.foogazi.com/2007/11/05/adding-shortcuts-to-the-right-click-menu-in-ubuntu/)

I have figured out the following commands to use:

Logout (without prompt)
/usr/bin/gnome-session-save --logout

Logout (with prompt to logout or switch users)
/usr/bin/gnome-session-save --logout-dialog

Shutdown/Restart (Displays an option for shutdown/restart)
/usr/bin/gnome-session-save --shutdown-dialog

Guest Session
/usr/share/gdm/guest-session/guest-session-launch
 


I have been searching for this answer for ages! Thank you!
gnome-session-save --log out fixes all my computer class log out and user switching problems!

Cheers!

---


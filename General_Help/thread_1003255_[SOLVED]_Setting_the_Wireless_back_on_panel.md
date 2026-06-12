---
title: "[SOLVED] Setting the Wireless back on panel"
date: 2008-12-05
forum: General Help
---

### Post by inirini on 2008-12-05
Awhile ago, I accidentally deleted the top panel (misclicked) and have got by fine without needing the wireless icon to connect wirelessly at home. But now, I can't fix the problem of what is causing for the machine with ubuntu and is now offline. I tried looking for the wireless icon... thing's name to add it back to the panel.

I have come here as a last resort in finding the program that manages wireless connections. I've already tried to use the add/remove applications to install some other wireless management, but of course, I need to connect to the server that will install it in the first place.

So, what is the name of this program? In addition to that, how do I search for it? As a complete new user, I have no idea how to find things I need.  Thank you so much in advance!

Tiffy

---

### Post by arrancaru on 2008-12-05
It's called Network Manager, you can look for it in synaptic package manager or Add/Remove Programs from menu if it's not installed.

---

### Post by lswb on 2008-12-06
For the icon to be visible you must have a notification area on your panel. You can restore the top panel or just add a notification to your remaining panel. (right-click on panel, select "Add to Panel", then select Notification Area from list)

After you have the notification area installed (without any icons to populate it, it is a barely visible double vertical row of dots) go to 
Main Menu/System/Preferences/Sessions/Startup Programs and make sure "Network Manager" is checked. If you don't see it in the list, click on add and enter "Network Manager" for the name, "nm-applet --sm-disable" as the command, and whatever you like for the comment; only the command field is important. 

Close the sessions dialog and if the icon doesn't show up within a few seconds log out of gnome and back in (or reboot)

---

### Post by inirini on 2008-12-06
"Network Manager" is already installed (checked the add/remove to make sure), but I do not know where it is located. That's what I meant about locating the program. Sorry if that sounded vague earlier. I know it is in the application>internet, but it is not visible in the menu.

Edit: Should have refreshed, but lemme try the notification area.

Edit^2: It's back up, thanks a lot, lswb!

---

### Post by Shoadow56 on 2008-12-08
Thank you for that lswb. I also deleted my wireless icon by accident and restored it by putting the "Notification Manager back onto my top bar. Thanks!

---


---
title: "[SOLVED] k menu button disappeared"
date: 2008-11-13
forum: Desktop Environments
---

### Post by johnnyhop on 2008-11-13
kde 4.1 menu button mysteriously appeared on the right side of panel.  When attempting to move to original position on left side the button disappeared. How is this restored?

---

### Post by aged hippy on 2008-11-13
A Right-click on the Desktop *->Unlock Widgets* then right-click on the Panel *->Add Widgets ->Application Launcher* should do it. :)

If you want to alter its position, you can drag it about when the widgets are unlocked.

---

### Post by johnnyhop on 2008-11-14
Thank you, OK it's back, but on the desktop, not the panel.  When adding to the panel it appeared on the right side and wouldn't drag.  Now in deep doo doo, removed the panel with the intention of creating a new panel but that's not working out well.  The application launcher icon is barely visible, the trash can doesn't fit and nothing will drag at all and widgets are unlocked.  I'm considering a clean install, wadda ya think? I'm an old hippie too.

---

### Post by SuperSonic4 on 2008-11-14
You have to use the add widget on the panel to get them on the panel. Right click on the desktop and try add panel

---

### Post by SuperSonic4 on 2008-11-14
You have to use the add widget on the panel to get them on the panel. Right click on the desktop and try add panel

---

### Post by aged hippy on 2008-11-14
> 
I'm considering a clean install, wadda ya think?


That's one way to do it. :D

Another is to stuff the live CD in the drive and boot it, and - with root privileges (_i think_) - find the **.kde** directory and either re-name or delete it.

A new one will be generated with default settings when you next boot.

There's probably a Command Line way to do it, but i pass on that one. :D

---

### Post by johnnyhop on 2008-11-14
Thanks again...Much easier this way.  I opted for the rm command

---

### Post by rocketero on 2009-01-25
I have the same issue. somehow I lost the K icon on kde 4.1.3

I have done all whay has been recommended here and NOTHING works. and Sonic4, you are totally wrong on your suggestion.

I have deleted infinite times the .kde folder in my user folder, and after rebooting the same thing shows, in other words, not K button.

I finally out of desperation desperation clicked on "REMOVE THIS PANEL" and now I dont have anything at  the bottom of the screen.

what a bummer.

any suggestion on how to get the complete K button and the taskbar ??

---

### Post by UbuntuniX on 2009-01-25
I also had the KDE menu button mysteriously disappear soon after updating to Intrepid, though I was able to recreate the button.

---

### Post by markofealing on 2009-02-19
This problem appears to be a bug in KDE4, it has also happened to me in Mandriva 2009! It's stupid bugs like this which put people off Linux!

Let's hope KDE 4.2 is better than 4.1.

I've resolved this issue as follows:

[LIST=1]
[*]Right click on the desktop and select run. 
[*]type dolphin and select the icon for dolphin to run it.
[*]From the menu bar, click View and Show Hidden Folders.
[*]Move, rename or delete the .kde folder. As previously posted a new one will be created.
[*]Close Dolphin, right click on desktop and select Leave. Restart Kubuntu.
[*] Once you log in the K menu should now be restored on the left hand side of the screen. You will then have to put up with another bug and deal with the "Incomplete Language Support" software update. I normally cancel this as English is already installed.
[*] Now lock your widgets by pressing CTRL+L, hopefully this will prevent them being deleted!
[/LIST]

Enjoy!

---

### Post by Smouch on 2009-03-07
I was having the same issue, got frustrated and deleted the bottom panel. deleting the .kde folder worked like a charm. All original icons and widgets back. thanks a bunch

---


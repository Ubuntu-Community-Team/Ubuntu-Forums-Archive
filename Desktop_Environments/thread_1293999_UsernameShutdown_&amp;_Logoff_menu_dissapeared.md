---
title: "Username/Shutdown &amp; Logoff menu dissapeared"
date: 2009-10-17
forum: Desktop Environments
---

### Post by Lewis Smith on 2009-10-17
Hi,

My menu thing on the right, with my username, and all the shutdown options etc. has dissapeared. I am using Karmic beta, and I installed the Educational desktop thing, which changed the boot screen and cursors and stuff. I then removed it and all it's applications, and searched in vain for a way to restore the human cursors. I got StartUp-Manager, and changed the splash screen from kubuntu to ubuntu, then I changed the GRUB resolution to 1O24x768, and rebooted the PC.
When I logged on, I got three messages saying that some applet wasn't working, and asking to delete it or not. As the CPU performance applet wasn't there, I assumed that's what they were, and deleted them, as I didn't know what the names meant, and I didn't need the CPU applet anyway. I then discovered that the menu on the right was no longer there:confused:, and the computer janitor would not get it back, and I couldn't find it anywhere in the add to panel thing, and it's not in the Ubuntu Software Center or administration/preferences menus. I assume that it will be fixed when I upgrade to the stable version of Karmic, and I can still switch user/log off/suspend/shutdown/lock screen/etc. in the system menu, although it would be nice if someone told me how to get the menu back, or failing that, at least its proper name.

Any help would be ENORMOUSLY appreciated!!
Thanks a million to anyone who helps get the menu back!

---

### Post by Lewis Smith on 2009-10-17
Hi, me again,

I got back the log off menu, but it's in the wrong place.
And there's more.
The Applications Menu won't open, and the Preferences and Administration Menus don't show up in the System Menu.
Can anyone please tell me how to reset the panel to the default configuration!?
Even though I'm not that good at it, I don't mind if it's a thing you type into the Terminal, that may even be better, as I think I can manage that without the menus.

Any help would be appreciated even more than for the previous bug!!!

---

### Post by Lewis Smith on 2009-10-17
Hi, me again, . . . again,

If anyone has already spent a while finding a solution, then sorry, but there's no need any more.

I started to file a bug report when I tried to open the Applications menu, and one of the possible duplicate bugs (from 7.04) had a comment saying to empty "~/.config/menus/", so I made my way there, and pressed "Ctrl+A", then "Del" (Control A then Delete), and voilà (I have a French keyboard, I didn't hunt in the character map for à), anyway, and voilà, all my menus work.

Just two snags:
1) All programs in Wine were deleted from the menu, although this could probably have been avoided by not deleting the Wine folder in the menus folder. (Don't care about this, I never use Wine.)
2) My Panel is missing the Battery charge thingy. (Important)

If anyone knows how to fix this, then you know the drill.

On a lighter note, the menu thingy that caused all the crazy BS is called the "Indicator Applet Session".

---

### Post by wojox on 2009-10-17
If it doesn't show up when you right click the panel +Add to Panel
Search with the add to panel box for battery.
If it still isn't there open synaptic and search battery-stats

---


---
title: "Ubuntu-MATE Application Menus"
date: 2015-10-08
forum: Desktop Environments
---

### Post by wagb278 on 2015-10-08
Installed Ubuntu-MATE 15.04 and I like it, back to what Ubuntu used to be.  But I have one thing that bugs me that I would like to change, but don't know how.  In applications, principally LibreOffice when a menu is open the menu is presented with a white background which is the same as the document background.  Linux Mint (17) does not have this presentation issue.  I checked LM-17 and LibreOffice shows menus with a border and very light gray (off-white) background for the menu which defines the menu content better to my liking. How can I tell Ubuntu-MATE to alter the menu presentation?  

I looked at the Appearance > Theme, but there is no customization for how menus are presented.  LM-17 uses a Theme named Mint-X, if that makes a difference.  The customizations in the available Themes do not include settings (Tabs) for Menu, only Controls, Colors, Window Border, Icons, and Pointer.  **So, where is the presentation of application menus configured?** 

Unrelated question, just curious - Ubuntu comes with different Desktop Environments, why is the distribution named Ubuntu not named Ubuntu-Unity?  I gave Unity an honest try for three months and just didn't like it which forced me to switch to Linux Mint; but Ubuntu-MATE gives me hope.

Thanks, hopefully someone knows how to change the presentation of application menus.

---

### Post by tgalati4 on 2015-10-08
Run *mozo* to edit the MATE menu.  Mate-menu-editor would be too obvious.  [http://stackoverflow.com/questions/19474421/mate-menu-is-not-configurable](http://stackoverflow.com/questions/19474421/mate-menu-is-not-configurable)

Some other not-so-obvious MATE tweaks:  [http://community.linuxmint.com/tutorial/view/1395](http://community.linuxmint.com/tutorial/view/1395)

---

### Post by wagb278 on 2015-10-08
Thanks tgalati4, but my issue is not with the Linux Mint Menu.  My issue is with the Ubuntu-MATE distribution and not knowing how to change how the menus in applications (such as LibreOffice). Maybe I wasn't clear in my description of what I want to change. 

I did discover a solution to my problem.  In the Themes (Appearance > Theme Tab) customizing the Controls to select a different setting (I selected "Industrial") gives me more readable menus in applications.  I would prefer to have a more control over these settings for Themes.  Maybe that is possible somewhere; but at least I now know the Themes control this stuff.  I will have to study up on Themes.

---

### Post by tgalati4 on 2015-10-08
I misread your post completely.  So much for speed reading.   Ignore everything I said.  Sorry.  In fact I opened LibreOffice and couldn't see the problem, and I'm running Linux Mint MATE, but then you mentioned that the problem didn't happen on Mint MATE 17.  I missed two chances to understand what the problem was.

I interpreted the layout of application menus to mean the layout of mint-menu ("The Start Button").  Again, apologies.

I suppose you can install the Mint-X theme onto Ubuntu MATE to give a better application menu appearance.

---

### Post by Dennis N on 2015-10-08
Menu background is determined by the GTK theme used (found under controls).

I use the Greybird theme. Sounds much like what you describe. Screenshot attached shows LibreOffice 5 menu color with Greybird in Ubuntu MATE 14.04. 
Install **shimmer-themes** package from the Ubuntu repository to get Greybird. 
Note: My Greybird has its selected background color changed. The default is bluer.

---


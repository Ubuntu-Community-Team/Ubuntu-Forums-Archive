---
title: "lost window decoration and other settings"
date: 2011-08-23
forum: Desktop Environments
---

### Post by utubun on 2011-08-23
I think I have done something foolish.

I'm using ubuntu classic on 11.04 (that's not the foolish part). I was tidying up my main menu with the Edit Menu application, and deleted all of the hidden items in the Applications submenu 'Other', including things like Compiz, Metacity, Open Folder, Window Manager.

I had believed that this would have no effect on the operation of anything; only upon what was listed in the menu, but the effects seem to have been quite severe and wide-ranging.

Now, at reboot, there is no background image, cursor, or windows decorator (I have to get a terminal window open and run compiz --replace), and I cannot open locations from the places Menu (I get an error telling me that no application is registered as handling this file). There are probably other consequences I have yet to discover.

The desktop.configuration files for the 'Other' menu items are still present in Usr/Share/Applications directory.

Is there a way that I can restore things to the way they worked before I deleted these Menu items? It would be an enormous help in my predicament.

---

### Post by jerrrys on 2011-08-25
like yourself; i don't see the connection with your problem and editing the main menu.

but to answer your question, go to your home folder and navigate to /.config/menu

this folder contains your custom menu settings.  rename it to whatever, so if you need to, you can restore it.  after you rename it you will end up with a mostly default main menu.  and if this does not help, your can restore it.

---

### Post by utubun on 2011-08-25
Thank you - this indeed works to restore the menu items to defaults.

My bigger issue was getting the desktop background, and window decorations back. I managed to do this, by adding compiz to the startup applications.

It still totally baffles me why editing menu items should have had this drastic effect, but it definitely did! If anyone has any insights into why, it would be interesting.

---


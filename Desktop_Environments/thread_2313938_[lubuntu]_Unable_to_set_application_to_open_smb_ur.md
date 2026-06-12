---
title: "[lubuntu] Unable to set application to open smb:// url"
date: 2016-02-17
forum: Desktop Environments
---

### Post by daniele-nosella on 2016-02-17
Hello there,
I'm a computer support guy, and I'm installing Lubuntu in many companies to re-use old PC that are too slow to support Microsoft O.S..

With a little effort, I configured the aspect and behaviour of the LXDE GUI to be usable by people who grew with Microsoft OSes.

-I created some launcher on the desktop to represent Computer resources, Network resources, etc..
-I activated the option to show "Trash" Icon (and I'm a little disappointed there is no option to empty trash)
-I chosen humanity icon style, which is very similar to what the user expect to see.

I have to say that the system is very responsive, usable, and good looking.

What I'm not able to do is how to allow the user to create Shortcuts to Network Shares (SMB) on the desktop.

I'm able to create it as bookmark in the pcmanfm filemanager, and it's a very user-friendly operation
I'm able to create it on the desktop creating a launcher (with lxshortcut -o command) and then calling pcmanfm with the url as paramater. It works great, but I can't ask to a standard user to do that kind of stuff to create a simple desktop shortcut.

I tried to go on the network position with pcmanfm, then select the folder, then click on the edit menu and select create link, then create the link on the desktop, which works great, but the when I try to open the created link the system tells me that there isn't any application set to open url smb://.

So I tried to right-click on the shortcut icon and set pcmanfm as default application to open that kind of link, but it seems the system doesn't remember the setting. (and yes, I have flagged the set application as default application to open this kind...)

If I right click on the icon and then select pcmanfm to open the link, it works, but if I double click on the icon, the system tells me that there isn't any application set to open url smb://.

For a technician like me it's perfectly acceptable to create a launcher, but from the user perspective it's not acceptable.

Can somebody help me?

Thank you

---

### Post by daniele-nosella on 2016-02-17
Solved!!!

You have to add this line: x-scheme-handler/smb=pcmanfm.desktop

In the file: /usr/share/applications/default.list


It seems the "set application as default" in the panel "Open with" should do that, but it doesn't work form the GUI.

---


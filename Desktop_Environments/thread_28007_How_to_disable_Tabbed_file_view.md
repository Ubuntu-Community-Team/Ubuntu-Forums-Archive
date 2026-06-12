---
title: "How to disable Tabbed file view?"
date: 2005-04-18
forum: Desktop Environments
---

### Post by raid517 on 2005-04-18
Hi, for some reason in KDE Konqueror has switched over to almost excusively using a tabbed file view when I am using it as a file manager and I cannot disable this feature. Tabs are occasionally useful for web browsing, but I find them much less useful for file mamagement. Essentially what seems to be happening is that the 'web behaviour'module options in KDE control are being applied to the file mamagement view too. Except that is  that in the web behaviour options module I have selected to explicitly disable tabbed web browsing. (I did so in an unsuccessful attempt to disable this behaviour).

Also I have just discovered that now when I attempt to open a web link, or click on any links at all, Konqueror will refuse to open them  and instead open a new window for every link I click. I am aware there is a dialog that asks if I want to open links in a new tab instead of a new window, but I don't really want either of these. All I want is a classic Internet explorer type behaviour, where if I click on a link the browser will just 'go there', without opening a new tab and without opening a new window. (I would like this to be true for both the file management view and the web browsing view). Of course there is the advantage that if I wanted to open a link in a new tab or in a new window I should be able to right click on the link or folder and select 'open in a new window'. But I do not want either of these to be the default behaviour.

Please advise.

GJ

---

### Post by Frustration on 2005-04-18
Me too :|

Opening Konqueror from the *System Menu - Home Folder* seems to open Konqueror in Web mode rather than file browsing mode, hence these issues..

---

### Post by robert114 on 2005-05-16
The solution is proberbly not disabling the function tabbed view. But I changed the command for opening directories in the KDE control center to -> kfmclient openProfile filemanagement
Now when i open a shortcut on my desktop and it opens a new window. (i think thats what you want too).

Here is what i've exactly done:
1. Open the KDE Control Center
2. Open in the Control Center KDE components
3. Click on File Associations.
4. In the right screen go to inode and click on directory.
5. Choose in the most right screen under Application Preference Order Konquror and click on the button Edit.
6. Now a new screen appears and go to the last tab (Application)
7. Change the command from kfmclient openURL %u inode/directory to kfmclient openProfile filemanagement
8. Click OK and close the Control Center with applying the changes.

Now my links (shortcuts) are opened in a new window.
To make sure you open the Konqueror in the file manager mode from the start menu do the following (create a link with the kfmclient openProfile filemanagement command in the KDE start menu)

1. Right click on the start/menu button and choose Menu Editor
2. In the Menu Editor choose where you want to put you're link and click on it. I choose Utilities.
3. Click in the menubar on file and choose New Item
4. Type a name for your browser. I simply choose Konqueror file browser
5. On the right type by command kfmclient openProfile filemanagement.
6. You can choose an other Icon by clicking on the dull Icon on the right near Name and choose an other one. 
7. Now close and save.

I hope this is a good solution for your problem.

---

### Post by robert114 on 2005-09-07
well, I've found a better solution ,
just go to the configure konqueror screen (Settings - Configure Konqueror in the menu)
go to web behavior and click on the button by "advanced options" by tabbed browsing,
disable the last option "open as tab in excisting Konqueror...." that should do it!

---


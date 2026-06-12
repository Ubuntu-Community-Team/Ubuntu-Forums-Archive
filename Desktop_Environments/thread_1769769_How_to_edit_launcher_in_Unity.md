---
title: "How to edit launcher in Unity?"
date: 2011-05-28
forum: Desktop Environments
---

### Post by dankegel on 2011-05-28
I upgraded to 11.04.  A launcher I had created before the
upgrade shows up in the dock and works nicely... but I want
to change what it does.

[http://askubuntu.com/questions/39205/how-do-i-change-the-command-that-a-launcher-item-launches](http://askubuntu.com/questions/39205/how-do-i-change-the-command-that-a-launcher-item-launches)

says to edit the .desktop file.  Fine, but there ought to be a
way to do it with the gui, shouldn't there?

[http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand](http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand)

suggests, after reading between the lines, that you can only
edit launchers in the gui when they're not in the dock;
the dock is only for pinning launchers that exist elsewhere.

But I don't know where my launcher file is, it's certainly not
on the desktop, since I removed it from there before upgrading.

I see that in the new world, deleting a launcher from the desktop
removes it from the dock, too.

I am very sad that I can't have launchers on the dock without
having them on the desktop, and that there's no way to edit
launchers from the dock.

I am aware of the "switch back to classic and stop using unity"
workaround.

---

### Post by mc4man on 2011-05-28
> Fine, but there ought to be a
way to do it with the gui, shouldn't there?
There is an editor/creator in development, is currently only available like shown here
[http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html](http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html)

It does a pretty good job, currently lacks a few things that can be done easier and better by 'hand'

For newly created icon/quicklists the .desktop can be anywhere, just don't add to launcher until it's where you wish to store
(I use ~/.local/share/applications to store or create new launchers ect.

For 1 app only quicklist mods ~/.local/share/applications is better than editing the app's .desktop in /usr/share/applications - it's protected from an app update
(if I had multiple users and wanted modded/created .desktops available to all then I'd put or copy them to /usr/local/shared/applications 

Myself make great use of 'icon menus' where the icon is a category and the quicklist entries are the menu - here's an example of a utilities icon, has since grown to 12 entries which probably about where I'd limit though there is no limit except what is practicable to use
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

---

### Post by Larkspur on 2011-05-28
You can edit launchers through a GUI (Main Menu) but you have to take them off the launcher bar temporarily: Unpin the launcher, open Main Menu, find the launcher you want to edit, click properties, change what you want, close the properties dialogue, launch the  program, pin to launcher.

It sounds a bit of a long-winded process, I know.

---

